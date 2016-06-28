---
title: getMetaData Method (SQLServerConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.getMetaData
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 86223cb5-3bf4-489a-8c82-669a91764f2b
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
# getMetaData Method (SQLServerConnection)
  Retrieves a [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) object that contains metadata about the database to which this [SQLServerConnection](../content/SQLServerConnection-Class.md) object represents a connection.  
  
## Syntax  
  
```  
  
public java.sql.DatabaseMetaData getMetaData()  
```  
  
## Return Value  
 The DatabaseMetaData object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getMetaData method is specified by the getMetaData method in the java.sql.Connection interface.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  