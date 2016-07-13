---
title: setTransactionTimeout Method (SQLServerXAResource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerXAResource.setTransactionTimeout
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 38bf4a1a-6ad3-437c-b9ed-8792ab6dde7e
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
# setTransactionTimeout Method (SQLServerXAResource)
  Sets the current transaction time out value for this [SQLServerXAResource](../content/SQLServerXAResource-Class.md) object.  
  
## Syntax  
  
```  
  
public boolean setTransactionTimeout(int seconds)  
```  
  
#### Parameters  
 *seconds*  
  
 An **int** value.  
  
## Return Value  
 **true** if the timeout was successfully set. Otherwise, **false**.  
  
## Exceptions  
 javax.transaction.xa.XAException  
  
## Remarks  
 This setTransactionTimeout method is specified by the setTransactionTimeout method in the javax.transaction.xa.XAResource interface.  
  
## See Also  
 [SQLServerXAResource Methods](../content/SQLServerXAResource-Methods.md)   
 [SQLServerXAResource Members](../content/SQLServerXAResource-Members.md)   
 [SQLServerXAResource Class](../content/SQLServerXAResource-Class.md)  
  
  