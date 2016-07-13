---
title: getWarnings Method (SQLServerStatement)
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
  - SQLServerStatement.getWarnings
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 3d6decae-2570-4ca5-8ff6-57a2cc3e921f
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
# getWarnings Method (SQLServerStatement)
  Retrieves the first warning that is reported by calls on this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.  
  
## Syntax  
  
```  
  
public final java.sql.SQLWarning getWarnings()  
```  
  
## Return Value  
 An SQLWarning object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getWarnings method is specified by the getWarnings method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  