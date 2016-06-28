---
title: Updating Large Data Sample
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
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
# Updating Large Data Sample
  This [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] sample application demonstrates how to update a large column in a database.  
  
 The code file for this sample is named updateLargeData.java, and can be found in the following location:  
  
 \<*installation directory*\>\\sqljdbc\_\<*version*\>\\\<*language*\>\\samples\\adaptive  
  
## Requirements  
 To run this sample application, you will need access to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database. You must also set the classpath to include the sqljdbc4.jar file. If the classpath is missing an entry for sqljdbc4.jar, the sample application will throw the common "Class not found" exception. For more information about how to set the classpath, see [Using the JDBC Driver](../content/Using-the-JDBC-Driver.md).  
  
> [!NOTE]  
>  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar, or sqljdbc42.jar class library files to be used depending on your preferred Java Runtime Environment \(JRE\) settings. This sample uses the [isWrapperFor](../content/isWrapperFor-Method--SQLServerStatement-.md) and [unwrap](../content/unwrap-Method--SQLServerStatement-.md) methods, which are introduced in the JDBC 4.0 API, to access the driver\-specific response buffering methods. In order to compile and run this sample, you will need sqljdbc4.jar class library, which provides support for JDBC 4.0. For more information about which JAR file to choose, see [System Requirements for the JDBC Driver](../content/System-Requirements-for-the-JDBC-Driver.md).  
  
## Example  
 In the following example, the sample code makes a connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] database. Then, the sample code creates a Statement object and uses the [isWrapperFor](../content/isWrapperFor-Method--SQLServerStatement-.md) method to check whether the Statement object is a wrapper for the specified [SQLServerStatement](../content/SQLServerStatement-Class.md) class. The [unwrap](../content/unwrap-Method--SQLServerStatement-.md) method is used to access the driver\-specific response buffering methods.  
  
 Next, the sample code sets the response buffering mode as "**adaptive**" by using the [setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class and also demonstrates how to get the adaptive buffering mode.  
  
 Then, it runs the SQL statement, and places the data that it returns into an updateable [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
 Finally, the sample code iterates through the rows of data that are contained in the result set. If it finds an empty document summary, it uses the combination of [updateString](../content/updateString-Method--SQLServerResultSet-.md) and [updateRow](../content/updateRow-Method--SQLServerResultSet-.md) methods to update the row of data and again persist it to the database. If there is already data, it uses the [getString](../content/getString-Method--SQLServerResultSet-.md) method to display some of the data that it contains.  
  
 The default behavior of the driver is "**adaptive.**" However, for the forward\-only updatable result sets and when the data in the result set is larger than the application memory, the application has to set the adaptive buffering mode explicitly by using the [setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class.  
  
 [!CODE [JDBC#UsingAdaptiveBuffering3](../CodeSnippet/SQLDrivers/jdbc#usingadaptivebuffering3)]  
  
## See Also  
 [Working with Large Data](../content/Working-with-Large-Data.md)  
  
  