---
title: getFetchDirection Method (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.getFetchDirection
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
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
# getFetchDirection Method (SQLServerStatement)
  Retrieves the direction for fetching rows from database tables that is the default for result sets that are generated from this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.  
  
> [!NOTE]  
>  This method is not currently implemented by the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]. Therefore, it will always return FETCH\_UNKNOWN.  
  
## Syntax  
  
```  
  
public final int getFetchDirection()  
```  
  
## Return Value  
 An **int** that indicates the fetch direction that is specified by the [setFetchDirection](../content/setFetchDirection-Method--SQLServerStatement-.md) method.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getFetchDirection method is specified by the getFetchDirection method in the java.sql.Statement interface.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  