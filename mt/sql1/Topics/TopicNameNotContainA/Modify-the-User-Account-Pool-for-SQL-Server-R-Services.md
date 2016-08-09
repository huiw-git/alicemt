---
title: "Modify the User Account Pool for SQL Server R Services"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-26
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: 9
caps.handback.revision: 0
manager: paulettm
---
# Modify the User Account Pool for SQL Server R Services
As part of the installation process for [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], a new Windows *user account pool* is created to support execution of tasks by the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] service. The number of user accounts in this pool determines how many R sessions can be active simultaneously.  
  
-   Group name: **SQLRUsergroup** for default instance, **SQLRUsergroup<instance_name>** for named instances  
  
     The Windows account group is created by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] setup for  each instance on which R Services is installed; however, the group does not have login permissions on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.  
  
     Therefore, to enable execution of R scripts by users, the database administrator must provide this group with **Connect to** permissions.  
  
-   Accounts: By default, the user account pool contains 20 users, named **MSSQLSERVER01** through **MSSQLSERVER20** for the default instance.  
  
     For named instance, the members are named **InstanceName01** through **InstanceName20**.  
  
 To modify the number of users in the account pool, you must edit the  configuration file and re-run the script as described below.  
  
 You can also specify a common prefix be used with all passwords for the accounts in this user account pool. By default, passwords associated with each user account are generated at random. By specifying a prefix to use in all passwords, you can more easily identify the  accounts that are related to the R service.  
  
### Stop the Launchpad service  
  
-   Open the **Services** panel in Control Panel and stop the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] service.  
  
### Edit the configuration file  
  
1.  Locate the installation script file `RegisterRExt.exe` and the configuration file that it generates, RegisterRExt.exe.config. If you have used the default installation, the path to the file will be something like this:  
  
     C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64  
  
2.  Make a copy of the .config file before proceeding.  
  
    > [!NOTE]  
    >  You will need administrative access to the folder to modify files.  
  
3.  Open the config file using Notepad or another text editor, and locate the following key-value pair:  
  
     <add key="UserAccountPoolSize" value="20" /\>  
  
4.  Increase the value to support additional R sessions. Decrease the value if memory or users are limited.  
  
### Change the common prefix for pool account passwords  
  
1.  Locate the key-value pair that specifies the prefix used for all accounts in the user account pool.  
  
     <add key="UserAccountPasswordPrefix" value="Aa$1" /\>  
  
2.  Type an appropriate string to replace the default prefix "Aa$1". For example, if you type RSql$1, the password for each account will begin with the string RSql$1.  
  
3.  Save the configuration file.  
  
### Run the configuration script and restart the service  
  
1.  Open an administrative command prompt in the directory where RegisterRExt.exe is located, and run the script.  
  
2.  Restart the [!INCLUDE[rsql_launchpad](../../Topics/TopicNameNotContainA/tokens/rsql_launchpad_md.md)] service.  
  
## See Also  
 [Post-Installation Server Configuration (SQL Server R Services)](../../Topics/TopicNameNotContainA/Post-Installation-Server-Configuration--SQL-Server-R-Services-.md)