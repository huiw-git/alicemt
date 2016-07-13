---
title: Handling Errors
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
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
# Handling Errors
  When using the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], all database error conditions are returned to your Java application as exceptions using the [SQLServerException](../content/SQLServerException-Class.md) class. The following methods of the SQLServerException class are inherited from java.sql.SQLException and java.lang.Throwable; and they can be used to return specific information about the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] error that has occurred:  
  
-   getSQLState returns the standard X\/Open or SQL99 state code of the exception.  
  
-   getErrorCode returns the specific database error number.  
  
-   getMessage returns the full text of the exception. The error message text describes the problem, and frequently includes placeholders for information, such as object names, that are inserted in the error message when it is displayed.  
  
-   getNextException returns the next SQLServerException object or null if there are no more exception objects to return.  
  
 In the following example, an open connection to the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)][!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database is passed in to the function and a malformed SQL statement is constructed that does not have a FROM clause. Then, the statement is run and an SQL exception is processed.  
  
 [!CODE [JDBC#HandlingErrors1](../CodeSnippet/SQLDrivers/jdbc#handlingerrors1)]  
  
## See Also  
 [Diagnosing Problems with the JDBC Driver](../content/Diagnosing-Problems-with-the-JDBC-Driver.md)  
  
  