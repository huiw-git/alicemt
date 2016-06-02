---
title: Reporting Services Login Dialog Box (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
---
# Reporting Services Login Dialog Box (SSRS)
  Use the **Reporting Services Login** dialog box to provide credentials to publish reports to the report server.  
  
-   **Note** If this is the first time you have published a report to a report server since set you set the deployment property **TargetServerURL** for a project, verify that the server name includes **server** and not **reports**. For example, `http://localhost/reportserver`, and not `http://localhost/reports`. Specifying the `reports` directory on the local server instead of the `reportserver` directory indirectly causes this dialog box to open. For more information about setting **TargetServerURL**, see [Set Deployment Properties &#40;Reporting Services&#41;](../Topic/Set%20Deployment%20Properties%20\(Reporting%20Services\).md).  
  
## Options  
 **Server**  
 Displays the name of the report server. For example, `http://localhost/reportserver`. For report servers that use a different port than default port 80, include the port number. For example, `http://localhost:81/reportserver`.  
  
 **User name**  
 Type the user name to log in to the Web service.  
  
 **Password**  
 Type the password to log in to the Web service.  
  
## See Also  
 [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)   
 [Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)   
 [Report Designer F1 Help](../../Topics\TopicNameNotContainA/Report-Designer-F1-Help.md)  
  
  