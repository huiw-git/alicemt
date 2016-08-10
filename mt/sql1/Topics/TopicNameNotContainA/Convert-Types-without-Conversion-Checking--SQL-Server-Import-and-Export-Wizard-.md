---
title: "Convert Types without Conversion Checking (SQL Server Import and Export Wizard)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# Convert Types without Conversion Checking (SQL Server Import and Export Wizard)
After you select the existing tables and views to copy or review the query that you provided, the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard shows **Convert Types without Conversion Checking** when the wizard can't locate one or more of the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] data type conversion and mapping files. This page asks your consent to continue without knowing whether data type conversions will succeed. The page also includes information that helps you identify the missing file or files.  
  
 For more info about how the wizard maps data types from source columns to destination columns, and about how the wizard uses the data type mapping files, see [How the Wizard maps data types from source to destination](../../Topics/TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md#wizardMapping).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics/TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## What's next?  
 After you agree to continue without knowing whether data type conversions will succeed and click **Next**, the next page is **Save and Execute Package**. On this page, you specify whether you want to run the copy operation immediately. Depending on your configuration, you may also be able to save the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] package created by the wizard  to customize it and to reuse it. For more info, see [Save and Run Package (SQL Server Import and Export Wizard)](../../Topics/TopicNameNotContainA/Save-and-Run-Package--SQL-Server-Import-and-Export-Wizard-.md).