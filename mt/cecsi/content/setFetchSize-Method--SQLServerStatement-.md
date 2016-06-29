---
title: setFetchSize Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.setFetchSize
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 760e555e-9667-4b40-b0ba-778026ff2923
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
# setFetchSize Method (SQLServerStatement)
  Gives the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] a hint as to the number of rows that should be fetched from the database when more rows are needed.  
  
## Syntax  
  
```  
  
public final void setFetchSize(int rows)  
```  
  
#### Parameters  
 *rows*  
  
 An **int** that indicates the number of rows to fetch.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setFetchSize method is specified by the setFetchSize method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  