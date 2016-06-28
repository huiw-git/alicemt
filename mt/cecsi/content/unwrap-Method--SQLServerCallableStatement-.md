---
title: unwrap Method (SQLServerCallableStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbbf2728-b8c8-4c35-875a-6e967c8285dc
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
# unwrap Method (SQLServerCallableStatement)
  Returns an object that implements the specified interface to allow access to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]\-specific methods.  
  
## Syntax  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### Parameters  
 *iface*  
  
 A class of type **T** defining an interface.  
  
## Return Value  
 An object that implements the specified interface.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 The [unwrap](../content/unwrap-Method--SQLServerCallableStatement-.md) method is defined by the java.sql.Wrapper interface, which is introduced in the JDBC 4.0 Spec.  
  
 Applications might need to access extensions to the JDBC API that are specific to the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]. The unwrap method supports unwrapping to public classes that this object extends, if the classes expose vendor extensions.  
  
 [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md) implements [ISQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md), which is extended from the [ISQLServerStatement](../content/SQLServerStatement-Class.md). When this method is called, the object unwraps to the following classes: [SQLServerStatement](../content/SQLServerStatement-Class.md), [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md), and [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md).  
  
 For more information, see [Wrappers and Interfaces](../content/Wrappers-and-Interfaces.md).  
  
 The following code example demonstrates how to use the isWrapperFor and unwrap methods to check the driver extensions and invoke the vendor\-specific methods, such as [setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md) and [getResponseBuffering](../content/getResponseBuffering-Method--SQLServerStatement-.md).  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
    CallableStatement cstmt =   
       con.prepareCall("{call dbo.stored_proc_name(?, ?)}");  
  
    // The recommended way to access the JDBC   
    // Driver-specific methods is to use the JDBC 4.0 Wrapper   
    // functionality.   
    // The following code statements demonstrates how to use the   
    // isWrapperFor and unwrap methods  
    // to access the driver-specific response buffering methods.  
  
    if (cstmt.isWrapperFor(  
      com.microsoft.sqlserver.jdbc.SQLServerCallableStatement.class)) {  
     // The CallableStatement object can unwrap to   
     // SQLServerCallableStatement.  
     SQLServerCallableStatement SQLcstmt =   
     cstmt.unwrap(  
        com.microsoft.sqlserver.jdbc.SQLServerCallableStatement.class);  
     SQLcstmt.setResponseBuffering("adaptive");  
     System.out.println("Response buffering mode has been set to " +  
         SQLcstmt.getResponseBuffering());  
     }  
  
    if (cstmt.isWrapperFor(  
      com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement.class)) {  
      // The CallableStatement object can unwrap to   
      // SQLServerPreparedStatement.                    
      SQLServerPreparedStatement SQLpstmt =   
       cstmt.unwrap(  
       com.microsoft.sqlserver.jdbc.SQLServerPreparedStatement.class);  
      SQLpstmt.setResponseBuffering("adaptive");  
      System.out.println("Response buffering mode has been set to " +  
          SQLpstmt.getResponseBuffering());  
    }  
    if (cstmt.isWrapperFor(  
      com.microsoft.sqlserver.jdbc.SQLServerStatement.class)) {  
  
      // The CallableStatement object can unwrap to SQLServerStatement.   
      SQLServerStatement SQLstmt =   
        cstmt.unwrap(  
        com.microsoft.sqlserver.jdbc.SQLServerStatement.class);  
      SQLstmt.setResponseBuffering("adaptive");  
      System.out.println("Response buffering mode has been set to " +  
      SQLstmt.getResponseBuffering());  
    }  
  }  
  catch (Exception e) {  
     e.printStackTrace();  
  }  
}   
```  
  
## See Also  
 [isWrapperFor Method &#40;SQLServerCallableStatement&#41;](../content/isWrapperFor-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  