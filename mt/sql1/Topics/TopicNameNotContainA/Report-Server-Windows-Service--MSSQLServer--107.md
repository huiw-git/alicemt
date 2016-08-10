---
title: "Report Server Windows Service (MSSQLServer) 107"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52b5704b-27f9-400a-a821-d8fa0786afe4
caps.latest.revision: 21
caps.handback.revision: 0
manager: mblythe
---
# Report Server Windows Service (MSSQLServer) 107
## Details  
  
|||  
|-|-|  
|Product Name|[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]|  
|Event ID|107|  
|Event Source|Report Server Windows Service|  
|Component|[!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]|  
|Message Text|Report Server Windows Service (MSSQLSERVER) cannot connect to the report server database.|  
  
## Explanation  
 The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Report Server service cannot connect to the report server database. This error occurs during a service restart if a connection to the report server database cannot be established. Conditions under which this error occurs include the following:  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] service is not running when the Report Server service starts.  
  
-   The connection to the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] service fails because remote connections or the TCP/IP protocol is not enabled.  
  
-   The report server database is not configured correctly.  
  
-   The service account is not configured correctly, or the account no longer has permissions on the report server database. This can occur if you do not use the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration tool to set up the account or the report server database.  
  
## User Action  
 Start the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] service if it is not running and check that remote connections are enabled for TCP/IP protocol.  
  
 Use the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration tool to configure the report server database and service account.  
  
## Internal-Only  
  
## See Also  
 [Configure the Report Server Service Account (SSRS Configuration Manager)](../../Topics/TopicNameNotContainA/Configure-the-Report-Server-Service-Account--SSRS-Configuration-Manager-.md)   
 [Reporting Services Configuration Manager (Native Mode)](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Manager--Native-Mode-.md)   
 [Start and Stop the Report Server Service](../../Topics/TopicNameNotContainA/Start-and-Stop-the-Report-Server-Service.md)