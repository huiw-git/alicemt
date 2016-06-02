---
title: Install SQL Server PowerShell
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
---
# Install SQL Server PowerShell
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup automatically configures PowerShell components.  
  
## Installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell Support  
 You install the software that provides [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] support for Windows PowerShell by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. When you select any [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features that require PowerShell support Setup installs the following [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell components:  
  
-   The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] PowerShell snap\-ins. The snap\-ins are dll files that implement two types of Windows PowerShell support for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
    -   A set of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cmdlets. Cmdlets are commands that implement a specific action. For example, **Invoke\-Sqlcmd** runs a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] or XQuery script that can also be run by using the **sqlcmd** utility, and **Invoke\-PolicyEvaluation** reports whether [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects comply with policy\-based management policies.  
  
    -   A [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] provider. The provider lets you navigate the hierarchy of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects using a path similar to a file system path. Each object is associated with a class from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Management object models. You can use the methods and properties of the class to perform work on the objects. For example, if you cd to a databases object in a path, you can use the methods and properties of the Microsoft.SqlServer.Managment.SMO.Database class to manage the database.  
  
-   The **sqlps** module that is imported into Windows PowerShell sessions to load the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] snap\-ins.  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] supports starting Windows PowerShell sessions from the Object Explorer tree. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent supports Windows PowerShell job steps.  
  
 Windows Server 2012 and later and Windows 8 and later come with PowerShell installed and configured. For information about installing Windows PowerShell see [Installing Windows PowerShell](http://msdn.microsoft.com/library/hh847837.aspx) page.  
  
## See Also  
 [SQL Server PowerShell](../../Topics\TopicNameNotContainA/SQL-Server-PowerShell.md)  
  
  