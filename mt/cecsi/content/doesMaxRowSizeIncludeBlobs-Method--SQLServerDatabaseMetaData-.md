---
title: doesMaxRowSizeIncludeBlobs Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.doesMaxRowSizeIncludeBlobs
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 0c90a7a7-5a59-4858-bb26-3e725d8611d7
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
# doesMaxRowSizeIncludeBlobs Method (SQLServerDatabaseMetaData)
  Retrieves whether the return value for the [getMaxRowSize](../content/getMaxRowSize-Method--SQLServerDatabaseMetaData-.md) method includes the SQL data types LONGVARCHAR and LONGVARBINARY.  
  
## Syntax  
  
```  
  
public boolean doesMaxRowSizeIncludeBlobs()  
```  
  
## Return Value  
 **true** if the return value includes the data types. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This doesMoxRowSizeIncludeBlobs method is specified by the doesMoxRowSizeIncludeBlobs method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  