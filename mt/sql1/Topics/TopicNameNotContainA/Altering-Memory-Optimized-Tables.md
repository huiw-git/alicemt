---
title: "Altering Memory-Optimized Tables"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-28
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine-imoltp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 690b70b7-5be1-4014-af97-54e531997839
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# Altering Memory-Optimized Tables
Schema and index changes on memory-optimized tables can be performed by using the ALTER TABLE statement. The database application can continue to run, and any operation that is accessing the table is blocked until the alteration process is completed.  
  
## ALTER TABLE  
 The ALTER TABLE syntax is used for making changes to the table schema, as well as for adding, deleting, and rebuilding indexes. Indexes are considered part of the table definition:  
  
-   The syntax ALTER TABLE … ADD/DROP/ALTER INDEX is supported only for memory-optimized tables.  
  
-   Without using an ALTER TABLE statement, the statements CREATE INDEX and DROP INDEX and ALTER INDEX are *not* supported for indexes on memory-optimized tables.  
  
 The following is the syntax for the ADD and DROP and ALTER INDEX clauses on the ALTER TABLE statement.  
  
```  
| ADD   
     {   
        <column_definition>  
      | <table_constraint>  
      | <table_index>    
     } [ ,...n ]  
  
| DROP   
     {  
         [ CONSTRAINT ]   
         {   
              constraint_name   
         } [ ,...n ]  
         | COLUMN   
         {  
              column_name   
         } [ ,...n ]  
         | INDEX   
         {  
              index_name   
         } [ ,...n ]  
     } [ ,...n ]  
  
| ALTER INDEX index_name  
     {   
         REBUILD WITH ( <rebuild_index_option> )     
     }  
}  
  
```  
  
 The following types of alterations are supported.  
  
-   Changing the bucket count  
  
-   Adding and removing an index  
  
-   Changing, adding and removing a column  
  
-   Adding and removing a constraint  
  
 For more information on ALTER TABLE functionality and the complete syntax, see [ALTER TABLE (Transact-SQL)](assetId:///f1745145-182d-4301-a334-18f799d361d1)  
  
## Schema-bound Dependency  
 Natively compiled stored procedures always have a schema-bound dependency on the memory optimized tables they access. A schema-bound dependency is a relationship between two entities that prevents the referenced entity from being dropped or incompatibly modified as long as the referencing entity exists.  
  
 For example, if a natively compiled stored procedure is foolish enough to use the syntax `SELECT * FROM mytable;`, then dropping any column from *mytable* would be an incompatible modification.  
  
## Examples  
 The following example alters the bucket count of an existing hash index. This rebuilds the hash index with the new bucket count while other properties of the hash index remain the same.  
  
```  
ALTER TABLE Sales.SalesOrderDetail_inmem   
       ALTER INDEX imPK_SalesOrderDetail_SalesOrderID_SalesOrderDetailID  
              REBUILD WITH (BUCKET_COUNT=67108864);  
GO  
  
```  
  
 The following example adds a column with a NOT NULL constraint and with a DEFAULT definition, and uses WITH VALUES to provide values for each existing row in the table. If WITH VALUES is not used, each row has the value NULL in the new column.  
  
```  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD Comment NVARCHAR(100) NOT NULL DEFAULT N'' WITH VALUES;  
GO  
  
```  
  
 The following example adds a primary key constraint to an existing column.  
  
```  
CREATE TABLE dbo.UserSession (   
   SessionId int not null,   
   UserId int not null,   
   CreatedDate datetime2 not null,   
   ShoppingCartId int,   
   index ix_UserId nonclustered hash (UserId) with (bucket_count=400000)   
)   
WITH (MEMORY_OPTIMIZED=ON, DURABILITY=SCHEMA_ONLY) ;  
GO  
  
ALTER TABLE dbo.UserSession  
       ADD CONSTRAINT PK_UserSession PRIMARY KEY NONCLUSTERED (SessionId);  
GO  
  
```  
  
 The following example removes an index.  
  
```  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       DROP INDEX ix_ModifiedDate;  
GO  
  
```  
  
 The following example adds an index.  
  
```  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD INDEX ix_ModifiedDate (ModifiedDate);  
GO  
  
```  
  
 The following example adds multiple columns, with an index and constraints.  
  
```  
ALTER TABLE Sales.SalesOrderDetail_inmem  
       ADD    CustomerID int NOT NULL DEFAULT -1 WITH VALUES,  
              ShipMethodID int NOT NULL DEFAULT -1 WITH VALUES,  
              INDEX ix_Customer (CustomerID);  
GO  
  
```  
  
## See Also  
 [Memory-Optimized Tables](../../Topics/TopicNameNotContainA/Memory-Optimized-Tables.md)