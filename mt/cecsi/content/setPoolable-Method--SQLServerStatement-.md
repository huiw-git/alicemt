---
title: setPoolable Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
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
# setPoolable Method (SQLServerStatement)
  Requests that a statement be pooled or not pooled.  
  
## Syntax  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### Parameters  
 *poolable*  
  
 If **true**, requests that the statement be pooled. If **false**, requests that the statement not be pooled.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 The value specified in the *poolable* parameter is a hint to the statement pool implementation indicating if the application wants the statement to be pooled. The statement pool manager decides if it will use the hint.  
  
 A statement's pool value applies to both internal statement caches implemented by the driver and external statement caches implemented by application servers and other applications.  
  
 By default, a SQLServerStatement object is not poolable when created. SQLServerPreparedStatement and SQLServerCallableStatement objects are poolable when created.  
  
 [SQLServerException](../content/SQLServerException-Class.md) is thrown if this method is called on a closed statement.  
  
 [isPoolable](../content/isPoolable-Method--SQLServerStatement-.md) returns a value indicating if the object is poolable.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  