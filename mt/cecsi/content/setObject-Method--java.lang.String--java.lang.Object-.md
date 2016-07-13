---
title: setObject Method (java.lang.String, java.lang.Object)
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
  - SQLServerCallableStatement.setObject (java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 14b84409-5510-4642-a83b-732d8511c5b1
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
# setObject Method (java.lang.String, java.lang.Object)
  Sets the value of the designated parameter using the given object.  
  
## Syntax  
  
```  
  
public void setObject(java.lang.String sCol,  
                      java.lang.Object o)  
```  
  
#### Parameters  
 *sCol*  
  
 A **String** that contains the parameter name.  
  
 *o*  
  
 An **Object** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This setObject method is specified by the setObject method in the java.sql.CallableStatement interface.  
  
 This method converts the specified parameter to a CHAR if a NULL is given, before sending it to the database. If the parameter is declared as a binary, varbinary or image SQL type, then an exception will be thrown when the statement is executed.  
  
 Beginning with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, the behavior of this method is modified by the **sendTimeAsDatetime** connection property \([Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)\) and [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## See Also  
 [setObject Method &#40;SQLServerCallableStatement&#41;](../content/setObject-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  