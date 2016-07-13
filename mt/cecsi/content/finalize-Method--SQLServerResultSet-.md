---
title: finalize Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.finalize
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
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
# finalize Method (SQLServerResultSet)
  Explicitly closes this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public void finalize()  
```  
  
## Remarks  
 Closes the result set if the application does not. This method exists only to conform to the JDBC specification. Because the Java Virtual Machine \(JVM\) does not guarantee when a finalizer will have a chance to run, applications that neglect to explicitly close their result sets could still deadlock on another statement that is using the same connection and is blocked on a common server resource, such as row locks.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  