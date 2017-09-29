---
title: Machine Sets
description: Machine Sets
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: a25c9f64-4340-4bd7-931d-7326dc927e75
---

# Machine Sets


A **MachineSet** object is a collection of machine roles, and a machine role is a collection of computers that run the same test binaries. You must create a valid **MachineSet** to allocate and assign computers for any test that requires multiple computers.

Although most tests in the Windows Hardware Lab Kit (Windows HLK) run on a single computer, some tests require multiple computers. For example, a network test might target a network adapter on one computer, and a second computer might act as a network message receiver. In this example scenario, each computer runs different (but coordinated) binaries for one test.

For the preceding scenario, the machine set has two roles, and each role has one computer.

In a more complex scenario (for example, testing server load stress), you might have one target computer, 10 client computers that make simultaneous requests on the target computer, and one test coordinator computer to synchronize clients and record results.

## <span id="MachineRole"></span><span id="machinerole"></span><span id="MACHINEROLE"></span>MachineRole


A **MachineRole** object is a list of computers that perform a specific test role. Use the **AddMachine()** method to add a computer to a role. **AddMachine()** returns an error if you add a computer that isn't in the correct machine pool or if the maximum number of computers is exceeded.

This example shows how to display the role for each computer in a **MachineSet** object:

``` syntax
Machine secondaryMachine = GetSecondaryMachine();
Test test = GetTest();
 
MachineSet machineSet = test.GetMachineRole();
 
foreach (MachineRole role in machineSet.Roles)
{
    Console.WriteLine("Role : " + role.Name);
    Console.WriteLine("Min : {0} Max : {1}" + role.Minimum, role.Maximum);
    Console.WriteLine("isPrimary {0}", role.Primary);
 
    Console.WriteLine("Allocated machines: ");
    foreach (Machine machine in role.GetMachines())
    {
        Console.WriteLine("\t" + machine.Name);
    }
}
```

If you want to add a secondary machine to Roles\[1\], you can use this:

``` syntax
machineSet.Roles[1].AddMachine(secondaryMachine);
if (machineSet.Validate())
{
Test.QueueTest(machineSet);
}
```

 

 






