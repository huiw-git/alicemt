---
title: supportsOpenStatementsAcrossCommit Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.supportsOpenStatementsAcrossCommit
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: e733586c-9222-43cb-92ea-ba474f442a43
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
# supportsOpenStatementsAcrossCommit Method (SQLServerDatabaseMetaData)
  Retrieves whether this database supports keeping statements open across commits.  
  
## Syntax  
  
```  
  
public boolean supportsOpenStatementsAcrossCommit()  
```  
  
## Return Value  
 **true** if supported. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This supportsOpenStatementsAcrossCommit method is specified by the supportsOpenStatementsAcrossCommit method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  