---
title: QosRemoteSettings
description: Provides troubleshooting guidelines for the QosRemoteSettings HLK test.
ms.author: sapaetsc
ms.date: 07/17/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-oem
---

# QosRemoteSettings Troubleshooting

#### Test Summary
This test verifies that the DUT correctly accepts, and resolves remote QoS settings via DCBX.

This test requires two machines, with the "Support Device" on the Server machine (PEER) **connected directly** to the "Test Device" (DUT) on the Client machine.


#### Traces and Packet Capture
The following traces can be enabled before starting the test, if you would like to get more information: 
- NDIS traces to enable on the DUT machine if you want to see how the OS handles DCB & DCBX status indication, and QoS capabilities advertisements from the DUT.
    - 0x800000 is for QoS status indication traces
      0x001000 is for QoS capability advertisement traces 
      0x000400 is for QoS OID request from the OS traces
    
```
netsh trace start provider={dd7a21e6-a651-46d4-b7c2-66543067b869} keywords=0x00801400 level=5 tracefile=ndis.etl 
<start the NDIS test>
netsh trace stop
```

- Run packet capture on the "Support Device" on PEER machine capture the LLDP DCBX packet sent out of the "Support Device".
    - Note that the test might reset the Support Device. Therefore, you might need to start/restart packet capture after the test has started.

#### Test Details
Each of the sub-tests does the following:
##### Configure local DCB on the DUT, including enable DCBX Willing on the DUT (NDIS\_QOS\_PARAMETERS\_WILLING) 
- _Expectation_: 
    - The DUT accepts the local DCB setting 
    - The DUT generates an NDIS\_STATUS\_QOS\_OPERATIONAL\_PARAMETERS\_CHANGE status indication if the local setting is different from its current local settings. 
- _Trace info (if enabled as shown above)_
    - Device QoS capability advertisements (to see this information, you'd need to restart the adapter prior to running the test, in order for the miniport to re-register QoS capabilities to the OS.)
        - ==&gt;ndisMSetQosAttributes: …
        - &lt;==ndisMSetQosAttributes: …, Status 0x0 
    - On OID request to miniport
        - ==&gt;ndisOidPreQosSetParameters: …
        - ==&gt;ndisValidateQosParameters: …
        - &lt;==ndisValidateQosParameters: … 
        - &lt;==ndisOidPreQosSetParameters: … Status 0 (Or some error traces in failure case)
    - On OS receiving NDIS\_STATUS\_QOS\_OPERATIONAL\_PARAMETERS\_CHANGE
        - ==&gt;ndisMIndicateQosParametersChange: … StatusCode: 400200a0
        - ==&gt;ndisValidateQosParameters 
        - &lt;==ndisValidateQosParameters succeeded 
        - &lt;==ndisMIndicateQosParametersChange: … StatusCode: 400200a0

##### Craft an LLDP DCBX packet on the server machine, and send the packet out of the "Support Device" on the server machine.  
- _Expectation_: 
    - The DUT receives the packet, since the "Support Device" is connected directly to the DUT.
    - The DUT resolves its local DCB settings with settings specified in the DCBX packet.
    - The DUT issues an NDIS_STATUS_QOS_REMOTE_PARAMETERS_CHANGE status indication with the resolved remote settings.
    - The OS subsequently issues an OID_QOS_PARAMETERS to the DUT to configure local DCB settings, based on the remote settings above.
    - The DUT accepts the local DCB setting.
    - The DUT generates an NDIS_STATUS_QOS_OPERATIONAL_PARAMETER_CHANGE status indication if the local setting is different from its current local settings.
- _Trace info (if enabled as shown above)_:
    - On sending DCBX message from PEER machine
        - Packet capture should show DCBX LLDP packets sent out of the Support Device
    - On OS receiving NDIS_STATUS_QOS_REMOTE_PARAMETERS_CHANGE
        - ==>ndisMIndicateQosParametersChange: … StatusCode: 400200a1
        - ==>ndisValidateQosParameters: …
        - <==ndisValidateQosParameters: …
        - <==ndisMIndicateQosParametersChange: … StatusCode: 400200a1
    - On OS issuing OID_QOS_PARAMETERS to the miniport for setting local DCB
        - Similar traces as above.
            
##### Query OID_QOS_REMOTE_PARAMETERS on the DUT to verify that the DUT has received the LLDP packet, and resolved the remote settings as expected.
- _Expectation_:
    - The query returns the DCB settings specified in the LLDP DCBX packet that was sent by the "Support Device" to the DUT.
    - Note that the query will not reach the miniport. Instead, NDIS intercepts the query OID, and responds with the settings of the last NDIS\_STATUS\_QOS\_REMOTE\_PARAMETERS\_CHANGE that it received from the DUT. Therefore, the DUT must have already generated a NDIS\_STATUS\_QOS\_REMOTE\_PARAMETERS\_CHANGE when it received the LLDP
DCBX packet.
