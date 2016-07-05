---
title: storesMixedCaseQuotedIdentifiers Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.storesMixedCaseQuotedIdentifiers
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 1ffa599c-d0c8-43b6-8e9b-7c856a846630
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
# storesMixedCaseQuotedIdentifiers Method (SQLServerDatabaseMetaData)
  Retrieves whether this database treats mixed\-case SQL identifiers that are enclosed in quotation marks as case\-insensitive and stores them in mixed case.  
  
## Syntax  
  
```  
  
public boolean storesMixedCaseQuotedIdentifiers()  
```  
  
## Return Value  
 **true** if the identifiers are stored in mixed case. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This storesMixedCaseQuotedIdentifiers method is specified by the storesMixedCaseQuotedIdentifiers method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  