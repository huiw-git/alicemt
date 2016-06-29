---
title: Using a Stored Procedure with No Parameters
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
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
# Using a Stored Procedure with No Parameters
  The simplest kind of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] stored procedure that you can call is one that contains no parameters and returns a single result set. The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides the [SQLServerStatement](../content/SQLServerStatement-Class.md) class, which you can use to call this kind of stored procedure and process the data that it returns.  
  
 When you use the JDBC driver to call a stored procedure without parameters, you must use the `call` SQL escape sequence. The syntax for the `call` escape sequence with no parameters is as follows:  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  For more information about the SQL escape sequences, see [Using SQL Escape Sequences](../content/Using-SQL-Escape-Sequences.md).  
  
 As an example, create the following stored procedure in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database:  
  
```  
CREATE PROCEDURE GetContactFormalNames   
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName   
   FROM Person.Contact  
END  
```  
  
 This stored procedure returns a single result set that contains one column of data, which is a combination of the title, first name, and last name of the top ten contacts that are in the Person.Contact table.  
  
 In the following example, an open connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function, and the [executeQuery](../content/executeQuery-Method--SQLServerStatement-.md) method is used to call the GetContactFormalNames stored procedure.  
  
```  
public static void executeSprocNoParams(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
  
      while (rs.next()) {  
         System.out.println(rs.getString("FormalName"));  
      }  
      rs.close();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## See Also  
 [Using Statements with Stored Procedures](../content/Using-Statements-with-Stored-Procedures.md)  
  
  