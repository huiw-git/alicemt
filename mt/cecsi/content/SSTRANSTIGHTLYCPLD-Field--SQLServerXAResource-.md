---
title: "SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)"
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
  - SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation: 
  - SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
caps.latest.revision: 15
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
# SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
  Used to allow the tightly coupled XA transactions, which have different XA branch transaction IDs (XIDs) but have the same global transaction ID (GTRID).  
  
## Syntax  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## Field Value  
 An **int** value of 32768.  
  
## Remarks  
 Each transaction is identified by an XA branch transaction ID (XID) and a global transaction ID (GTRID). In order to allow the applications to use tightly coupled XA transactions that have different XIDs but have the same GTRID, you must set the [SSTRANSTIGHTLYCPLD](../content/SSTRANSTIGHTLYCPLD-Field--SQLServerXAResource-.md) on the flags parameter of the XAResource.start method. For more information about how to use this flag, see [Understanding XA Transactions](../content/Understanding-XA-Transactions.md).  
  
## See Also  
 [SQLServerXAResource Fields](../content/SQLServerXAResource-Fields.md)   
 [SQLServerXAResource Members](../content/SQLServerXAResource-Members.md)   
 [SQLServerXAResource Class](../content/SQLServerXAResource-Class.md)  
  
  