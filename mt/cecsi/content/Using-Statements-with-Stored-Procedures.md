---
title: Using Statements with Stored Procedures
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0041f9e1-09b6-4487-b052-afd636c8e89a
manager:jhubbard
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
# Using Statements with Stored Procedures
  A stored procedure is a database procedure, similar to a procedure in other programming languages, which is contained within the database itself. In [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], stored procedures can be created by using [!INCLUDE[tsql](../content/includes/tsql_md.md)], or by using the common language runtime \(CLR\) and one of the Visual Studio programming languages such as Visual Basic or C\#. Generally, [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] stored procedures can do the following:  
  
-   Accept input parameters and return multiple values in the form of output parameters to the calling procedure or batch.  
  
-   Contain programming statements that perform operations in the database, including calling other procedures.  
  
-   Return a status value to a calling procedure or batch to indicate success or failure \(and the reason for failure\).  
  
> [!NOTE]  
>  For more information about [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] stored procedures, see "Understanding Stored Procedures" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
 To work with data in a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using a stored procedure, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides the [SQLServerStatement](../content/SQLServerStatement-Class.md), [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md), and [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) classes. Which class you use depends on whether IN \(input\) or OUT \(output\) parameters are required by the stored procedure. If the stored procedure requires no IN or OUT parameters, you can use the SQLServerStatement class; if the stored procedure will be called multiple times, or requires only IN parameters, you can use the SQLServerPreparedStatement class. If the stored procedure requires both IN and OUT parameters, you should use the SQLServerCallableStatement class. It is only when the stored procedure requires OUT parameters that you will need the overhead of using the SQLServerCallableStatement class.  
  
> [!NOTE]  
>  Stored procedures can also return update counts and multiple result sets. For more information, see [Using a Stored Procedure with an Update Count](../content/Using-a-Stored-Procedure-with-an-Update-Count.md) and [Using Multiple Result Sets](../content/Using-Multiple-Result-Sets.md).  
  
 When you use the JDBC driver to call a stored procedure with parameters, you must use the `call` SQL escape sequence together with the [prepareCall](../content/prepareCall-Method--SQLServerConnection-.md) method of the [SQLServerConnection](../content/SQLServerConnection-Class.md) class. The complete syntax for the `call` escape sequence is as follows:  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  For more information about the `call` and other SQL escape sequences, see [Using SQL Escape Sequences](../content/Using-SQL-Escape-Sequences.md).  
  
 The topics in this section describe the ways that you can call [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] stored procedures by using the JDBC driver and the `call` SQL escape sequence.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Using a Stored Procedure with No Parameters](../content/Using-a-Stored-Procedure-with-No-Parameters.md)|Describes how to use the JDBC driver to run stored procedures that contain no input or output parameters.|  
|[Using a Stored Procedure with Input Parameters](../content/Using-a-Stored-Procedure-with-Input-Parameters.md)|Describes how to use the JDBC driver to run stored procedures that contain input parameters.|  
|[Using a Stored Procedure with Output Parameters](../content/Using-a-Stored-Procedure-with-Output-Parameters.md)|Describes how to use the JDBC driver to run stored procedures that contain output parameters.|  
|[Using a Stored Procedure with a Return Status](../content/Using-a-Stored-Procedure-with-a-Return-Status.md)|Describes how to use the JDBC driver to run stored procedures that contain return status values.|  
|[Using a Stored Procedure with an Update Count](../content/Using-a-Stored-Procedure-with-an-Update-Count.md)|Describes how to use the JDBC driver to run stored procedures that return update counts.|  
  
## See Also  
 [Using Statements with the JDBC Driver](../content/Using-Statements-with-the-JDBC-Driver.md)  
  
  