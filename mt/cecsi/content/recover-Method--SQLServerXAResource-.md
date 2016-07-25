---
title: "recover Method (SQLServerXAResource)"
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
  - SQLServerXAResource.recover
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
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
# recover Method (SQLServerXAResource)
  Obtains a list of prepared transaction branches from a resource manager.  
  
## Syntax  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### Parameters  
 *flags*  
  
 An **int** value that can take one of the following values: XAResource.TMSTARTRSCAN or XAResource.TMENDRSCAN or XAResource.TMNOFLAGS or XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## Return Value  
 An Xid object.  
  
## Exceptions  
 javax.transaction.xa.XAException  
  
## Remarks  
 This recover method is specified by the recover method in the javax.transaction.xa.XAResource interface.  
  
 If the parameter **flag** is not XAResource.TMSTARTRSCAN or XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, a recovery scan must be in progress.  
  
## See Also  
 [SQLServerXAResource Methods](../content/SQLServerXAResource-Methods.md)   
 [SQLServerXAResource Members](../content/SQLServerXAResource-Members.md)   
 [SQLServerXAResource Class](../content/SQLServerXAResource-Class.md)  
  
  