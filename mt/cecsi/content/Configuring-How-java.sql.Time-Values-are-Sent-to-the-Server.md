---
title: Configuring How java.sql.Time Values are Sent to the Server
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
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
# Configuring How java.sql.Time Values are Sent to the Server
  If you use a java.sql.Time object or the java.sql.Types.TIME JDBC type to set a parameter, you can configure how the java.sql.Time value is sent to the server; either as a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **time** type or as a **datetime** type.  
  
 This scenario applies when using one of the following methods:  
  
-   [SQLServerCallableStatement.registerOutParameter\(int, int\)](../content/registerOutParameter-Method--int--int-.md)  
  
-   [SQLServerCallableStatement.registerOutParameter\(int, int, int\)](../content/registerOutParameter-Method--int--int--int-.md)  
  
-   [SQLServerCallableStatement.setTime](../content/setTime-Method--SQLServerCallableStatement-.md)  
  
-   [SQLServerPreparedStatement.setTime](../content/setTime-Method--SQLServerPreparedStatement-.md)  
  
-   [SQLServerCallableStatement.setObject](../content/setObject-Method--SQLServerCallableStatement-.md)  
  
-   [SQLServerPreparedStatement.setObject](../content/setObject-Method--SQLServerPreparedStatement-.md)  
  
 You can configure how the java.sql.Time value is sent by using the **sendTimeAsDatetime** connection property. For more information, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
 You can programmatically modify the value of the **sendTimeAsDatetime** connection property with [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 Versions of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] earlier than [!INCLUDE[ssKatmai](../content/includes/ssKatmai_md.md)] do not support the **time** data type, so applications using java.sql.Time typically store java.sql.Time values either as **datetime** or **smalldatetime** [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types.  
  
 If you want to use the **datetime** and **smalldatetime**[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types when working with java.sql.Time values, you should set the **sendTimeAsDatetime** connection property to **true**. If you want to use the **time** [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type when working with java.sql.Time values, you should set the **sendTimeAsDatetime** connection property to **false**.  
  
 Be aware that when sending java.sql.Time values into a parameter whose data type can also store the date, that default dates are different depending on whether the java.sql.Time value is sent as a **datetime** \(1\/1\/1970\) or **time** \(1\/1\/1900\) value. For more information about data conversions when sending data to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], see [Using Date and Time Data](http://go.microsoft.com/fwlink/?LinkID=145211).  
  
 In [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, **sendTimeAsDatetime** is true by default. In a future release, the **sendTimeAsDatetime** connection property may be set to false by default.  
  
 To ensure that your application continues to work as expected regardless of the default value of the **sendTimeAsDatetime** connection property you can:  
  
-   Use java.sql.Time when working with the **time**[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type.  
  
-   Use java.sql.Timestamp when working with the **datetime**, **smalldatetime**, and **datetime2**[!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data types.  
  
## See Also  
 [Understanding the JDBC Driver Data Types](../content/Understanding-the-JDBC-Driver-Data-Types.md)  
  
  