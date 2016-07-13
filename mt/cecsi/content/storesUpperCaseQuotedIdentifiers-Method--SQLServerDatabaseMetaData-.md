---
title: storesUpperCaseQuotedIdentifiers Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.storesUpperCaseQuotedIdentifiers
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 936ec140-2597-44e6-82d3-3994a676ee35
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
# storesUpperCaseQuotedIdentifiers Method (SQLServerDatabaseMetaData)
  Retrieves whether this database treats mixed\-case SQL identifiers that are enclosed in quotation marks as case\-insensitive and stores them in uppercase.  
  
## Syntax  
  
```  
  
public boolean storesUpperCaseQuotedIdentifiers()  
```  
  
## Return Value  
 **true** if the identifiers are stored in uppercase. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This storesUpperCaseQuotedIdentifiers method is specified by the storesUpperCaseQuotedIdentifiers method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  