---
title: getSQLStateType Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getSQLStateType
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
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
# getSQLStateType Method (SQLServerDatabaseMetaData)
  Indicates whether the SQLSTATE that is returned by the SQLException.getSQLState method is X\/Open \(now known as Open Group\) SQL CLI, SQL99 \(JDBC 3.0\), or SQL:2003 \(JDBC 4.0\).  
  
## Syntax  
  
```  
  
public int getSQLStateType()  
```  
  
## Return Value  
 An **int** that indicates the type of SQLSTATE, which can be one of the following values:  
  
-   For Java Runtime Environment version 5.0: If the **xopenStates** connection property is set to **true**, this method returns DatabaseMetaData.sqlStateXOpen. Otherwise, DatabaseMetaData.sqlStateSQL99.  
  
-   For Java Runtime Environment version 6.0: If the **xopenStates** connection property is set to **true**, this method returns DatabaseMetaData.sqlStateXOpen. Otherwise, DatabaseMetaData.sqlStateSQL.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getSQLStateType method is specified by the getSQLStateType method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  