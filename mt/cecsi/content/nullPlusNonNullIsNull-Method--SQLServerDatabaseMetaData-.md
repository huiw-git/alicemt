---
title: nullPlusNonNullIsNull Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.nullPlusNonNullIsNull
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: c594736f-3a9b-463f-bbd8-eaf9221230ea
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
# nullPlusNonNullIsNull Method (SQLServerDatabaseMetaData)
  Indicates whether this database supports concatenations between NULL and non\-NULL values being NULL.  
  
## Syntax  
  
```  
  
public boolean nullPlusNonNullIsNull()  
```  
  
## Return Value  
 **true** if the concatenations are supported. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This nullPlusNonNullIsNull method is specified by the nullPlusNonNullIsNull method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  