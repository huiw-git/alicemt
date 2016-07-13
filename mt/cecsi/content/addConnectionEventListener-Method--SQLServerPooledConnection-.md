---
title: addConnectionEventListener Method (SQLServerPooledConnection)
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
  - SQLServerPooledConnection.addConnectionEventListener
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
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
# addConnectionEventListener Method (SQLServerPooledConnection)
  Registers the given event listener so that it will be notified when an event occurs on this [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md) object.  
  
## Syntax  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### Parameters  
 *listener*  
  
 A ConnectionEventListener object.  
  
## Remarks  
 This addConnectionEventListener method is specified by the addConnectionEventListener method in the javax.sql.PooledConnection interface.  
  
## See Also  
 [SQLServerPooledConnection Methods](../content/SQLServerPooledConnection-Methods.md)   
 [SQLServerPooledConnection Members](../content/SQLServerPooledConnection-Members.md)   
 [SQLServerPooledConnection Class](../content/SQLServerPooledConnection-Class.md)  
  
  