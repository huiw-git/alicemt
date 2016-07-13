---
title: storesUpperCaseIdentifiers Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.storesUpperCaseIdentifiers
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: a622b748-d10b-4f02-afe3-fba4a5bca17b
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
# storesUpperCaseIdentifiers Method (SQLServerDatabaseMetaData)
  Retrieves whether this database treats mixed\-case SQL identifiers that are not enclosed in quotation marks as case\-insensitive and stores them in uppercase.  
  
## Syntax  
  
```  
  
public boolean storesUpperCaseIdentifiers()  
```  
  
## Return Value  
 **true** if the identifiers are stored in uppercase. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This storesUpperCaseIdentifiers method is specified by the storesUpperCaseIdentifiers method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  