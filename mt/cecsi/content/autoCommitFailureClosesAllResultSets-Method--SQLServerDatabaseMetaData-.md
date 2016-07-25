---
title: "autoCommitFailureClosesAllResultSets Method (SQLServerDatabaseMetaData)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
caps.latest.revision: 14
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
# autoCommitFailureClosesAllResultSets Method (SQLServerDatabaseMetaData)
  Indicates whether the JDBC driver closes all the open result sets, including the holdable ones, when an auto-commit is enabled and an exception is raised.  
  
## Syntax  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## Return Value  
 **true** if all the open result sets, including the holdable ones, are closed when an auto-commit is enabled and an exception is raised. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This autoCommitFailureClosesAllResultSets method is specified by the autoCommitFailureClosesAllResultSets method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  