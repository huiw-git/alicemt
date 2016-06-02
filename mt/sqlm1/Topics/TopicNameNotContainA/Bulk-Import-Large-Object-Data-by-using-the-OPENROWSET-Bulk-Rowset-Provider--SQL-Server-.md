---
title: Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
---
# Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)
  The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] OPENROWSET Bulk Rowset Provider enables you to bulk import a data file as large\-object data.  
  
 The large\-object data types supported by OPENROWSET Bulk Rowset Provider are **varbinary**\(max\) or **image**, **varchar**\(max\) or **text**, and **nvarchar**\(max\) or **ntext**.  
  
> [!NOTE]  
>  The **image**, **text** and **ntext** data types are deprecated.  
  
 The OPENROWSET BULK clause supports three options for importing the contents of a data file as a single\-row, single\-column rowset. You can specify one of these large\-object options instead of using a format file. These options are as follows:  
  
 SINGLE\_BLOB  
 Reads the contents of *data\_file* as a single\-row, returns the contents as a single\-column rowset of type **varbinary\(max\)**.  
  
 SINGLE\_CLOB  
 Reads the contents of the specified data file as characters, returns the contents as a single\-row, single\-column rowset of type **varchar\(max\)**, using the collation of the current database; such as a text or [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Word document.  
  
 SINGLE\_NCLOB  
 Reads the contents of the specified data file as Unicode, returns the contents as a single\-row, single\-column rowset of type **nvarchar\(max\)**, using the collation of the current database.  
  
## See Also  
 [Import Bulk Data by Using BULK INSERT or OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](../Topic/Import%20Bulk%20Data%20by%20Using%20BULK%20INSERT%20or%20OPENROWSET\(BULK...\)%20\(SQL%20Server\).md)   
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../Topic/OPENROWSET%20\(Transact-SQL\).md)   
 [Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;](../Topic/Keep%20Nulls%20or%20Use%20Default%20Values%20During%20Bulk%20Import%20\(SQL%20Server\).md)   
 [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md)  
  
  