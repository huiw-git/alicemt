---
title: Agent XPs Server Configuration Option
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
---
# Agent XPs Server Configuration Option
  Use the **Agent XPs** option to enable the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent extended stored procedures on this server. When this option is not enabled, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent node is not available in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] Object Explorer.  
  
 When you use the [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] tool to start the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service, these extended stored procedures are enabled automatically. For more information, see [Surface Area Configuration](../../Topics\TopicNameNotContainA/Surface-Area-Configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] Object Explorer does not display the contents of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]Agent node unless these extended stored procedures are enabled regardless of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service state.  
  
 The possible values are:  
  
-   **0**, indicating that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent extended stored procedures are not available \(the default\).  
  
-   **1**, indicating that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent extended stored procedures are available.  
  
 The setting takes effect immediately without a server stop and restart.  
  
## Examples  
 The following example enables the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent extended stored procedures.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## See Also  
 [Automated Administration Tasks &#40;SQL Server Agent&#41;](../Topic/Automated%20Administration%20Tasks%20\(SQL%20Server%20Agent\).md)   
 [Start, Stop, or Pause the SQL Server Agent Service](../Topic/Start,%20Stop,%20or%20Pause%20the%20SQL%20Server%20Agent%20Service.md)  
  
  