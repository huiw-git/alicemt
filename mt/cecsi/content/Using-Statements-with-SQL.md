---
title: Using Statements with SQL
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe28f48a-e1bc-48ff-a5e7-c24cd6e5ecc7
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
# Using Statements with SQL
  When you work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] and inline SQL statements, there are different classes that you can use. Which class you use depends on the type of SQL statement that you want to run.  
  
 If your SQL statement contains no IN parameters, use the [SQLServerStatement](../content/SQLServerStatement-Class.md) class, but if it does contain IN parameters, use the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) class.  
  
> [!NOTE]  
>  If you need to use SQL statements that contain both IN and OUT parameters, you must implement them as stored procedures and call them by using the [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) class. For more information about using stored procedures, see [Using Statements with Stored Procedures](../content/Using-Statements-with-Stored-Procedures.md).  
  
 The following sections describe the different scenarios for working with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using SQL statements.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Using an SQL Statement with No Parameters](../content/Using-an-SQL-Statement-with-No-Parameters.md)|Describes how to use SQL statements that contain no parameters.|  
|[Using an SQL Statement with Parameters](../content/Using-an-SQL-Statement-with-Parameters.md)|Describes how to use SQL statements that contain parameters.|  
|[Using an SQL Statement to Modify Database Objects](../content/Using-an-SQL-Statement-to-Modify-Database-Objects.md)|Describes how to use SQL statements to modify database objects.|  
|[Using an SQL Statement to Modify Data](../content/Using-an-SQL-Statement-to-Modify-Data.md)|Describes how to use SQL statements to modify data in a database.|  
  
## See Also  
 [Using Statements with the JDBC Driver](../content/Using-Statements-with-the-JDBC-Driver.md)  
  
  