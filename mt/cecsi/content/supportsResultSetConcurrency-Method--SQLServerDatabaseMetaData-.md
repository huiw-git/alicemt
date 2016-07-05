---
title: supportsResultSetConcurrency Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.supportsResultSetConcurrency
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8f7573b2-ac5c-4721-8a02-4b6cb60c74b2
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
# supportsResultSetConcurrency Method (SQLServerDatabaseMetaData)
  Retrieves whether this database supports the given concurrency type in combination with the given result set type.  
  
## Syntax  
  
```  
  
public boolean supportsResultSetConcurrency(int type,  
                                            int concurrency)  
```  
  
#### Parameters  
 *type*  
  
 An **int** that indicates the result set type, which can be one of the following values as defined in java.sql.ResultSet or SQLServerResultSet:  
  
## java.sql.ResultSet Types  
 TYPE\_FORWARD\_ONLY  
  
 TYPE\_SCROLL\_SENSITIVE  
  
 TYPE\_SCROLL\_INSENSITIVE  
  
## SQLServerResultSet Types  
 TYPE\_SS\_SCROLL\_STATIC  
  
 TYPE\_SS\_SCROLL\_KEYSET  
  
 TYPE\_SS\_DIRECT\_FORWARD\_ONLY  
  
 TYPE\_SS\_SERVER\_CURSOR\_FORWARD\_ONLY  
  
 TYPE\_SS\_SCROLL\_DYNAMIC  
  
 *concurrency*  
  
 An **int** that indicates the result set concurrency level, which can be one of the following values as defined in java.sql.ResultSet or SQLServerResultSet:  
  
## java.sql.ResultSet Types  
 CONCUR\_READ\_ONLY  
  
 CONCUR\_UPDATABLE  
  
## SQLServerResultSet Types  
 CONCUR\_SS\_OPTIMISTIC\_CC  
  
 CONCUR\_SS\_SCROLL\_LOCKS  
  
 CONCUR\_SS\_OPTIMISTIC\_VAL  
  
## Return Value  
 **true** if supported. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This supportsResultSetConcurrency method is specified by the supportsResultSetConcurrency method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  