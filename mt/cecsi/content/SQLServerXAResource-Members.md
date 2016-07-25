---
title: "SQLServerXAResource Members"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a069bf2c-1b70-4817-b084-a508445de799
caps.latest.revision: 12
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
# SQLServerXAResource Members
  The following tables list the members exposed by the [SQLServerXAResource](../content/SQLServerXAResource-Class.md) class.  
  
## Constructors  
 None.  
  
## Fields  
  
|Name|Description|  
|----------|-----------------|  
|[SSTRANSTIGHTLYCPLD](../content/SSTRANSTIGHTLYCPLD-Field--SQLServerXAResource-.md)|Used to allow the tightly coupled XA transactions, which have different XA branch transaction IDs (XIDs) but have the same global transaction ID (GTRID).|  
  
## Inherited Fields  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|javax.transaction.xa.XAResource|TMENDRSCAN, TMFAIL, TMJOIN, TMNOFLAGS, TMONEPHASE, TMRESUME, TMSTARTRSCAN, TMSUCCESS, TMSUSPEND, XA_OK, XA_RDONLY|  
  
## Methods  
  
|Name|Description|  
|----------|-----------------|  
|[commit](../content/commit-Method--SQLServerXAResource-.md)|Commits the global transaction specified by the given Xid object.|  
|[end](../content/end-Method--SQLServerXAResource-.md)|Ends the work performed on behalf of a transaction branch.|  
|[forget](../content/forget-Method--SQLServerXAResource-.md)|Tells the resource manager to forget about a heuristically completed transaction branch.|  
|[getTransactionTimeout](../content/getTransactionTimeout-Method--SQLServerXAResource-.md)|Obtains the current transaction timeout value set for this [SQLServerXAResource](../content/SQLServerXAResource-Class.md) object.|  
|[isSameRM](../content/isSameRM-Method--SQLServerXAResource-.md)|Determines if the resource manager instance represented by the target object is the same as the resource manager instance represented by the given XAResource object.|  
|[prepare](../content/prepare-Method--SQLServerXAResource-.md)|Requests that the resource manager prepare for a transaction commit of the transaction specified by the given Xid object.|  
|[recover](../content/recover-Method--SQLServerXAResource-.md)|Obtains a list of prepared transaction branches from a resource manager.|  
|[rollback](../content/rollback-Method--SQLServerXAResource-.md)|Requests that the resource manager roll back work done on behalf of a transaction branch.|  
|[setTransactionTimeout](../content/setTransactionTimeout-Method--SQLServerXAResource-.md)|Sets the current transaction timeout value for this [SQLServerXAResource](../content/SQLServerXAResource-Class.md) object.|  
|[start](../content/start-Method--SQLServerXAResource-.md)|Starts work on behalf of a transaction branch specified in the Xid object.|  
  
## Inherited Methods  
  
|Class inherited from:|Methods|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## See Also  
 [SQLServerXAResource Class](../content/SQLServerXAResource-Class.md)  
  
  