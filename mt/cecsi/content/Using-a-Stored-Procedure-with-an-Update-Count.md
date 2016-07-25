---
title: "Using a Stored Procedure with an Update Count"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
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
# Using a Stored Procedure with an Update Count
  To modify data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using a stored procedure, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides the [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) class. By using the SQLServerCallableStatement class, you can call stored procedures that modify data that is contained in the database and return a count of the number of rows affected, also referred to as the update count.  
  
 After you have set up the call to the stored procedure by using the SQLServerCallableStatement class, you can then call the stored procedure by using either the [execute](../content/execute-Method--SQLServerStatement-.md) or the [executeUpdate](../content/executeUpdate-Method--SQLServerStatement-.md) method. The executeUpdate method will return an **int** value that contains the number of rows affected by the stored procedure, but the execute method does not. If you use the execute method and want to get the count of the number of rows affected, you can call the [getUpdateCount](../content/getUpdateCount-Method--SQLServerStatement-.md) method after you run the stored procedure.  
  
> [!NOTE]  
>  If you want the JDBC driver to return all update counts, including update counts returned by any triggers that may have fired, set the lastUpdateCount connection string property to "false". For more information about the lastUpdateCount property, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
 As an example, create the following table and stored procedure, and also insert sample data in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
  
CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, the execute method is used to call the UpdateTestTable stored procedure, and then the getUpdateCount method is used to return a count of the rows that are affected by the stored procedure.  
  
 [!CODE [JDBC#UsingSprocWithUpdateCount1](../CodeSnippet/SQLDrivers/jdbc#usingsprocwithupdatecount1)]  
  
## See Also  
 [Using Statements with Stored Procedures](../content/Using-Statements-with-Stored-Procedures.md)  
  
  