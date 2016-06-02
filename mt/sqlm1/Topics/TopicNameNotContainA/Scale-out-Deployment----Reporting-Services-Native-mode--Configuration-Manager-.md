---
title: Scale-out Deployment  - Reporting Services Native mode (Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4df38294-6f9d-4b40-9f03-1f01c1f0700c
robots: noindex,nofollow
---
# Scale-out Deployment  - Reporting Services Native mode (Configuration Manager)
  Use the **Scale\-out Deployment** page in [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to view the initialization status for a scale\-out deployment or to join a report server to a scale\-out deployment. A *scale\-out deployment* refers to two or more report server instances that share a single report server database.  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
 An *initialized report server* describes a server that can encrypt and decrypt sensitive data that is stored in a report server database \(stored credentials and connection strings are examples of encrypted data that is stored in the database\). Report server initialization is a requirement for report server operations.  
  
 A *scale\-out deployment* is used in the following scenarios:  
  
-   As a prerequisite for load balancing multiple report servers in a server cluster. Before you can load balance multiple report servers, you must first configure them to share the same report server database.  
  
-   To segment report server applications on different computers, by using one server for interactive report processing and a second server for scheduled report processing. In this scenario, each server instance processes different types of requests for the same report server content stored in the shared report server database.  
  
 To configure a scale\-out deployment, start with two or more report server instances that are all connected to the same report server database. After all of the instances are installed, you connect to the first report server and then use the Scale\-out Deployment page to join each additional instance. Only a report server that is already initialized to use a database can initialize additional nodes.  
  
 To open this page, start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager and select **Scale\-out Deployment** in the navigation pane. For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md).  
  
## Options  
 **SQL Server Name**  
 Specify the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance that hosts the report server database.  
  
 **Database Name**  
 Specifies the name of the database to which the report server instance is currently connected.  
  
 **Server Mode**  
 Displays the mode of server and database. The server mode is either Native or SharePoint integrated. Scale\-out deployments are supported for both modes.  
  
 **Server**  
 Shows the report server name. In most cases, this is the name of the computer on which the report server is installed.  
  
 **Instance**  
 Shows the report server instance name. Report server instances are based on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instances.  
  
 **Status**  
 Indicates whether the report server is initialized or waiting to join a scale\-out deployment:  
  
-   For a standalone report server that is not part of a scale\-out deployment, this page shows that the report server instance is initialized with respect to its dedicated report server database. Status is set to **Joined**.  
  
-   For a report server that is waiting to join a scale\-out deployment, this page contains empty values for Server, Instance, and Status. A report server is waiting to join a scale\-out deployment if you selected an existing report server database that is already used by another report server instance. A message on this page instructs you to connect to a report server that is already joined to the farm. To complete this request, click **Connect**, select a report server that is already initialized to use the report server database, click **Scale\-out Deployment**, select the report server instance that is **Waiting to Join**, and then click **Initialize**.  
  
-   For a report server that is currently part of a scale\-out deployment, this page shows initialization status for all of the report server instances that share the same report server database. When viewing status for a scale\-out deployment, it does not matter which server you are connected to. The status information is reported identically for all nodes in the scale\-out deployment.  
  
     For a report server that is already part of a scale\-out deployment, you can use this page to add or remove nodes.  
  
 **Initialize**  
 Click **Initialize** to add a report server to the scale\-out deployment. This step configures a report server to use a symmetric key in a shared report server database. You can use **Initialize** to add a report server instance to a scale\-out deployment or to troubleshoot a migration or installation problem.  
  
 A report server instance is only available if you have previously configured a connection to the shared report server database. In addition, you must perform the initialization from a report server that is already initialized to use the report server database.  
  
 **Remove**  
 Click **Remove** to remove the encryption keys of the selected report server instance from the report server database. You can remove keys to remove a report server from a scale\-out deployment or to troubleshoot a migration or installation problem. With this option, only the encryption keys for the specified report server instance are removed. Encrypted data in the report server database is not affected.  
  
 As a precaution, be sure to create a backup copy of the symmetric key before you remove it. Once you remove the encryption keys of the last report server in the list, you introduce new requirements for any subsequent report server initialization for that database. The new requirement is that after you initialize a report server you must restore a backup copy of the symmetric key. Restoring the symmetric key is necessary if you want to access the encrypted data that is currently in the report server database.  
  
 If you no longer need the encrypted data or if you do not have a backup copy of the key, you must delete the encrypted data. For more information, see [Encryption Keys - Reporting Services Native mode &#40;Configuration Manager&#41;](../Topic/Encryption%20Keys%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md).  
  
## See Also  
 [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../Topic/Initialize%20a%20Report%20Server%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20and%20Manage%20Encryption%20Keys%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Native%20Mode%20Report%20Server%20Scale-Out%20Deployment%20\(SSRS%20Configuration%20Manager\).md)  
  
  