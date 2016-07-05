---
title: getObject Method (int, java.util.Map) (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getObject (int, java.util.Map)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: df85a514-ab43-4bf6-98dd-f7f37fad1850
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
# getObject Method (int, java.util.Map) (SQLServerResultSet)
  Gets the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as an object in the Java programming language, using the given Map object.  
  
> [!NOTE]  
>  This method is not currently supported by the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)]. Using this method will always return the default mapping.  
  
## Syntax  
  
```  
  
public java.lang.Object getObject(int i,  
                                  java.util.Map map)  
```  
  
#### Parameters  
 *i*  
  
 An **int** that indicates the column index.  
  
 *map*  
  
 A Map object.  
  
## Return Value  
 An **Object** value.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getObject method is specified by the getObject method in the java.sql.ResultSet interface.  
  
 This method will return the value of the given column as a Java object. The type of the Java object will be the default Java object type corresponding to the SQL type of the column, following the mapping for built\-in types that is specified in the JDBC specification. If the value is an SQL NULL, the driver returns a Java null.  
  
 This method can also be used to read database\-specific abstract data types. In the JDBC 2.0 API, the behavior of the getObject method is extended to materialize data of SQL user\-defined types. When a column contains a structured or distinct value, the behavior of this method is as if it were a call to `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 Beginning in the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0:  
  
-   A value of type date will be returned as a java.sql.Date object.  
  
-   A value of type time will be returned as a java.sql.Time object.  
  
-   A value of type datetime2 will be returned as a java.sql.Timestamp object.  
  
-   A value of type datetimeoffset will be returned as a microsoft.sql.DateTimeOffset object.  
  
## See Also  
 [getObject Method &#40;SQLServerResultSet&#41;](../content/getObject-Method--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  