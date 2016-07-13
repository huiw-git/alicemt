---
title: setObject Method (int, java.lang.Object, int, int)
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
  - SQLServerPreparedStatement.setObject (int, java.lang.Object, int, int)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d190ee20-d669-4c6f-a081-d5cfec2f72ca
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
# setObject Method (int, java.lang.Object, int, int)
  Sets the value of the designated parameter by using the given object, target type, and scale.  
  
## Syntax  
  
```  
  
public final void setObject(int n,  
                            java.lang.Object obj,  
                            int targetSqlType,  
                            int scale)  
```  
  
#### Parameters  
 *n*  
  
 An **int** that indicates the parameter number.  
  
 *obj*  
  
 An object.  
  
 *targetSqlType*  
  
 An **int** that indicates the target type as defined in java.sql.Types.  
  
 *scale*  
  
 An **int** that indicates the number of digits to the right of the decimal point. This parameter is ignored for all types other than NUMERIC and DECIMAL.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setObject method is specified by the setObject method in the java.sql.PreparedStatement interface.  
  
 Beginning with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, the behavior of this method is modified by the **sendTimeAsDatetime** connection property \([Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)\) and [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## See Also  
 [setObject Method &#40;SQLServerPreparedStatement&#41;](../content/setObject-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  