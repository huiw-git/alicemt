---
title: prepareCall Method (java.lang.String, int, int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.prepareCall (java.lang.String, int, int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 04d36a25-7f95-4675-9690-4462671b3d67
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
# prepareCall Method (java.lang.String, int, int)
  Creates a [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) object that generates [SQLServerResultSet](../content/SQLServerResultSet-Class.md) objects with the given type and concurrency.  
  
## Syntax  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int resultSetType,  
                                              int resultSetConcurrency)  
```  
  
#### Parameters  
 *sql*  
  
 A **String** containing an SQL statement.  
  
 *resultSetType*  
  
 An **int** that indicates the result set type.  
  
 *resultSetConcurrency*  
  
 An **int** that indicates the result set concurrency type.  
  
## Return Value  
 A CallableStatement object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This prepareCall method is specified by the prepareCall method in the java.sql.Connection interface.  
  
## See Also  
 [prepareCall Method &#40;SQLServerConnection&#41;](../content/prepareCall-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  