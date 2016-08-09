---
title: "Modify XML Indexes"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
caps.latest.revision: 13
manager: jhubbard
---
# Modify XML Indexes
The [ALTER INDEX](assetId:///b796c829-ef3a-405c-a784-48286d4fb2b9)[!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] DDL statement can be used to modify existing XML and non-XML indexes. However, not all the ALTER INDEX options are available to XML indexes. The following options are not valid when modifying XML indexes:  
  
-   The rebuild and set option IGNORE_DUP_KEY is not valid for XML indexes. The rebuild option ONLINE must be set to OFF for secondary XML indexes. The option DROP_EXISTING is not permitted in the ALTER INDEX statement.  
  
-   The modifications of the primary key constraint in the user table are not automatically propagated to XML indexes. The user must drop the XML indexes first and then re-create them.  
  
-   If ALTER INDEX ALL is specified, it applies to both non-XML and XML indexes. Indexing options may be specified that are not valid for both types of indexes. In this case, the whole statement fails.  
  
## Example: Modifying an XML Index  
 In the following example, an XML index is created and then modified by setting the option `ALLOW_ROW_LOCKS` to `OFF`. When `ALLOW_ROW_LOCKS` is `OFF`, rows are not locked and access to the specified indexes is obtained by using page-and table-level locks.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## Example: Disabling and Enabling an XML Index  
 By default, an XML index is enabled. If an XML index is disabled, the queries running against the XML column do not use the XML index. To enable an XML index, use `ALTER INDEX` with the `REBUILD` option.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## See Also  
 [XML Indexes (SQL Server)](../../Topics/TopicNameNotContainA/XML-Indexes--SQL-Server-.md)