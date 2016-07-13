---
title: Wrappers and Interfaces
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27fc9b72-9f21-4728-abcb-5c015f28a6ab
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
# Wrappers and Interfaces
  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports interfaces that allow you create a proxy of a class, and wrappers that let you access extensions to the JDBC API that are specific to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] through a proxy interface.  
  
## Wrappers  
 The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports the java.sql.Wrapper interface. This interface provides a mechanism to access extensions to the JDBC API that are specific to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] through a proxy interface.  
  
 The java.sql.Wrapper interface defines two methods: **isWrapperFor** and **unwrap**. The **isWrapperFor** method checks whether the specified input object implements this interface. The **unwrap** method returns an object that implements this interface to allow access to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] specific methods.  
  
 **isWrapperFor** and **unwrap** methods are exposed as follows:  
  
-   [isWrapperFor Method &#40;SQLServerCallableStatement&#41;](../content/isWrapperFor-Method--SQLServerCallableStatement-.md)  
  
-   [unwrap Method &#40;SQLServerCallableStatement&#41;](../content/unwrap-Method--SQLServerCallableStatement-.md)  
  
-   [isWrapperFor Method &#40;SQLServerConnectionPoolDataSource&#41;](../content/isWrapperFor-Method--SQLServerConnectionPoolDataSource-.md)  
  
-   [unwrap Method &#40;SQLServerConnectionPoolDataSource&#41;](../content/unwrap-Method--SQLServerConnectionPoolDataSource-.md)  
  
-   [isWrapperFor Method &#40;SQLServerDataSource&#41;](../content/isWrapperFor-Method--SQLServerDataSource-.md)  
  
-   [unwrap Method &#40;SQLServerDataSource&#41;](../content/unwrap-Method--SQLServerDataSource-.md)  
  
-   [isWrapperFor Method &#40;SQLServerPreparedStatement&#41;](../content/isWrapperFor-Method--SQLServerPreparedStatement-.md)  
  
-   [unwrap Method &#40;SQLServerPreparedStatement&#41;](../content/unwrap-Method--SQLServerPreparedStatement-.md)  
  
-   [isWrapperFor Method &#40;SQLServerStatement&#41;](../content/isWrapperFor-Method--SQLServerStatement-.md)  
  
-   [unwrap Method &#40;SQLServerStatement&#41;](../content/unwrap-Method--SQLServerStatement-.md)  
  
-   [isWrapperFor Method &#40;SQLServerXADataSource&#41;](../content/isWrapperFor-Method--SQLServerXADataSource-.md)  
  
-   [unwrap Method &#40;SQLServerXADataSource&#41;](../content/unwrap-Method--SQLServerXADataSource-.md)  
  
## Interfaces  
 Beginning in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, interfaces are available for an application server to access a driver specific method from the associated class. The application server can wrap the class by creating a proxy, exposing the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific functionality from an interface. The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports interfaces that have the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] specific methods and constants so an application server can create a proxy of the class.  
  
 The interfaces derive from standard Java interfaces so you can use the same object once it is unwrapped to access driver specific functionality or generic [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] functionality.  
  
 The following interfaces are added:  
  
-   [ISQLServerCallableStatement](../content/ISQLServerCallableStatement-Interface.md)  
  
-   [ISQLServerConnection](../content/ISQLServerConnection-Interface.md)  
  
-   [ISQLServerDataSource](../content/ISQLServerDataSource-Interface.md)  
  
-   [ISQLServerPreparedStatement](../content/ISQLServerPreparedStatement-Interface.md)  
  
-   [ISQLServerResultSet](../content/ISQLServerResultSet-Interface.md)  
  
-   [ISQLServerStatement](../content/ISQLServerStatement-Interface.md)  
  
## Example  
  
### Description  
 This sample demonstrates how to access to a [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific function from a DataSource object. This DataSource class may have been wrapped by an application server. To access the JDBC driver\-specific function or constant, you can unwrap the datasource to an ISQLServerDataSource interface and use the functions declared in this interface.  
  
### Code  
  
```  
import javax.sql.*;  
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class UnWrapTest {  
   public static void main(String[] args) {  
      // This is a test.  This DataSource object could be something from an appserver   
      // which has wrapped the real SQLServerDataSource with its own wrapper  
      SQLServerDataSource ds = new SQLServerDataSource();  
      checkSendStringParametersAsUnicode(ds);  
   }  
  
   // Unwrap to the ISQLServerDataSource interface to access the getSendStringParametersAsUnicode function  
   static void checkSendStringParametersAsUnicode(DataSource ds) {  
      try {  
         final ISQLServerDataSource sqlServerDataSource = ds.unwrap(ISQLServerDataSource.class);  
         boolean sendStringParametersAsUnicode = sqlServerDataSource.getSendStringParametersAsUnicode();  
  
         System.out.println("Send string as parameter value is:-" + sendStringParametersAsUnicode);  
  
      } catch (SQLException sqlE) {  
         System.out.println("Exception:-" + sqlE);  
      }  
   }  
}  
```  
  
## See Also  
 [Understanding the JDBC Driver Data Types](../content/Understanding-the-JDBC-Driver-Data-Types.md)  
  
  