---
title: "Create, Alter, and Drop Secondary Selective XML Indexes"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Create, Alter, and Drop Secondary Selective XML Indexes
Describes how to create a new secondary selective XML index, or alter or drop an existing secondary selective XML index.  
  
##  <a name="create"></a> Creating a Secondary Selective XML Index  
  
### How to: Create a Secondary Selective XML Index  
 **Create a Secondary Selective XML Index by Using Transact-SQL**  
 Create a secondary selective XML index by calling the CREATE XML INDEX statement. For more information, see [CREATE XML INDEX (Selective XML Indexes) (SQL Database)](assetId:///1f510151-41d5-45c2-9cd0-b1ca0246fffe).  
  
 **Example**  
  
 The following example creates a secondary selective XML index on the path `'pathabc'`. The path to index is identified by the name that was given to it when it was created with the CREATE SELECTIVE XML INDEX statement. For more information, see [CREATE SELECTIVE XML INDEX (SQL Database)](assetId:///1d769f62-f646-4057-b93a-bf5f90e935ed).  
  
```tsql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
 [&#91;TOP&#93;](#top)  
  
##  <a name="alter"></a> Altering a Secondary Selective XML Index  
 The ALTER statement is not supported for secondary selective XML indexes. To change a secondary selective XML index, drop the existing index and recreate it.  
  
### How to: Alter a Secondary Selective XML Index  
 **Alter a Secondary Selective XML Index by Using Transact-SQL**  
 1.  Drop the existing secondary selective XML index by calling the DROP INDEX statement. For more information, see [DROP INDEX (Selective XML Indexes) (SQL Database)](assetId:///4779ae84-e5f4-4d04-8fc1-e24a6631b428).  
  
2.  Recreate the index with the desired options by calling the CREATE XML INDEX statement. For more information, see [CREATE XML INDEX (Selective XML Indexes) (SQL Database)](assetId:///1f510151-41d5-45c2-9cd0-b1ca0246fffe).  
  
 **Example**  
  
 The following example changes a secondary selective XML index by dropping it and recreating it.  
  
```tsql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
 [&#91;TOP&#93;](#top)  
  
##  <a name="drop"></a> Dropping a Secondary Selective XML Index  
  
### How to: Drop a Secondary Selective XML Index  
 **Drop a Secondary Selective XML Index by Using Transact-SQL**  
 Drop a secondary selective XML index by calling the DROP INDEX statement. For more information, see [DROP INDEX (Selective XML Indexes) (SQL Database)](assetId:///4779ae84-e5f4-4d04-8fc1-e24a6631b428).  
  
 **Example**  
  
 The following example shows a DROP INDEX statement.  
  
```tsql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
 [&#91;TOP&#93;](#top)  
  
## See Also  
 [Selective XML Indexes (SXI)](../../Topics/TopicNameNotContainA/Selective-XML-Indexes--SXI-.md)