---
title: getWarnings Method (SQLServerConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.getWarnings
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 15af39bf-6285-44cc-a021-7341e7a055c4
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
# getWarnings Method (SQLServerConnection)
  Retrieves the first warning reported by calls on this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
## Syntax  
  
```  
  
public java.sql.SQLWarning getWarnings()  
```  
  
## Return Value  
 A SQLWarning object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getWarnings method is specified by the getWarnings method in the java.sql.Connection interface.  
  
 Subsequent warnings are chained to the first SQLWarning and called with the getNextWarning method. If called on a closed connection, an exception will be thrown.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  