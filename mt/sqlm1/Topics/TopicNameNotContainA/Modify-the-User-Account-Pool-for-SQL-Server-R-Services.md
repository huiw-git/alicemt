---
title: Modify the User Account Pool for SQL Server R Services
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
---
# Modify the User Account Pool for SQL Server R Services
  As part of the installation process for [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)], a new Windows *user account pool* is created to support execution of tasks by the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service. The number of user accounts in this pool determines how many R sessions can be active simultaneously.  
  
-   In a default instance, the group name is **SQLRUserGroup** 
-   In a named instance, the default group name is suffixed with the instance name: for example, **SQLRUserGroupMyInstanceName** 
-   Accounts: By default, the user account pool contains 20 user accounts, named **MSSQLSERVER01** through **MSSQLSERVER20** for the default instance.  
-   For a named instance, the user accounts are named using the instance name: for example, **MyInstanceName01** through **MyInstanceName20**.  

## Managing the User Group for Each Instance
The Windows account group is created by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup for  each instance on which R Services is installed, so if you have installed multiple instance that support R, there will be multiple user groups.
However, each user group is associated with the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service on a specific instance and cannot support R jobs that run on other instances.

By default, the group does **not** have login permissions on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance with which it is associated. If you need to to enable execution of R scripts by users, the database administrator must provide this group with **Connect to** permissions.  

### Changing the number of worker accounts in the Windows user group

To modify the number of users in the account pool, you must edit the properties of the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)] service as described below.  
  
You can also specify a common prefix be used with all passwords for the accounts in this user account pool. By default, passwords associated with each user account are generated at random. By specifying a prefix to use in all passwords, you can more easily identify the  accounts that are related to the R service.  
  
  
2. Open SQL Server Configuration Manager and select **SQL Server Services**.
3. Double-click the SQL Server Launchpad service and stop the service if it is running. 
4.  On the **Service** tab, make sure that the Start Mode is set to Automatic. R scripts will fail if the LaunchPad is not running.
5.  Click the **Advanced** tab and edit the value of **External Users Count** if necessary. The default is 20 accounts, which in most cases is more than adequate to support R sessions. You can decrease the value if memory is limited.
6. Optionally, you can set the option **Reset External Users Password** to _Yes_ if your organization has a policy that requires changing passwords every 90 days. Doing this will regenerate the encrypted passwords that LaunchPad maintains for the user accounts.    
6.  Restart the service.  

  
## See Also  
 [enter link description here](Configuration%20\(SQL%20Server%20R%20Services\).md)
  