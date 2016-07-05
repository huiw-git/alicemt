---
title: Reading Large Data Sample
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
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
# Reading Large Data Sample
  This [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] sample application demonstrates how to retrieve a large single\-column value from a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using the [getCharacterStream](../content/getCharacterStream-Method--SQLServerResultSet-.md) method.  
  
 The code file for this sample is named readLargeData.java, and it can be found in the following location:  
  
 \<*installation directory*\>\\sqljdbc\_\<*version*\>\\\<*language*\>\\samples\\adaptive  
  
## Requirements  
 To run this sample application, you will need access to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database. You must also set the classpath to include the sqljdbc.jar file or sqljdbc4.jar file. If the classpath is missing an entry for sqljdbc.jar or sqljdbc4.jar, the sample application will throw the common "Class not found" exception. For more information about how to set the classpath, see [Using the JDBC Driver](../content/Using-the-JDBC-Driver.md).  
  
> [!NOTE]  
>  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides sqljdbc.jar and sqljdbc4.jar class library files to be used depending on your preferred Java Runtime Environment \(JRE\) settings. For more information about which JAR file to choose, see [System Requirements for the JDBC Driver](../content/System-Requirements-for-the-JDBC-Driver.md).  
  
## Example  
 In the following example, the sample code makes a connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] database. Next, the sample code creates sample data and updates the Production.Document table by using a parameterized query.  
  
 In addition, the sample code demonstrates how to get the adaptive buffering mode by using the [getResponseBuffering](../content/getResponseBuffering-Method--SQLServerStatement-.md) method of the [SQLServerStatement](../content/SQLServerStatement-Class.md) class. Note that starting with the JDBC driver version 2.0 release, the responseBuffering connection property is set to "adaptive" by default.  
  
 Then, using an SQL statement with the [SQLServerStatement](../content/SQLServerStatement-Class.md) object, the sample code runs the SQL statement and places the data that it returns into a [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
 Finally, the sample code iterates through the rows of data that are contained in the result set, and uses the [getCharacterStream](../content/getCharacterStream-Method--SQLServerResultSet-.md) method to access some of the data that it contains.  
  
 [!CODE [JDBC#UsingAdaptiveBuffering1](../CodeSnippet/SQLDrivers/jdbc#usingadaptivebuffering1)]  
  
## See Also  
 [Working with Large Data](../content/Working-with-Large-Data.md)  
  
  