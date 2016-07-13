---
title: getRowIdLifetime Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
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
# getRowIdLifetime Method (SQLServerDatabaseMetaData)
  Returns a status indicating whether or not SQL RowId data type is supported. If supported, it returns the lifetime for which a RowId object remains valid.  
  
## Syntax  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## Return Value  
 A RowIdLifetime object.  
  
> [!NOTE]  
>  In the JDBC Driver version 2.0 release, this method returns java.sql.RowIdLifetime.ROWID\_UNSUPPORTED value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getRowIdLifetime method is specified by the getRowIdLifetime method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  