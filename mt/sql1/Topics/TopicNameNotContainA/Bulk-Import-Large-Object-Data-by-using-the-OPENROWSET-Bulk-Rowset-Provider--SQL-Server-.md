---
title: "Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-bulk-import-export
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
caps.latest.revision: 17
manager: jhubbard
---
# Bulk Import Large-Object Data by using the OPENROWSET Bulk Rowset Provider (SQL Server)
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] OPENROWSET Bulk Rowset Provider enables you to bulk import a data file as large-object data.  
  
 The large-object data types supported by OPENROWSET Bulk Rowset Provider are **varbinary**(max) or **image**, **varchar**(max) or **text**, and **nvarchar**(max) or **ntext**.  
  
> [!NOTE]  
>  The **image**, **text** and **ntext** data types are deprecated.  
  
 The OPENROWSET BULK clause supports three options for importing the contents of a data file as a single-row, single-column rowset. You can specify one of these large-object options instead of using a format file. These options are as follows:  
  
 SINGLE_BLOB  
 Reads the contents of *data_file* as a single-row, returns the contents as a single-column rowset of type **varbinary(max)**.  
  
 SINGLE_CLOB  
 Reads the contents of the specified data file as characters, returns the contents as a single-row, single-column rowset of type **varchar(max)**, using the collation of the current database; such as a text or [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Word document.  
  
 SINGLE_NCLOB  
 Reads the contents of the specified data file as Unicode, returns the contents as a single-row, single-column rowset of type **nvarchar(max)**, using the collation of the current database.  
  
## See Also  
 [Import Bulk Data by Using BULK INSERT or OPENROWSET(BULK...) (SQL Server)](../../Topics/TopicNameNotContainA/Import-Bulk-Data-by-Using-BULK-INSERT-or-OPENROWSET-BULK...---SQL-Server-.md)   
 [BACKUP](assetId:///89a4658a-62f1-4289-8982-f072229720a1)   
 [OPENROWSET (Transact-SQL)](assetId:///f47eda43-33aa-454d-840a-bb15a031ca17)   
 [Keep Nulls or Use Default Values During Bulk Import (SQL Server)](../../Topics/TopicNameNotContainA/Keep-Nulls-or-Use-Default-Values-During-Bulk-Import--SQL-Server-.md)   
 [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md)   
 [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2)