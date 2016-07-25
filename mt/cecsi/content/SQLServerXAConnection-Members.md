---
title: "SQLServerXAConnection Members"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
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
# SQLServerXAConnection Members
  The following tables list the members that are exposed by the [SQLServerXAConnection](../content/SQLServerXAConnection-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
 None.  
  
## Inherited Fields  
 None.  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[addConnectionEventListener](../content/addConnectionEventListener-Method--SQLServerPooledConnection-.md)|(Inherited from [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md)) Registers the given event listener so that it will be notified when an event occurs on this Connection object.|  
|[close](../content/close-Method--SQLServerPooledConnection-.md)|(Inherited from [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md)) Closes the physical connection that this Connection object represents.|  
|[getConnection](../content/getConnection-Method--SQLServerPooledConnection-.md)|(Inherited from [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md)) Creates an object handle for the physical connection that this Connection object represents.|  
|[getXAResource](../content/getXAResource-Method--SQLServerXAConnection-.md)|Retrieves a [SQLServerXAResource](../content/SQLServerXAResource-Class.md) object that the transaction manager will use to manage the participation of this [SQLServerXAConnection](../content/SQLServerXAConnection-Class.md) object in a distributed transaction.|  
|[removeConnectionEventListener](../content/removeConnectionEventListener-Method--SQLServerPooledConnection-.md)|(Inherited from [SQLServerPooledConnection](../content/SQLServerPooledConnection-Class.md)) Removes the given event listener.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|javax.sql.PooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
  
## See Also  
 [SQLServerXAConnection Class](../content/SQLServerXAConnection-Class.md)  
  
  