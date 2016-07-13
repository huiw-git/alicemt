---
title: getXAConnection Method ()
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerXADataSource.getXAConnection ()
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b2710613-78b1-438f-b996-c7ae6f34381a
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
# getXAConnection Method ()
  Tries to establish a physical database connection that can be used in a distributed transaction.  
  
## Syntax  
  
```  
  
public javax.sql.XAConnection getXAConnection()  
```  
  
## Return Value  
 An XAConnection object.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getXAConnection method is specified by the getXAConnection method in the javax.sql.XADataSource interface.  
  
> [!NOTE]  
>  This method is typically called by XA connection pool implementations and not by regular JDBC application code.  
  
## See Also  
 [getXAConnection Method &#40;SQLServerXADataSource&#41;](../content/getXAConnection-Method--SQLServerXADataSource-.md)   
 [SQLServerXADataSource Methods](../content/SQLServerXADataSource-Methods.md)   
 [SQLServerXADataSource Members](../content/SQLServerXADataSource-Members.md)   
 [SQLServerXADataSource Class](../content/SQLServerXADataSource-Class.md)  
  
  