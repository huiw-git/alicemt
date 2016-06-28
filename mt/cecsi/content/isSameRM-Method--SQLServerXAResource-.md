---
title: isSameRM Method (SQLServerXAResource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerXAResource.isSameRM
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: bfa24c46-b7cf-470a-afa1-52301847a448
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
# isSameRM Method (SQLServerXAResource)
  Determines if the resource manager instance that is represented by the target object is the same as the resource manager instance that is represented by the given XAResource object.  
  
## Syntax  
  
```  
  
public boolean isSameRM(javax.transaction.xa.XAResource xares)  
```  
  
#### Parameters  
 *xares*  
  
 An XAResource object.  
  
## Return Value  
 **true** if the instances are the same. Otherwise, **false**.  
  
## Exceptions  
 javax.transaction.xa.XAException  
  
## Remarks  
 This commit method is specified by the commit method in the javax.transaction.xa.XAResource interface.  
  
## See Also  
 [SQLServerXAResource Methods](../content/SQLServerXAResource-Methods.md)   
 [SQLServerXAResource Members](../content/SQLServerXAResource-Members.md)   
 [SQLServerXAResource Class](../content/SQLServerXAResource-Class.md)  
  
  