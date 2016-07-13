---
title: dataDefinitionCausesTransactionCommit Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.dataDefinitionCausesTransactionCommit
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: bf04fa73-b9f1-4403-b6a0-e53d0d27c671
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
# dataDefinitionCausesTransactionCommit Method (SQLServerDatabaseMetaData)
  Retrieves whether a data definition statement within a transaction forces the transaction to commit.  
  
## Syntax  
  
```  
  
public boolean dataDefinitionCausesTransactionCommit()  
```  
  
## Return Value  
 **true** if the DDL statement forces a commit. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This dataDefinitionCausesTransactionCommit method is specified by the dataDefinitionCausesTransactionCommit method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  