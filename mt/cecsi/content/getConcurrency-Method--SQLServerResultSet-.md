---
title: "getConcurrency Method (SQLServerResultSet)"
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
  - SQLServerResultSet.getConcurrency
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 207e25f4-769c-4ff3-913c-3517b06208e4
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
# getConcurrency Method (SQLServerResultSet)
  Retrieves the concurrency mode of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Syntax  
  
```  
  
public int getConcurrency()  
```  
  
## Return Value  
 An **int** that indicates the concurrency type, which can be one of the following values:  
  
 ResultSet.CONCUR_READ_ONLY  
  
 ResultSet.CONCUR_UPDATABLE  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getConcurrency method is specified by the getConcurrency method in the java.sql.ResultSet interface.  
  
 The concurrency used is determined by the [SQLServerStatement](../content/SQLServerStatement-Class.md) object that created the result set.  
  
 This method can be used to determine the actual concurrency. If the application selected CONCUR_READ_ONLY or CONCUR_UPDATABLE, these will be returned. If the application used default concurrency, CONCUR_READ_ONLY will be returned.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  