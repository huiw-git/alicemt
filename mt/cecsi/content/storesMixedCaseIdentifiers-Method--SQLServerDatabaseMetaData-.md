---
title: storesMixedCaseIdentifiers Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.storesMixedCaseIdentifiers
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: a91e5cd6-22b1-464e-aeec-665590737a74
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
# storesMixedCaseIdentifiers Method (SQLServerDatabaseMetaData)
  Retrieves whether this database treats mixed\-case SQL identifiers that are not enclosed in quotation marks as case\-insensitive and stores them in mixed case.  
  
## Syntax  
  
```  
  
public boolean storesMixedCaseIdentifiers()  
```  
  
## Return Value  
 **true** if the identifiers are stored in mixed case. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This storesMixedCaseIdentifiers method is specified by the storesMixedCaseIdentifiers method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  