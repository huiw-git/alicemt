---
title: locatorsUpdateCopy Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.locatorsUpdateCopy
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f6ec8c1d-7ff8-4bc5-8bd3-0199a9294a6e
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
# locatorsUpdateCopy Method (SQLServerDatabaseMetaData)
  Indicates whether updates made to a LOB are made on a copy or directly to the LOB.  
  
## Syntax  
  
```  
  
public boolean locatorsUpdateCopy()  
```  
  
## Return Value  
 **true** if updates are made to a copy. **false** if updates are made directly.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This locatorsUpdateCopy method is specified by the locatorsUpdateCopy method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  