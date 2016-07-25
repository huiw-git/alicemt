---
title: "Connect to Server (Analysis Services)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
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
# Connect to Server (Analysis Services)
Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssASnoversion](../content/includes/ssASnoversion_md.md)].  
  
## Options  
**Server type**  
When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], Analysis Services, Reporting Services, or Integration Services. The rest of the dialog shows only the options that apply to the selected server type. When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component. To register a different type of server, select [!INCLUDE[ssDE](../content/includes/ssDE_md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.  
  
**Server name**  
Select the server instance to connect to. The server instance last connected to is displayed by default.  
  
**Authentication**  
The following authentication modes are supported when connecting to an instance of Analysis Services: [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows Authentication.  
  
**Windows Authentication Mode (Windows Authentication)**  
**Windows Authentication** mode allows a user to connect through a Windows user account.  
  
**User name**  
This option is not available in this release. Enter the user name to connect with. This option is only available if you have selected to connect using **Windows Authentication**.  
  
**Password**  
This option is not available in this release. Enter the password for the login. This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Authentication.  
  
**Connect**  
Click to connect to the server selected above.  
  
**Options**  
Click to display additional server connection options, such as registering a server and remembering the password.  
  
