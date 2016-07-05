---
title: isReadOnly Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.isReadOnly
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d1569e03-b7bd-486a-af0b-d3f108f712dc
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
# isReadOnly Method (SQLServerDatabaseMetaData)
  Retrieves whether this database is in read\-only mode.  
  
## Syntax  
  
```  
  
public boolean isReadOnly()  
```  
  
## Return Value  
 **true** if the database is in read\-only mode. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isReadOnly method is specified by the isReadOnly method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  