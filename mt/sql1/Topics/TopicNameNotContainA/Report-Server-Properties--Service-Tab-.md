---
title: "Report Server Properties (Service Tab)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a2e1dbf-02b9-4893-aaf0-c0e4a2c9b4f9
caps.latest.revision: 23
manager: jhubbard
---
# Report Server Properties (Service Tab)
This service is the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Report Server service. The property values in light gray cannot be changed by using this application.  
  
## Options  
 **Binary Path**  
 Displays the location of the program files used by this service.  
  
 **Error Control**  
 1 indicates "SERVICE_ERROR_NORMAL". If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation. This value cannot be changed.  
  
 **Exit Code**  
 When an error occurs, the error number appears in this box. Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Knowledge Base or provide the number to your technical support staff.  
  
 **Host Name**  
 Displays the name of the computer or cluster running the full text search.  
  
 **Name**  
 Indicates the display name of the service.  
  
 **Process ID**  
 Displays the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows process ID.  
  
 **SQL Service Type**  
 Type of service provided to calling processes. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] installs several services.  
  
 **Start Mode**  
 Set this service to the following choices:  
  
-   Manual: This service does not automatically start when the computer starts. You must start the service using [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, or some other tool.  
  
-   Automatic: This service attempts to start when this computer starts.  
  
-   Disabled: This service cannot be started.  
  
 **State**  
 Indicates whether this service is running, stopped, or disabled.  
  
## See Also  
 [SQL Server Services](../../Topics/TopicNameNotContainA/SQL-Server-Services.md)