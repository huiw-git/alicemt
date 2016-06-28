---
title: Data Source Sample
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
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
# Data Source Sample
  This [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] sample application demonstrates how to connect to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using a data source object. It also demonstrates how to retrieve data from a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using a stored procedure.  
  
 The code file for this sample is named connectDS.java, and it can be found in the following location:  
  
 \<*installation directory*\>\\sqljdbc\_\<*version*\>\\\<*language*\>\\samples\\connections  
  
## Requirements  
 To run this sample application, you must set the classpath to include the sqljdbc.jar file or sqljdbc4.jar file. If the classpath is missing an entry for sqljdbc.jar or sqljdbc4.jar, the sample application will throw the common "Class not found" exception. You will also need access to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database. For more information about how to set the classpath, see [Using the JDBC Driver](../content/Using-the-JDBC-Driver.md).  
  
> [!NOTE]  
>  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides sqljdbc.jar and sqljdbc4.jar class library files to be used depending on your preferred Java Runtime Environment \(JRE\) settings. For more information about which JAR file to choose, see [System Requirements for the JDBC Driver](../content/System-Requirements-for-the-JDBC-Driver.md).  
  
## Example  
 In the following example, the sample code sets various connection properties by using setter methods of the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object, and then calls the [getConnection](../content/getConnection-Method--SQLServerDataSource-.md) method of the SQLServerDataSource object to return a [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
 Next, the sample code uses the [prepareCall](../content/prepareCall-Method--SQLServerConnection-.md) method of the SQLServerConnection object to create a [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) object, and then the [executeQuery](../content/executeQuery-Method--SQLServerPreparedStatement-.md) method is called to execute the stored procedure.  
  
 Finally, the sample uses the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object returned from the executeQuery method to iterate through the results returned by the stored procedure.  
  
```java
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class connectDS {  
  
   public static void main(String[] args) {  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      CallableStatement cstmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.   
         SQLServerDataSource ds = new SQLServerDataSource();  
         ds.setUser("UserName");  
         ds.setPassword("*****");  
         ds.setServerName("localhost");  
         ds.setPortNumber(1433);   
         ds.setDatabaseName("AdventureWorks");  
         con = ds.getConnection();  
  
         // Execute a stored procedure that returns some data.  
         cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");  
         cstmt.setInt(1, 50);  
         rs = cstmt.executeQuery();  
  
         // Iterate through the data in the result set and display it.  
         while (rs.next()) {  
            System.out.println("EMPLOYEE: " + rs.getString("LastName") +   
               ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER: " + rs.getString("ManagerLastName") +   
               ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
         }  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (cstmt != null) try { cstmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
         System.exit(1);  
      }  
   }  
}  
```  
  
## See Also  
 [Connecting and Retrieving Data](../content/Connecting-and-Retrieving-Data.md)  
  
  