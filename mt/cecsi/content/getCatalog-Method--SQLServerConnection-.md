---
title: getCatalog Method (SQLServerConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.getCatalog
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: e87ef65f-4b5a-4e1c-8db5-7f0932390bb0
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
# getCatalog Method (SQLServerConnection)
  Retrieves the current catalog name of this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
## Syntax  
  
```  
  
public java.lang.String getCatalog()  
```  
  
## Return Value  
 A **String** that contains the catalog name.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getCatalog method is specified by the getCatalog method in the java.sql.Connection interface.  
  
 Returns the current catalog property of the SQLServerConnection object, or null if it is not set. The catalog property is set explicitly with the [setCatalog](../content/setCatalog-Method--SQLServerConnection-.md) method, or is implicitly updated by reading the environment change on TDS for the current catalog.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  