---
title: "isClosed Method (SQLServerConnection)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerConnection.isClosed
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: 9
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
# isClosed Method (SQLServerConnection)
  Indicates whether this [SQLServerConnection](../content/SQLServerConnection-Class.md) object has been closed.  
  
## Syntax  
  
```  
  
public boolean isClosed()  
```  
  
## Return Value  
 **true** if the connection is close, **false** if it is not.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isClosed method is specified by the isClosed method in the java.sql.Connection interface.  
  
 Verifies the state of the called SQLServerConnection object. A connection is closed if the [close](../content/close-Method--SQLServerConnection-.md) method has been called on it, or if certain fatal errors have occurred. This method will return **true** only when it is called after the close method has been called.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  