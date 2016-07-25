---
title: "Connect to Server (Login Page) Integration Services"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
caps.latest.revision: 4
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Connect to Server (Login Page) Integration Services
Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssISnoversion](../content/includes/ssISnoversion_md.md)].  
  
## Options  
**Server type**  
When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], Analysis Services, Reporting Services, or Integration Services. The rest of the dialog shows only the options that apply to the selected server type. When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component. To register a different type of server, select [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.  
  
**Server name**  
Select the server to connect to. The server instance last connected to is displayed by default.  
  
> [!NOTE]  
> Do not use *<servername>*\\*<instancename>*, because [!INCLUDE[ssIS](../content/includes/ssIS_md.md)] does not support multiple instances on a computer.  
  
**Authentication**  
Only [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Authentication is available for [!INCLUDE[ssIS](../content/includes/ssIS_md.md)]. Windows Authentication mode allows a user to connect through a Windows user account.  
  
**User name**  
This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../content/includes/ssIS_md.md)].  
  
**Password**  
This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../content/includes/ssIS_md.md)].  
  
**Remember password**  
This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../content/includes/ssIS_md.md)].  
  
**Connect**  
Connect to the server selected above.  
  
**Options**  
Click to change the dialog and hide the additional server connection options, such as remembering the password.  
  
