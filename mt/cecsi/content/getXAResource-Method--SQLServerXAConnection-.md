---
title: getXAResource Method (SQLServerXAConnection)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerXAConnection.getXAResource
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
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
# getXAResource Method (SQLServerXAConnection)
  Retrieves a [SQLServerXAResource](../content/SQLServerXAResource-Class.md) object that the transaction manager will use to manage this [SQLServerXAConnection](../content/SQLServerXAConnection-Class.md) object's participation in a distributed transaction.  
  
## Syntax  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## Return Value  
 An XAResource object.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getXAResource method is specified by the getXAResource method in the javax.sql.XAConnection interface.  
  
## See Also  
 [SQLServerXAConnection Methods](../content/SQLServerXAConnection-Methods.md)   
 [SQLServerXAConnection Members](../content/SQLServerXAConnection-Members.md)   
 [SQLServerXAConnection Class](../content/SQLServerXAConnection-Class.md)  
  
  