---
title: commit Method (SQLServerXAResource)
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
  - SQLServerXAResource.commit
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 1d0f8612-fb4a-4eca-bc37-8342e1419fd4
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
# commit Method (SQLServerXAResource)
  Commits the global transaction that is specified by the given Xid object.  
  
## Syntax  
  
```  
  
public void commit(javax.transaction.xa.Xid xid,  
                   boolean onePhase)  
```  
  
#### Parameters  
 *xid*  
  
 An Xid object.  
  
 *onePhase*  
  
 A **boolean** value.  
  
## Exceptions  
 javax.transaction.xa.XAException  
  
## Remarks  
 This commit method is specified by the commit method in the javax.transaction.xa.XAResource interface.  
  
## See Also  
 [SQLServerXAResource Methods](../content/SQLServerXAResource-Methods.md)   
 [SQLServerXAResource Members](../content/SQLServerXAResource-Members.md)   
 [SQLServerXAResource Class](../content/SQLServerXAResource-Class.md)  
  
  