---
title: Understand SQL Server Management Studio Windows Management
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bebf8383-dcaf-466e-84f5-63b81c9cfe52
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
# Understand SQL Server Management Studio Windows Management
The tool windows in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] are a highly functional, flexible, and efficient system that allows you to:  
  
-   Maximize the user workspace for development and management.  
  
-   Reduce the number of unused windows displayed at one time.  
  
-   Easily customize the user environment.  
  
Manipulating windows is central to the [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] environment. Users can easily access the tools and windows they use frequently. Users can control how much space they want to allocate to different information, and the environment should maximize the space available for editing queries accordingly. Windows can be moved to different locations on the screen. Many windows can be undocked and dragged out of the [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] frame. This is particularly useful when using more than one monitor.  
  
To increase your editing space while maintaining functionality, all windows offer the Auto Hide feature, which displays the window as a tab within a bar along the border of the main [!INCLUDE[ssManStudio](../content/includes/ssManStudio_md.md)] environment. When the pointer is placed over one of these tabs, the underlying window reveals itself. Auto Hide for a window can be toggled by clicking the **Auto Hide** button, represented by a pushpin in the upper\-right corner of the window. There is also an **Auto Hide All** option on the **Window** menu.  
  
Some components can be configured in either tabbed mode where components appear as tabs in the same docking location, or in multiple document interface (MDI) mode where each document has its own window. To configure this feature, on the **Tools** menu, click **Options**, click **Environment**, and then click **General**.  
  
> [!IMPORTANT]  
> When a login (or a contained database user) connects and is authenticated, the connection stores identity information about the login. For a Windows Authentication login, this includes information about membership in Windows groups. The identity of the login remains authenticated as long as the connection is maintained. To force changes in the identity, such as a password reset or change in Windows group membership, the login must logoff from the authentication authority (Windows or [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]), and log in again. A member of the **sysadmin** fixed server role or any login with the **ALTER ANY CONNECTION** permission can use the **KILL** command to end a connection and force a login to reconnect. [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] can reuse connection information when opening multiple connections to Object Explorer and Query Editor windows. Close all connections to force reconnection.  
  
> [!IMPORTANT]  
> When a login (or a contained database user) connects and is authenticated, the connection caches identity information about the login. For a Windows Authentication login, this includes information about membership in Windows groups. The identity of the login remains authenticated as long as the connection is maintained. To force changes in the identity, such as a password reset or change in Windows group membership, the login must logoff from the authentication authority (Windows or [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]), and log in again. A member of the **sysadmin** fixed server role or any login with the **ALTER ANY CONNECTION** permission can use the **KILL** command to end a connection and force a login to reconnect. [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)] can reuse connection information when opening multiple connections to Object Explorer and Query Editor windows. Close all connections to force reconnection.  
  
## See Also  
[Use SQL Server Management Studio](../content/Use-SQL-Server-Management-Studio.md)  
[The SQL Server Management Studio Environment](../content/The-SQL-Server-Management-Studio-Environment.md)  
  
