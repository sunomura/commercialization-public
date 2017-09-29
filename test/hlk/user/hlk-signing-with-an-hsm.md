---
title: HLK Signing with an HSM
description: HLK Signing with an HSM
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 85CEB88F-66F5-45FF-8E87-04229A180752
---

# HLK Signing with an HSM


## <span id="Introduction"></span><span id="introduction"></span><span id="INTRODUCTION"></span>Introduction


This topic describes some of the setup and configuration issues that can occur when using a third party network-based Hardware Security Module (HSM) to store Extended Validation (EV) Certificates.

## <span id="Background"></span><span id="background"></span><span id="BACKGROUND"></span>Background


### <span id="HLK_Packaging"></span><span id="hlk_packaging"></span><span id="HLK_PACKAGING"></span>HLK Packaging

HLKX package files use the [Open Packaging Conventions](https://en.wikipedia.org/wiki/Open_Packaging_Conventions). The specification is part of a ISO working group, implying that HLKX files are not compatible with Signtool.

### <span id="HLK_Package_Signing"></span><span id="hlk_package_signing"></span><span id="HLK_PACKAGE_SIGNING"></span>HLK Package Signing

When the HLK signs a package, the signature and relationships are placed in the package alongside the HLK data. This is the data that `System.IO.Packaging.PackageDigitalSignature` uses to validate the signature on the data in the package.

### <span id="Cryptographic_Service_Providers"></span><span id="cryptographic_service_providers"></span><span id="CRYPTOGRAPHIC_SERVICE_PROVIDERS"></span>Cryptographic Service Providers

A [cryptographic service provider](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721572.aspx#-security-cryptographic-service-provider-gly) (CSP) contains implementations of cryptographic standards and algorithms. At a minimum, a CSP consists of a [dynamic-link library](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721573.aspx#-security-dynamic-link-library-gly) (DLL) that implements the functions in [CryptoSPI](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721572.aspx#-security-cryptospi-gly) (a [system program interface](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721625.aspx#-security-system-program-interface-gly)). Most CSPs contain the implementation of all of their own functions. Some CSPs, however, implement their functions mainly in a Windows-based service program managed by the Windows service control manager. Others implement functions in hardware, such as a [smart card](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721625.aspx#-security-smart-card-gly) or secure coprocessor. If a CSP does not implement its own functions, the DLL acts as a pass-through layer, facilitating the communication between the operating system and the actual CSP implementation.

### <span id="Certificate_Store_and_Registry"></span><span id="certificate_store_and_registry"></span><span id="CERTIFICATE_STORE_AND_REGISTRY"></span>Certificate Store and Registry

Certificates in the Certificate Store all map to a CSP DLL that will do the final signing. This can be seen in the registry entry below.

``` syntax
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\Defaults\Provider\Microsoft Enhanced DSS and Diffie-Hellman Cryptographic Provider]
"Image Path"="%SystemRoot%\\system32\\dssenh.dll"
"SigInFile"=dword:00000000
"Type"=dword:0000000d
```

## <span id="HLKX_Package_Signing_with_a_Certificate_hosted_by_a_Network-Based_HSM"></span><span id="hlkx_package_signing_with_a_certificate_hosted_by_a_network-based_hsm"></span><span id="HLKX_PACKAGE_SIGNING_WITH_A_CERTIFICATE_HOSTED_BY_A_NETWORK-BASED_HSM"></span>HLKX Package Signing with a Certificate hosted by a Network-Based HSM


### <span id="Controller_Configuration"></span><span id="controller_configuration"></span><span id="CONTROLLER_CONFIGURATION"></span>Controller Configuration

To set up an HLK controller to sign with an HSM certificate, the following must be present on the system:

-   A Certificate Authority (CA) from the HSM
-   A CSP file from the HSM

Instructions on how to configure an HSM client with these components should be documented by your HSM provider.

### <span id="Signing_with_the_HLK"></span><span id="signing_with_the_hlk"></span><span id="SIGNING_WITH_THE_HLK"></span>Signing with the HLK

If the controller is configured correctly, you should be able to point to the certificate from the HSM as you would a locally installed certificate from the HLK and sign the package.

## <span id="Testing_the_HSM_Configuration"></span><span id="testing_the_hsm_configuration"></span><span id="TESTING_THE_HSM_CONFIGURATION"></span>Testing the HSM Configuration


### <span id="Using_Signtool"></span><span id="using_signtool"></span><span id="USING_SIGNTOOL"></span>Using Signtool

The first step to understand if we can sign is by trying to sign a file using signtool. This will allow us to verify that the signing workflow is functioning correctly. First we will sign a PE file (exe or dll). For example, signing using a name:

``` syntax
signtool sign /f HighValue.cer /csp "Hardware Cryptography Module" /kHighValueContainerMyControl.exe
signtool sign /n "My Company Certificate" MyFile.exe
```

or to sign using the SHA1 hash of the installed certificate:

``` syntax
signtool sign /sha1 0cf1d2f7befc7d143678f86963aef5572b710cf2 MyFile.exe
```

The certificate name is found in the Subject Information and the SHA1 hash is found in the Thumbprint. When using the hash remove all of the spaces and special characters that are in the hash so the format looks like the example above. You can also sign using a [Personal Information Exchange](https://msdn.microsoft.com/en-us/library/windows/hardware/ff549703.aspx) (PFX) file. This is most likely not what you want to do, since a PFX file can contain the private key, where a certificate contains only the public key.

``` syntax
signtool sign /f certdata.pfx MyFile.exe
```

You can verify the signature using signtool

``` syntax
signtool verify /v /pa MyFile.exe
```

If you were able to sign and verify a file using anything except a PFX file, you can try to sign an HLK package. If you were unable to sign please look at the Troubleshooting section.

### <span id="Using_PackageDigitalSignature"></span><span id="using_packagedigitalsignature"></span><span id="USING_PACKAGEDIGITALSIGNATURE"></span>Using PackageDigitalSignature

There is a code example of signing using `PackageDigitalSignature` at the end of this document in the Code Samples section. You should have also gotten the complete C# file when you received this document. To use this example, you will need to provide a full path to your unsigned package and the thumbprint of the certificate you going to use for signing. If you were unable to sign please look at the Troubleshooting section.

## <span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Troubleshooting


The most likely cause is that there is not a certificate and associated CSP installed on your system from your HSM. Some of the things you could try are the following:

-   Can you sign on this system using just the tools supported by your HSM vendor?
-   Does your HSM vendor install a certificate and CSP on this system?
    -   What are the certificate properties?
-   Does your HSM vendor support and document using signtool? If a file can be signed using Signtool with an HSM, this is an indicator that the system has been configured correctly and implies that the HLK can also sign HLKX packages.
-   When running the example code (HSM\_example.cs) what is printed for the CspKeyContainerInfo.ProviderName
    -   Does that provider name map to the correct vender supplied CSP DLL. That information can be found in the registry as shown above.

## <span id="Code_Samples"></span><span id="code_samples"></span><span id="CODE_SAMPLES"></span>Code Samples


### <span id="PackageDigitalSignatureManager"></span><span id="packagedigitalsignaturemanager"></span><span id="PACKAGEDIGITALSIGNATUREMANAGER"></span>PackageDigitalSignatureManager

```CSharp
public static void Sign(string package, X509Certificate2 certificate)
{
  // Open the package to sign it
  Package packageToSign = Package.Open(package);

  // Specify that the digital signature should exist 
  // embedded in the signature part
  PackageDigitalSignatureManager signatureManager = new PackageDigitalSignatureManager(packageToSign);

  signatureManager.CertificateOption = CertificateEmbeddingOption.InCertificatePart;

  // We want to sign every part in the package
  List<Uri> partsToSign = new List<Uri>();
  foreach (PackagePart part in packageToSign.GetParts())
  {
    partsToSign.Add(part.Uri);
  }

  // We will sign every relationship by type
  // This will mean the signature is invalidated if *anything* is modified in                           //the package post-signing
  List<PackageRelationshipSelector> relationshipSelectors = new List<PackageRelationshipSelector>();

  foreach (PackageRelationship relationship in packageToSign.GetRelationships())
  {
    relationshipSelectors.Add(new PackageRelationshipSelector(relationship.SourceUri, PackageRelationshipSelectorType.Type, relationship.RelationshipType));
  }

  try
  {
    signatureManager.Sign(partsToSign, certificate, relationshipSelectors);
  }
  finally
  {
    packageToSign.Close();
  }
}
                
```

 

 






