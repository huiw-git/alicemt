---
title: "Unicode Compression Implementation"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-data-compression
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Unicode Compression Implementation
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] uses an implementation of the Standard Compression Scheme for Unicode (SCSU) algorithm to compress Unicode values that are stored in row or page compressed objects. For these compressed objects, Unicode compression is automatic for **nchar(n)** and **nvarchar(n)** columns. The [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] stores Unicode data as 2 bytes, regardless of locale. This is known as UCS-2 encoding. For some locales, the implementation of SCSU compression in SQL Server can save up to 50 percent in storage space.  
  
## Supported Data Types  
 Unicode compression supports the fixed-length **nchar(n)** and **nvarchar(n)** data types. Data values that are stored off row or in **nvarchar(max)** columns are not compressed.  
  
> [!NOTE]  
>  Unicode compression is not supported for **nvarchar(max)** data even if it is stored in row. However, this data type can still benefit from page compression.  
  
## Upgrading from Earlier Versions of SQL Server  
 When a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database is upgraded to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], Unicode compression–related changes are not made to any database object, compressed or uncompressed. After the database is upgraded, objects are affected as follows:  
  
-   If the object is not compressed, no changes are made and the object continues to function as it did previously.  
  
-   Row- or page-compressed objects continue to function as they did previously. Uncompressed data remains in uncompressed form until its value is updated.  
  
-   New rows that are inserted into a row- or page-compressed table are compressed using Unicode compression.  
  
    > [!NOTE]  
    >  To take full advantage of the benefits of Unicode compression, the object must be rebuilt with page or row compression.  
  
## How Unicode Compression Affects Data Storage  
 When an index is created or rebuilt or when a value is changed in a table that was compressed with row or page compression, the affected index or value is stored compressed only if its compressed size is less than its current size. This prevents rows in a table or index from increasing in size because of Unicode compression.  
  
 The storage space that compression saves depends on the characteristics of the data that is being compressed and the locale of the data. The following table lists the space savings that can be achieved for several locales.  
  
|Locale|Compression percent|  
|------------|-------------------------|  
|English|50%|  
|German|50%|  
|Hindi|50%|  
|Turkish|48%|  
|Vietnamese|39%|  
|Japanese|15%|  
  
## See Also  
 [Data Compression](../../Topics/TopicNameNotContainA/Data-Compression.md)   
 [sp_estimate_data_compression_savings (Transact-SQL)](assetId:///6f6c7150-e788-45e0-9d08-d6c2f4a33729)   
 [Page Compression Implementation](../../Topics/TopicNameNotContainA/Page-Compression-Implementation.md)   
 [sys.dm_db_persisted_sku_features (Transact-SQL)](assetId:///b4b29e97-b523-41b9-9528-6d4e84b89e09)