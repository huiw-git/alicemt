---
title: "WMI Connection Manager Editor"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ef2c913-0779-4a07-989e-3361cd83170b
caps.latest.revision: 29
manager: jhubbard
---
# WMI Connection Manager Editor
Use the **WMI Connection Manager** dialog box to specify a Microsoft Windows Management Instrumentation (WMI) connection to a server.  
  
 To learn more about the WMI connection manager, see [WMI Connection Manager](../../Topics/TopicNameNotContainA/WMI-Connection-Manager.md).  
  
## Options  
 **Name**  
 Provide a unique name for the connection manager.  
  
 **Description**  
 Describe the connection manager. As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.  
  
 **Server name**  
 Provide the name of the server to which you want to make the WMI connection.  
  
 **Namespace**  
 Specify the WMI namespace.  
  
 **Use Windows authentication**  
 Select to use Windows Authentication. If you use Windows Authentication, you do not need to provide a user name or password for the connection.  
  
 **User name**  
 If you do not use Windows Authentication, you must provide a user name for the connection.  
  
 **Password**  
 If you do not use Windows Authentication, you must provide the password for the connection.  
  
 **Test**  
 Test the connection manager settings.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [WMI Provider for Configuration Management Concepts](assetId:///7e41db24-b915-4eb8-a1d6-e6948ee915b7)   
 [WMI Provider for Server Events Concepts](assetId:///80767fe0-32ac-406a-81a0-8212cd6ce7e4)