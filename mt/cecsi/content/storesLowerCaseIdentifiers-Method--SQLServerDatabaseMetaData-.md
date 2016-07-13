---
title: storesLowerCaseIdentifiers Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.storesLowerCaseIdentifiers
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b7dd60f5-c4f3-4b14-9a33-d95327395083
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
# storesLowerCaseIdentifiers Method (SQLServerDatabaseMetaData)
  Retrieves whether this database treats mixed\-case SQL identifiers that are not enclosed in quotation marks as case\-insensitive and stores them in lowercase.  
  
## Syntax  
  
```  
  
public boolean storesLowerCaseIdentifiers()  
```  
  
## Return Value  
 **true** if the identifiers are stored in lowercase. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This storesLowerCaseIdentifiers method is specified by the storesLowerCaseIdentifiers method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  