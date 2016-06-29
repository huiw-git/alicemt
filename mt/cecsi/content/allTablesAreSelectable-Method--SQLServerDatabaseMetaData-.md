---
title: allTablesAreSelectable Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.allTablesAreSelectable
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: eb340450-45a7-49c8-84bc-1b9dd5ee842f
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
# allTablesAreSelectable Method (SQLServerDatabaseMetaData)
  Retrieves whether the current user has permissions to use all the tables that are returned by the [getTables](../content/getTables-Method--SQLServerDatabaseMetaData-.md) method in a SELECT statement.  
  
## Syntax  
  
```  
  
public boolean allTablesAreSelectable()  
```  
  
## Return Value  
 **true** if the user has permissions to call use all the tables. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This allTablesAreSelectable method is specified by the allTablesAreSelectable method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  