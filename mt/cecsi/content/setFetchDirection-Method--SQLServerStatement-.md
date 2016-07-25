---
title: "setFetchDirection Method (SQLServerStatement)"
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
  - SQLServerStatement.setFetchDirection
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 18176517-2fb3-4266-924d-0f01253083d2
caps.latest.revision: 13
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
# setFetchDirection Method (SQLServerStatement)
  Gives [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] a hint as to the direction in which result set rows should be processed.  
  
> [!NOTE]  
>  The JDBC driver currently ignores the hint that is given by this method.  
  
## Syntax  
  
```  
  
public final void setFetchDirection(int nDir)  
```  
  
#### Parameters  
 *nDir*  
  
 An **int** that indicates the row processing direction, which can be one of the following values:  
  
 FETCH_FORWARD  
  
 FETCH_REVERSE  
  
 FETCH_UNKNOWN  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setFetchDirection method is specified by the setFetchDirection method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  