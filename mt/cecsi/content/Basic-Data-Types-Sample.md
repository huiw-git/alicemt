---
title: Basic Data Types Sample
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
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
# Basic Data Types Sample
  This [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] sample application demonstrates how to use result set getter methods to retrieve basic [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type values, and how to use result set update methods to update those values.  
  
 The code file for this sample is named basicDT.java, and it can be found in the following location:  
  
 \<*installation directory*\>\\sqljdbc\_\<*version*\>\\\<*language*\>\\samples\\datatypes  
  
## Requirements  
 To run this sample application, you must set the classpath to include the sqljdbc.jar file or sqljdbc4.jar file. If the classpath is missing an entry for sqljdbc.jar or sqljdbc4.jar, the sample application will throw the common "Class not found" exception. You will also need access to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database. For more information about how to set the classpath, see [Using the JDBC Driver](../content/Using-the-JDBC-Driver.md).  
  
 You must also create the following table and sample data in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database:  
  
```  
use AdventureWorks  
CREATE TABLE DataTypesTable   
   (Col1 int IDENTITY,   
    Col2 char,  
    Col3 varchar(50),   
    Col4 bit,  
    Col5 decimal(18, 2),  
    Col6 money,  
    Col7 datetime,  
    Col8 date,  
    Col9 time,  
    Col10 datetime2,  
    Col11 datetimeoffset  
    );  
  
INSERT INTO DataTypesTable   
VALUES ('A', 'Some text.', 0, 15.25, 10.00, '01/01/2006 23:59:59.991', '01/01/2006', '23:59:59', '01/01/2006 23:59:59.12345', '01/01/2006 23:59:59.12345 -1:00')  
```  
  
> [!NOTE]  
>  The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides sqljdbc.jar and sqljdbc4.jar class library files to be used depending on your preferred Java Runtime Environment \(JRE\) settings. For more information about which JAR file to choose, see [System Requirements for the JDBC Driver](../content/System-Requirements-for-the-JDBC-Driver.md).  
  
## Example  
 In the following example, the sample code makes a connection to the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] database, and then retrieves a single row of data from the DataTypesTable test table. The custom displayRow method is then called to display all the data contained in the result set using various get\<Type\> methods of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.  
  
 Next, the sample uses various update\<Type\> methods of the SQLServerResultSet class to update the data contained in the result set, and then calls the [updateRow](../content/updateRow-Method--SQLServerResultSet-.md) method to persist that data back to the database.  
  
 Finally, the sample refreshes the data contained in the result set and then calls the custom displayRow method again to display the data contained in the result set.  
  
```java
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;  
import microsoft.sql.DateTimeOffset;  
  
public class basicDT {  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns some data  
         // and display it.  
         String SQL = "SELECT * FROM DataTypesTable";  
         stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);  
         rs = stmt.executeQuery(SQL);           
         rs.next();  
         displayRow("ORIGINAL DATA", rs);  
  
         // Update the data in the result set.  
         rs.updateString(2, "B");  
         rs.updateString(3, "Some updated text.");  
         rs.updateBoolean(4, true);  
         rs.updateDouble(5, 77.89);  
         rs.updateDouble(6, 1000.01);  
         long timeInMillis = System.currentTimeMillis();  
         Timestamp ts = new Timestamp(timeInMillis);  
         rs.updateTimestamp(7, ts);  
         rs.updateDate(8, new Date(timeInMillis));  
         rs.updateTime(9, new Time(timeInMillis));  
         rs.updateTimestamp(10, ts);  
  
         //-480 indicates GMT - 8:00 hrs  
         ((SQLServerResultSet)rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));  
  
         rs.updateRow();  
  
         // Get the updated data from the database and display it.  
         rs = stmt.executeQuery(SQL);  
         rs.next();  
         displayRow("UPDATED DATA", rs);  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
  
      finally {  
         if (rs != null)   
         try {   
         rs.close();   
         }   
         catch(Exception e) {}  
  
         if (stmt != null)   
         try { stmt.close();   
         }   
         catch(Exception e) {}  
  
         if (con != null)   
         try {   
         con.close();   
         }   
         catch(Exception e) {}  
      }  
   }  
  
   private static void displayRow(String title, ResultSet rs) {  
      try {  
         System.out.println(title);  
         System.out.println(rs.getInt(1) + " , " +  // SQL integer type.  
               rs.getString(2) + " , " +            // SQL char type.  
               rs.getString(3) + " , " +            // SQL varchar type.  
               rs.getBoolean(4) + " , " +           // SQL bit type.  
               rs.getDouble(5) + " , " +            // SQL decimal type.  
               rs.getDouble(6) + " , " +            // SQL money type.  
               rs.getTimestamp(7) + " , " +            // SQL datetime type.  
               rs.getDate(8) + " , " +              // SQL date type.  
               rs.getTime(9) + " , " +              // SQL time type.  
               rs.getTimestamp(10) + " , " +            // SQL datetime2 type.  
               ((SQLServerResultSet)rs).getDateTimeOffset(11)); // SQL datetimeoffset type.   
  
         System.out.println();  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
  
```  
  
## See Also  
 [Working with Data Types &#40;JDBC&#41;](../content/Working-with-Data-Types--JDBC-.md)  
  
  