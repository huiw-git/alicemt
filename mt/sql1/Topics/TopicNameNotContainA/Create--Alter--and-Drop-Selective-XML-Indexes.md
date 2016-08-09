---
title: "Create, Alter, and Drop Selective XML Indexes"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Create, Alter, and Drop Selective XML Indexes
Describes how to create a new selective XML index, or alter or drop an existing selective XML index.  
  
 For more information about selective XML indexes, see [Selective XML Indexes (SXI)](../../Topics/TopicNameNotContainA/Selective-XML-Indexes--SXI-.md).  
  
##  <a name="create"></a> Creating a Selective XML Index  
  
### How to: Create a Selective XML Index  
 **Create a Selective XML Index by Using Transact-SQL**  
 Create a selective XML index by calling the CREATE SELECTIVE XML INDEX statement. For more information, see [CREATE SELECTIVE XML INDEX (SQL Database)](assetId:///1d769f62-f646-4057-b93a-bf5f90e935ed).  
  
 **Example**  
  
 The following example shows the syntax for creating a selective XML index. It also shows several variations of the syntax for describing the paths to be indexed, with optional optimization hints.  
  
```tsql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
 [&#91;TOP&#93;](#top)  
  
##  <a name="alter"></a> Altering a Selective XML Index  
  
### How to: Alter a Selective XML Index  
 **Alter a Selective XML Index by Using Transact-SQL**  
 Alter an existing selective XML index by calling the ALTER INDEX statement. For more information, see [ALTER INDEX (Selective XML Indexes) (SQL Database)](assetId:///cca96a8f-7737-42d2-bbcc-03d5f858dcc1).  
  
 **Example**  
  
 The following example shows an ALTER INDEX statement. This statement adds the path `'/a/b/m'` to the XQuery part of the index and deletes the path `'/a/b/e'` from the SQL part of the index created in the example in the topic [CREATE SELECTIVE XML INDEX (SQL Database)](assetId:///1d769f62-f646-4057-b93a-bf5f90e935ed). The path to delete is identified by the name that was given to it when it was created.  
  
```tsql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
 [&#91;TOP&#93;](#top)  
  
##  <a name="drop"></a> Dropping a Selective XML Index  
  
### How to: Drop a Selective XML Index  
 **Drop a Selective XML Index by Using Transact-SQL**  
 Drop a selective XML index by calling the DROP INDEX statement. For more information, see [DROP INDEX (Selective XML Indexes) (SQL Database)](assetId:///4779ae84-e5f4-4d04-8fc1-e24a6631b428).  
  
 **Example**  
  
 The following example shows a DROP INDEX statement.  
  
```tsql  
DROP INDEX sxi_index ON tbl  
```  
  
 [&#91;TOP&#93;](#top)