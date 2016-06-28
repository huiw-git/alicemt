---
title: supportsDataManipulationTransactionsOnly Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.supportsDataManipulationTransactionsOnly
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: bdc182db-4518-4bf2-b63a-05f58fdb4eb8
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
# supportsDataManipulationTransactionsOnly Method (SQLServerDatabaseMetaData)
  Retrieves whether this database supports only data manipulation statements within a transaction.  
  
## Syntax  
  
```  
  
public boolean supportsDataManipulationTransactionsOnly()  
```  
  
## Return Value  
 **true** if supported. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This supportsDataManipulationTransactionsOnly method is specified by the supportsDataManipulationTransactionsOnly method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  