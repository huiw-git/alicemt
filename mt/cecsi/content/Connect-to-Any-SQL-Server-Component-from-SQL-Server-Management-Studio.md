---
title: "Connect to Any SQL Server Component from SQL Server Management Studio"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
caps.latest.revision: 5
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
# Connect to Any SQL Server Component from SQL Server Management Studio
[!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] provides functionality for managing every component of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. Use [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] to connect to:  
  
-   An instance of the [!INCLUDE[ssDEnoversion](../content/includes/ssDEnoversion_md.md)].  
  
-   [!INCLUDE[ssASnoversion](../content/includes/ssASnoversion_md.md)].  
  
-   [!INCLUDE[ssISnoversion](../content/includes/ssISnoversion_md.md)].  
  
-   [!INCLUDE[ssRSnoversion](../content/includes/ssRSnoversion_md.md)].  
  
Although [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] allows you to work with queries without first establishing a connection to a data source, most other tasks require a connection. [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] provides the **Connect to Server** dialog box to configure connection properties to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] components. When [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] starts, it opens the **Connect to Server** dialog box and prompts you to connect to a server. The **Connect to Server** dialog box retains the connection settings from the last time it was used.  
  
> [!NOTE]  
> This feature can be turned off so no connection is automatically initiated. For more information, see [Database Engine Service Startup Options](assetId:///d373298b-f6cf-458a-849d-7083ecb54ef5).  
  
## Saving Connections  
You can save connections to specific servers in Registered Servers, or you can save connections in projects with Solution Explorer.  
  
### Saving Connections in Registered Servers  
When you register a server, [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] saves the connection information in Registered Servers. To connect to a registered server, double-click the server name in Registered Servers. Object Explorer then opens a connection to the server.  
  
### Saving Connections in Solution Explorer  
Solution Explorer allows you to store related queries, scripts, connections, and other associated information in a project. Each script project contains a node called **Connections**, where you can save one or more connections. To add a connection, right-click **Connections**, and then click **New Connection**. To access a saved connection, expand **Connections** and double-click the connection. [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] opens a query window associated with that connection. When saved, scripts retain their association to a specific connection.  
  
## See Also  
[Use SQL Server Management Studio](../content/Use-SQL-Server-Management-Studio.md)  
[Object Explorer](../content/Object-Explorer.md)  
  
