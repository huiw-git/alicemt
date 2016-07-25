---
title: "getGeneratedKeys Method (SQLServerStatement)"
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
  - SQLServerStatement.getGeneratedKeys
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
caps.latest.revision: 12
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
# getGeneratedKeys Method (SQLServerStatement)
  Retrieves any auto-generated keys that are created as a result of running this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.  
  
## Syntax  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## Return Value  
 A ResultSet object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getGeneratedKeys method is specified by the getGeneratedKeys method in the java.sql.Statement interface.  
  
 For more information about how to use this method, see [Using Auto Generated Keys](../content/Using-Auto-Generated-Keys.md).  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  