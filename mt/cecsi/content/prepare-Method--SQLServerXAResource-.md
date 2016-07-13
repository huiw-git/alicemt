---
title: prepare Method (SQLServerXAResource)
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
  - SQLServerXAResource.prepare
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f800c966-3fae-41b3-963a-464988f80da3
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
# prepare Method (SQLServerXAResource)
  Requests that the resource manager prepare for a transaction commit of the transaction specified by the given Xid object.  
  
## Syntax  
  
```  
  
public int prepare(javax.transaction.xa.Xid xid)  
```  
  
#### Parameters  
 *xid*  
  
 An Xid object.  
  
## Return Value  
 An **int** value.  
  
## Exceptions  
 javax.transaction.xa.XAException  
  
## Remarks  
 This prepare method is specified by the prepare method in the javax.transaction.xa.XAResource interface.  
  
## See Also  
 [SQLServerXAResource Methods](../content/SQLServerXAResource-Methods.md)   
 [SQLServerXAResource Members](../content/SQLServerXAResource-Members.md)   
 [SQLServerXAResource Class](../content/SQLServerXAResource-Class.md)  
  
  