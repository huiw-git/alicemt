---
title: Run Windows PowerShell from SQL Server Management Studio
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
---
# Run Windows PowerShell from SQL Server Management Studio
  You can start Windows PowerShell sessions from **Object Explorer** in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] launches Windows PowerShell, loads the **sqlps** module, and sets the path context to the associated node in the **Object Explorer** tree.  
  
## Before You Begin  
 When you specify running PowerShell for an object in **Object Explorer**, [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] starts a Windows PowerShell session in which the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell snap\-ins have been loaded and registered. The path for the session is preset to the location of the object you right clicked in Object Explorer. For example, if you right\-click the [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database object in Object Explorer and select **Start PowerShell**, the Windows PowerShell path is set to the following:  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## Run PowerShell  
 **To run PowerShell from SQL Server Management Studio**  
  
1.  Open **Object Explorer**.  
  
2.  Navigate to the node for the object to be worked on.  
  
3.  Right\-click the object and select **Start PowerShell**.  
  
## Permissions  
 When opened from [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], PowerShell does not run with Administrator privileges which may prevent some activities such as calls to WMI.  
  
## See Also  
 [SQL Server PowerShell](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell.md)  
  
  