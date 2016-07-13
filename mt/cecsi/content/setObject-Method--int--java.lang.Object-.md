---
title: setObject Method (int, java.lang.Object)
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
  - SQLServerPreparedStatement.setObject (int, java.lang.Object)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 61f19faa-3006-4a1c-974c-55951e3b3000
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
# setObject Method (int, java.lang.Object)
  Sets the value of the designated parameter by using the given object.  
  
## Syntax  
  
```  
  
public final void setObject(int index,  
                            java.lang.Object obj)  
```  
  
#### Parameters  
 *index*  
  
 An **int** that indicates the parameter number.  
  
 *obj*  
  
 An object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setObject method is specified by the setObject method in the java.sql.PreparedStatement interface.  
  
 Before calling this setObject method, the application might set the specified parameter by using one of the following methods:  
  
-   The set\<Type\> methods of the SQLServerPreparedStatement class or the SQLServerCallableStatement class  
  
-   The setNull methods of the SQLServerPreparedStatement class or the SQLServerCallableStatement class  
  
-   The [registerOutParameter](../content/registerOutParameter-Method--SQLServerCallableStatement-.md) method of the SQLServerCallableStatement class  
  
 In such a case, the type of the parameter is automatically set. If the application calls this setObject method with an obj value NULL, the driver assumes that the type of the parameter is one that is set by the previously called method.  
  
 If the obj value is NULL and no type information for that parameter can be determined, this setObject method converts the specified parameter to a CHAR before sending it to the database.  
  
 Beginning with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, the behavior of this method is modified by the **sendTimeAsDatetime** connection property \([Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)\) and [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## See Also  
 [setObject Method &#40;SQLServerPreparedStatement&#41;](../content/setObject-Method--SQLServerPreparedStatement-.md)   
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  