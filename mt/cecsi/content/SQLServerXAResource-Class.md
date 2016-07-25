---
title: "SQLServerXAResource Class"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df957b79-536f-4db7-b6ac-3d59343559fc
caps.latest.revision: 10
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
# SQLServerXAResource Class
  Represents an XAResource for XA distributed transaction management.  
  
 **Package:** com.microsoft.sqlserver.jdbc  
  
 **Extends:** java.lang.Object  
  
 **Implements:** javax.transaction.xa.XAResource  
  
## Syntax  
  
```  
  
public class SQLServerXAResource  
```  
  
## Remarks  
 XA transactions are implemented in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] by using [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Distributed Transaction Manager (DTC). The SQLServerXAResource class makes calls to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] extended dll named sqljdbc_xa.dll, which interfaces with DTC. XA calls that are received by SQLServerXAResource (XA_START, XA_END, XA_PREPARE, and so forth) are mapped to the corresponding calls to DTC functions.  
  
## See Also  
 [SQLServerXAResource Members](../content/SQLServerXAResource-Members.md)   
 [JDBC Driver API Reference](../content/JDBC-Driver-API-Reference.md)  
  
  