---
title: setTimestamp Method (int, java.sql.Timestamp, java.util.Calendar)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.setTimestamp (int, java.sql.Timestamp, java.util.Calendar))
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 10c93cbf-f831-4e00-8e37-ea728bf34b1e
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
# setTimestamp Method (int, java.sql.Timestamp, java.util.Calendar)
  Sets the designated parameter to the given timestamp and calendar values.  
  
## Syntax  
  
```  
  
public final void setTimestamp(int n,  
                               java.sql.Timestamp x,  
                               java.util.Calendar cal)  
```  
  
#### Parameters  
 *n*  
  
 An **int** that indicates the parameter number.  
  
 *x*  
  
 An Timestamp object.  
  
 *cal*  
  
 A Calendar object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setTimestamp method is specified by the setTimestamp method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [setTimestamp Method &#40;SQLServerPreparedStatement&#41;](../content/setTimestamp-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  