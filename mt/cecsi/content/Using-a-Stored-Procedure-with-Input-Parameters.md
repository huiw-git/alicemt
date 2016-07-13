---
title: Using a Stored Procedure with Input Parameters
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
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
# Using a Stored Procedure with Input Parameters
  A [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] stored procedure that you can call is one that contains one or more IN parameters, which are parameters that can be used to pass data into the stored procedure. The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) class, which you can use to call this kind of stored procedure and to process the data that it returns.  
  
 When you use the JDBC driver to call a stored procedure with IN parameters, you must use the `call` SQL escape sequence together with the [prepareCall](../content/prepareCall-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class. The syntax for the `call` escape sequence with IN parameters is as follows:  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  For more information about the SQL escape sequences, see [Using SQL Escape Sequences](../content/Using-SQL-Escape-Sequences.md).  
  
 When you construct the `call` escape sequence, specify the IN parameters by using the ? \(question mark\) character. This character acts as a placeholder for the parameter values that will be passed into the stored procedure. To specify a value for a parameter, you can use one of the setter methods of the SQLServerPreparedStatement class. The setter method that you can use is determined by the data type of the IN parameter.  
  
 When you pass a value to the setter method, you must specify not only the actual value that will be used in the parameter, but also the ordinal placement of the parameter in the stored procedure. For example, if your stored procedure contains a single IN parameter, its ordinal value will be 1. If the stored procedure contains two parameters, the first ordinal value will be 1, and the second ordinal value will be 2.  
  
 As an example of how to call a stored procedure that contains an IN parameter, use the uspGetEmployeeManagers stored procedure in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database. This stored procedure accepts a single input parameter named EmployeeID, which is an integer value, and it returns a recursive list of employees and their managers based on the specified EmployeeID. The Java code for calling this stored procedure is as follows:  
  
```  
public static void executeSprocInParams(Connection con) {  
   try {  
      PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}");  
      pstmt.setInt(1, 50);  
      ResultSet rs = pstmt.executeQuery();  
  
      while (rs.next()) {  
         System.out.println("EMPLOYEE:");  
         System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
         System.out.println("MANAGER:");  
         System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
         System.out.println();  
      }  
      rs.close();  
      pstmt.close();  
   }  
  
   catch (Exception e) {  
      e.printStackTrace();  
    }  
}  
```  
  
## See Also  
 [Using Statements with Stored Procedures](../content/Using-Statements-with-Stored-Procedures.md)  
  
  