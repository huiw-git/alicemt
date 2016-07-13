---
title: setNull Method (int, int)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.setNull (int, int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 7e7f08e9-278a-495a-8ce3-ca173d055021
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
# setNull Method (int, int)
  Sets the designated parameter to a null value, given the type of parameter to set.  
  
## Syntax  
  
```  
  
public final void setNull(int index,  
                          int jdbcType)  
```  
  
#### Parameters  
 *index*  
  
 An **int** that indicates the parameter number.  
  
 *jdbcType*  
  
 A JDBC type code that is defined by java.sql.Types.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setNull method is specified by the setNull method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [setNull Method &#40;SQLServerPreparedStatement&#41;](../content/setNull-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  