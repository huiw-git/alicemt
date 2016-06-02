---
title: Convert Types without Conversion Checking (SQL Server Import and Export Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87d9d3e5-477f-4117-a37f-bff53ea3e14d
---
# Convert Types without Conversion Checking (SQL Server Import and Export Wizard)
  After you select the existing tables and views to copy or review the query that you provided, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard shows **Convert Types without Conversion Checking** when the wizard can't locate one or more of the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data type conversion and mapping files. This page asks your consent to continue without knowing whether data type conversions will succeed. The page also includes information that helps you identify the missing file or files.  
  
 For more info about how the wizard maps data types from source columns to destination columns, and about how the wizard uses the data type mapping files, see [How the Wizard maps data types from source to destination](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
 For more info about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Import and Export Wizard and how it works, see [SQL Server Import and Export Wizard](../../Topics\TopicNameNotContainA/SQL-Server-Import-and-Export-Wizard.md).  
  
## Screen shot  
  
The following screen shot shows the **Convert Types without Conversion Checking** page of the Wizard.  
  
![Convert types](../../Images\Image\ImageNotContaina/Convert-types.png)  
  
## What's next?  
 After you agree to continue without knowing whether data type conversions will succeed and click **Next**, the next page is **Save and Run Package**. On this page, you specify whether you want to run the copy operation immediately. Depending on your configuration, you may also be able to save the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package created by the wizard  to customize it and to reuse it. For more info, see [Save and Run Package &#40;SQL Server Import and Export Wizard&#41;](../Topic/Save%20and%20Run%20Package%20\(SQL%20Server%20Import%20and%20Export%20Wizard\).md).  
  
  