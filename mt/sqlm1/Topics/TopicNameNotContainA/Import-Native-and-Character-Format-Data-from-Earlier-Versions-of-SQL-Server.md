---
title: Import Native and Character Format Data from Earlier Versions of SQL Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
---
# Import Native and Character Format Data from Earlier Versions of SQL Server
  In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you can use **bcp** to import native and character format data from [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)], [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], or [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] by using the **\-V** switch. The **\-V** switch causes [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] to use data types from the specified earlier version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and the data file format are the same as the format in that earlier version.  
  
 To specify an earlier [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version for a data file, use the **\-V** switch with one of the following qualifiers:  
  
|SQL Server version|Qualifier|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)]|**\-V80**|  
|[!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)]|**\-V90**|  
|[!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]|**\-V100**|  
|[!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]|**\-V 110**|  
  
## Interpretation of Data Types  
 [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions have support for some new types. When you want to import a new data type into an earlier [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version, the data type must be stored in a format that readable by the older **bcp** clients. The following table summarizes how the new data types are converted for compatibility with the earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
|New data types in SQL Server 2005|Compatible data types in version 6*x*|Compatible data types in version 70|Compatible data types in version 80|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|**bigint**|**decimal**|**decimal**|\*|  
|**sql\_variant**|**text**|**nvarchar\(4000\)**|\*|  
|**varchar\(max\)**|**text**|**text**|**text**|  
|**nvarchar\(max\)**|**ntext**|**ntext**|**ntext**|  
|**varbinary\(max\)**|**image**|**image**|**image**|  
|XML|**ntext**|**ntext**|**ntext**|  
|UDT\*\*|**image**|**image**|**image**|  
  
 \*This type is natively supported.  
  
 \*\*UDT indicates a user defined type.  
  
## Exporting using –V 80  
 When you bulk export data by using the **–V80** switch, **nvarchar\(max\)**, **varchar\(max\)**, **varbinary\(max\)**, XML, and UDT data in native mode are stored with a 4\-byte prefix, like **text**, **image**, and **ntext** data, rather than with an 8\-byte prefix, which is the default for [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions.  
  
## Copying Date Values  
 **bcp** uses the ODBC bulk copy API. Therefore, to import date values into [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], **bcp** uses the ODBC date format \(*yyyy\-mm\-dd hh:mm:ss*\[*.f...*\]\).  
  
 The **bcp** command exports character format data files using the ODBC default format for **datetime** and **smalldatetime** values. For example, a **datetime** column containing the date `12 Aug 1998` is bulk copied to a data file as the character string `1998-08-12 00:00:00.000`.  
  
> [!IMPORTANT]  
>  When importing data into a **smalldatetime** field using **bcp**, be sure the value for seconds is 00.000; otherwise the operation will fail. The **smalldatetime** data type only holds values to the nearest minute. BULK INSERT and INSERT ... SELECT \* FROM OPENROWSET\(BULK...\) will not fail in this instance but will truncate the seconds value.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To use data formats for bulk import or bulk export**  
  
-   [Use Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Character%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
-   [Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;](../Topic/Use%20Unicode%20Native%20Format%20to%20Import%20or%20Export%20Data%20\(SQL%20Server\).md)  
  
## See Also  
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [Data Types &#40;Transact-SQL&#41;](../Topic/Data%20Types%20\(Transact-SQL\).md)   
 [SQL Server Database Engine Backward Compatibility](../../Topics\TopicNameNotContainA/SQL-Server-Database-Engine-Backward-Compatibility.md)   
 [CAST and CONVERT &#40;Transact-SQL&#41;](../Topic/CAST%20and%20CONVERT%20\(Transact-SQL\).md)  
  
  