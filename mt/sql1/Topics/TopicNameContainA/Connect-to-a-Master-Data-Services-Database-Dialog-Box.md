---
title: "Connect to a Master Data Services Database Dialog Box"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2f8c9b9-c31e-4f0d-9095-978709423190
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Connect to a Master Data Services Database Dialog Box
Use the **Connect to a Master Data Services Database** dialog box to select a [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
 In [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)], this dialog is available from the following pages:  
  
-   On the **Database Configuration** page, click **Select Database.** Use this dialog to select a database for which to configure system settings.  
  
-   On the **Web Configuration** page, under **Associate Application with Database**, click **Select** to select the database to associate with your [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] website or application.  
  
## Select Database  
 Specify information to connect to a local or remote [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] instance that hosts the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. To connect to a remote instance, it must be enabled for remote connections.  
  
|Control Name|Description|  
|------------------|-----------------|  
|**SQL Server instance**|Specify the name of the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] instance that you want to host the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. This can be a default or named instance on either a local or a remote computer. Specify the information by typing:<br /><br /> A period (.) to connect to the default instance on your local computer.<br /><br /> The server name or IP address to connect to the default instance on the specified local or remote computer.<br /><br /> The server name or IP address, and the instance name to connect to the named instance on the specified local or remote computer. Specify this information in the format *server_name*\\*instance_name*.|  
|**Authentication type**|Select the type of authentication to use when connecting to the specified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance. The credentials that you use to connect determine the databases that are displayed in the **Master Data Services database** drop-down list.<br /><br /> The authentication types include:<br /><br /> **Current User – Integrated Security**: Uses Integrated Windows Authentication to connect by using the credentials of the current Windows user account. [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)] uses the Windows credentials of the user who logged on to the computer and opened the application. You cannot specify different Windows credentials in the application. If you want to connect with different Windows credentials, you must log on to the computer as that user and then open the [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)].<br /><br /> **SQL Server Account**: Uses a SQL Server account to connect. When you select this option, the **User name** and **Password** fields are enabled and you must specify credentials for a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] account on the specified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.|  
|**User name**|Specify the name of the user account that will be used to connect to the specified SQL Server instance. The account must be part of the **sysadmin** role on the specified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance:<br /><br /> When the **Authentication type** is **Current User – Integrated Security**, the **User name** box is read-only and it displays the name of the Windows user account that is logged on to the computer.<br /><br /> When the **Authentication type** is **SQL Server Account**, the **User name** box is enabled and you must specify credentials for a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] account on the specified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.|  
|**Password**|Specify the password associated with the user account:<br /><br /> When the **Authentication type** is **Current User – Integrated Security**, the **Password** box is read-only and credentials of the specified Windows user account are used to connect.<br /><br /> When the **Authentication type** is **SQL Server Account**, the **Password** box is enabled and you must specify the password associated with the specified user account.|  
|**Connect**|Connect to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance with the specified credentials.|  
|**Master Data Services database**|Displays the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] databases in the specified [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance based on the following criteria:<br /><br /> When the user is a member of the **sysadmin** server role for that instance, all [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] databases in that instance are displayed.<br /><br /> When the user is a member of the **db_owner** database role for any [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] databases in that instance, those [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] databases are displayed.<br /><br /> <br /><br /> For more information about SQL Server roles, see [Server-Level Roles](../../Topics/TopicNameNotContainA/Server-Level-Roles.md) and [Database-Level Roles](../../Topics/TopicNameNotContainA/Database-Level-Roles.md).|  
  
## See Also  
 [Database Configuration Page (Master Data Services Configuration Manager)](../../Topics/TopicNameNotContainA/Database-Configuration-Page--Master-Data-Services-Configuration-Manager-.md)   
 [Get Started with Master Data Services (SQL Server 2016)](../../Topics/TopicNameNotContainA/Get-Started-with-Master-Data-Services--SQL-Server-2016-.md)