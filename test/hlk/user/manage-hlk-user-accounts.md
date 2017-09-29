---
title: Manage HLK User Accounts
description: Manage HLK User Accounts
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 3b642ee4-e66a-4625-814c-571a1babfc01
---

# Manage HLK User Accounts


An HLK user account is automatically created for the person who installed the HLK Controller, and that account is granted administrator privileges within HLK. A person who has a HLK user account with administrator privileges is called a HLK administrator.

HLK administrators can create new HLK user accounts or modify the permissions of existing HLK user accounts.

>[!IMPORTANT]
>  
To create an HLK user account for a domain user, as opposed to a user account for a local user, you must be logged on to the HLK Studio computer as a domain user with administrator rights on the local machine.

 

If you try to create an HLK user account for a domain user while you are logged on as a local user with administrator rights, an error message will appear informing you that the user for whom you are trying to set up permissions does not exist in the domain. The domain referred to in the error message is the local machine and not the domain to which it is connected.

## <span id="Assigning_Roles"></span><span id="assigning_roles"></span><span id="ASSIGNING_ROLES"></span>Assigning Roles


When you create a new user account for an HLK user, you must also assign a datastore role for the user.

The following is a list of the HLK datastore roles that you can assign a user when you create the new user account.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>hlk_DSGuests</p></td>
<td><p>With a guest user account, you can log in without having a user account to access the HLK datastore. This level of access is very restricted and only allows the user to view the results of a job.</p></td>
</tr>
<tr class="even">
<td><p>hlk_DSUsers</p></td>
<td><p>To obtain access to a Microsoft SQL Server database, you must have a corresponding user account for that database.</p>
<p>This user account allows the HLK user to perform several of the basic tasks associated with logo testing. See the permissions table that follows for more details</p></td>
</tr>
<tr class="odd">
<td><p>hlk_DSAdministrators</p></td>
<td><p>If a user is assigned this role, that user has administrator privileges on the local system and is able to install a system. Additionally, if the host computer is part of a Windows domain, the Administrator account usually has domain-wide privileges as well.</p></td>
</tr>
<tr class="even">
<td><p>hlk_DSOwners</p></td>
<td><p>The datastore owner is a user that has permission to perform all activities in the database. See the permissions table that follows for more details.</p>
<p>To the HLK Studio user interface, the HLK_DSOwners and the HLK_DSAdministrators roles are the same. However, the level of access a user has to the HLK datastore itself when he or she is assigned the HLK_DSOwners role far surpasses the level of access a HLK_DSAdministrators user has. As such, you must only assign the HLK_DSOwners role to users who are very knowledgeable about Microsoft SQL Server.</p></td>
</tr>
</tbody>
</table>

 

**Permissions Table**

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>hlk_DSGuests</th>
<th>hlk_DSUsers</th>
<th>hlk_DSAdministrators</th>
<th>hlk_DSOwners</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Schedule/Run jobs</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Create Jobs</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Edit Jobs</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>View Results</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Delete Jobs</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Cancel Jobs</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Add Users</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Remove Users</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>

 

## <span id="Creating_a_HLK_User_Account"></span><span id="creating_a_hlk_user_account"></span><span id="CREATING_A_HLK_USER_ACCOUNT"></span>Creating a HLK User Account


1.  From your controller, select **Start&gt;All Programs&gt; Windows Kits&gt;Hardware Certification Kit&gt;HLK Manager**.

2.  Select **Tool&gt;Management Console**.

3.  In the left pane, expand **Console Root**.

4.  For each of the listed datastores (WTTIdentity and HLKJobs), do the following:

    1.  Expand the datastore, right-click **Users**, and then click **New User**.

    2.  In the **Datastore User Properties - New User** dialog box, in the top pane, type the user name of the person you are creating a HLK user account for using the format domain\\username, where domain is the user's domain or workgroup name, and username is the user's user name.

        >[!NOTE]
        >  
        If you are creating multiple user accounts, separate each user with a semicolon.

         

    3.  In the **Datastore Role** pane, select the **HLK\_DSOwners** check box.

        >[!WARNING]
        >  
        You can assign multiple roles to a new user at the same time. To grant this user administrator privileges, select the **hlk\_DSAdmins** check box also.

         

    4.  Click **OK**.

## <span id="Granting_Permissions"></span><span id="granting_permissions"></span><span id="GRANTING_PERMISSIONS"></span>Granting Permissions


Complete the following procedure to grant a HLK user permission to run jobs on a machine pool.

1.  From your controller, select **Start&gt;All Programs&gt; Windows Kits&gt;Hardware Certification Kit&gt;HLK Manager**.

2.  Select **Explorers&gt;Job Monitor**.

3.  Select your HLK controller from the drop-down list box at the upper-left corner.

4.  In the **Machine Pool** pane, expand the machine pool hierarchy, right-click the machine pool that you want the user to be able to run a job on, and then click **Properties**.

5.  On the **Security** tab, click **Add**.

6.  In the **User List** dialog box, click the user name, and then click **OK**.

    >[!WARNING]
    >  
    If the user name does not appear in the user list, the user does not have a HLK user account. Create the user account, and then give the user permission to run jobs.

     

7.  In the bottom pane of the **Properties** dialog box, select the **Execute Jobs** check box and clear any check boxes for permissions that you don't want the user to have, and then click **OK**.

 

 






