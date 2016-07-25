---
title: "Performing Batch Operations"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a576d95-7da6-4b7b-8b32-59e5b4d354c4
caps.latest.revision: 22
manager: jhubbard
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# Performing Batch Operations
  To improve performance when multiple updates to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database are occurring, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides the ability to submit multiple updates as a single unit of work, also referred to as a batch.  
  
 The [SQLServerStatement](../content/SQLServerStatement-Class.md), [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md), and [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) classes can all be used to submit batch updates. The [addBatch](../content/addBatch-Method--SQLServerPreparedStatement-.md) method is used to add a command. The [clearBatch](../content/clearBatch-Method--SQLServerPreparedStatement-.md) method is used to clear the list of commands. The [executeBatch](../content/executeBatch-Method--SQLServerStatement-.md) method is used to submit all commands for processing. Only Data Definition Language (DDL) and Data Manipulation Language (DML) statements that return a simple update count can be run as part of a batch.  
  
 The executeBatch method returns an array of **int** values that correspond to the update count of each command. If one of the commands fails, a BatchUpdateException is thrown, and you should use the getUpdateCounts method of the BatchUpdateException class to retrieve the update count array. If a command fails, the driver continues processing the remaining commands. However, if a command has a syntax error, the statements in the batch fail.  
  
> [!NOTE]  
>  If you do not have to use update counts, you can first issue a SET NOCOUNT ON statement to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. This will reduce network traffic and additionally enhance the performance of your application.  
  
 As an example, create the following table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, the addBatch method is used to create the statements to be executed, and the executeBatch method is called to submit the batch to the database.  
  
```  
public static void executeBatchUpdate(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('X', 100)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Y', 200)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Z', 300)");  
      int[] updateCounts = stmt.executeBatch();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## See Also  
 [Using Statements with the JDBC Driver](../content/Using-Statements-with-the-JDBC-Driver.md)  
  
  