---
title: "Server Configuration - Collation"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
caps.latest.revision: 21
caps.handback.revision: 0
manager: jhubbard
---
# Server Configuration - Collation
On the Server Configuration - Collation page of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Installation Wizard, you can modify collation settings that the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] use for sorting purposes. Select the option to match collation settings of different installations of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], or of another computer.  
  
## Options  
 Customize for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] and [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]  
 [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides two groups of collations: Windows collations and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] collations. You can specify separate collation settings for the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] and [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], or you can specify the same collation for both.  
  
 By default, a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] collation is selected for US-English system locales. The default collation for localized versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is determined by the Windows system locale setting for your computer.  
  
 The default settings should be changed only if the collation setting for this installation of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] must match the collation settings used by another instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], or if it must match the Windows system locale of another computer.  
  
 **Note** [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] uses Windows collations only. If you plan to install [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], select a Windows collation during [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup to ensure consistent results between the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] and [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)].  
  
 For more information, see [Collation Settings in Setup](http://go.microsoft.com/fwlink/?LinkId=190977).  
  
## Best Practices  
 For more information about a table of Windows System locales and the corresponding default collations used by [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Setup, see [Collation Settings in Setup](http://go.microsoft.com/fwlink/?LinkId=190977).  
  
 If it is possible, use a single collation for your organization. This way, you do not have to explicitly specify the collation for every database, column, expression, or identifier. If you must work with multiple collations and code page settings, code your queries to consider the rules of collation precedence. For more information, see the Books Online topic for [Collation Precedence (Transact-SQL)](assetId:///58c4e64b-5634-4c29-aa22-33193282dd27).  
  
 When you select a collation for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], consider the following recommendations:  
  
-   Select a BINARY2 collation if binary code point based ordering is acceptable.  
  
-   Select a Windows collation for consistent comparison across data types.  
  
-   Use a new 100-level collation for better linguistic sorting support. For more information, see [Collation and Unicode Support](../../Topics/TopicNameNotContainA/Collation-and-Unicode-Support.md).  
  
-   If you plan to migrate a database to the upgraded instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], select the collation that matches your existing collation of the database.