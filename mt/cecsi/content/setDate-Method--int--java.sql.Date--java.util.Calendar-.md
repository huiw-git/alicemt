---
title: setDate Method (int, java.sql.Date, java.util.Calendar)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.setDate (int, java.sql.Date, java.util.Calendar)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 2c46f694-6dc4-429f-a037-a3bad369a7c8
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
# setDate Method (int, java.sql.Date, java.util.Calendar)
  Sets the designated parameter to the given date and calendar values.  
  
## Syntax  
  
```  
  
public final void setDate(int n,  
                          java.sql.Date x,  
                          java.util.Calendar cal)  
```  
  
#### Parameters  
 *n*  
  
 An **int** that indicates the parameter number.  
  
 *x*  
  
 A Date object.  
  
 *cal*  
  
 A Calendar object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setDate method is specified by the setDate method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [setDate Method &#40;SQLServerPreparedStatement&#41;](../content/setDate-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  