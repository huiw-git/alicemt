---
title: getAutoCommit Method (SQLServerConnection)
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
  - SQLServerConnection.getAutoCommit
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: af1f67f4-f568-4e58-abcc-5c809a89b547
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
# getAutoCommit Method (SQLServerConnection)
  Retrieves the current auto\-commit mode for this [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
## Syntax  
  
```  
  
public boolean getAutoCommit()  
```  
  
## Return Value  
 **true** if auto\-commit mode is enabled, **false** if it is not.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getAutoCommit method is specified by the getAutoCommit method in the java.sql.Connection interface.  
  
## See Also  
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  