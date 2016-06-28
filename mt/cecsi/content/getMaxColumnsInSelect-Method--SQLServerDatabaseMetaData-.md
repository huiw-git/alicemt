---
title: getMaxColumnsInSelect Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getMaxColumnsInSelect
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 43c428df-ef91-4f55-81c3-49a4db3379cc
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
# getMaxColumnsInSelect Method (SQLServerDatabaseMetaData)
  Retrieves the maximum number of columns that this database allows in a SELECT list.  
  
## Syntax  
  
```  
  
public int getMaxColumnsInSelect()  
```  
  
## Return Value  
 An **int** that indicates the maximum number of columns allowed.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getMaxColumnsInSelect method is specified by the getMaxColumnsInSelect method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  