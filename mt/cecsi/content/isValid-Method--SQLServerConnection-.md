---
title: "isValid Method (SQLServerConnection)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
caps.latest.revision: 15
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
# isValid Method (SQLServerConnection)
  Indicates whether this [SQLServerConnection](../content/SQLServerConnection-Class.md) object has not been closed and is still valid.  
  
## Syntax  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### Parameters  
 *timeout*  
  
 An **int** that specifies the number of seconds to wait for validating the connection.  
  
## Return Value  
 **true** if the connection is valid; **false** if the connection is not valid or the validity of the connection cannot be determined before the timeout expires.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isValid method is specified by the isValid method in the java.sql.Connection interface.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  