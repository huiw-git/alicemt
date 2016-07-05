---
title: getTypeInfo Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getTypeInfo
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 23208f01-c1bf-4235-b29c-9051d3df59a3
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
# getTypeInfo Method (SQLServerDatabaseMetaData)
  Retrieves a description of all the standard SQL types that are supported by the current database.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getTypeInfo()  
```  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getTypeInfo method is specified by the getTypeInfo method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getTypeInfo method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TYPE\_NAME|**String**|The name of the data type.|  
|DATA\_TYPE|**short**|The SQL data type from java.sql.Types.|  
|PRECISION|**int**|The total number of significant digits.|  
|LITERAL\_PREFIX|**String**|The character or characters used before a constant.|  
|LITERAL\_SUFFIX|**String**|The character or characters used to terminate a constant.|  
|CREATE\_PARAMS|**String**|The description of the creation parameters for the data type.|  
|NULLABLE|**short**|Indicates if the column can contain a null value. It can be one of the following values:<br /><br /> typeNoNulls \(0\)<br /><br /> typeNullable \(1\)<br /><br /> typeNullableUnknown \(2\)|  
|CASE\_SENSITIVE|**boolean**|Indicates if the data type is case sensitive. "**true**" if the type is case sensitive; otherwise, "**false**".|  
|SEARCHABLE|**short**|Indicates if the column can be used in a SQL WHERE clause. It can be one of the following values:<br /><br /> typePredNone \(0\)<br /><br /> typePredChar \(1\)<br /><br /> typePredBasic \(2\)<br /><br /> typeSeachable \(3\)|  
|UNSIGNED\_ATTRIBUTE|**boolean**|Indicates the sign of the data type. "**true**" if the type is unsigned; otherwise, "**false**".|  
|FIXED\_PREC\_SCALE|**boolean**|Indicates that the data type can be a money value. "**true**" if the data type is money type; otherwise, "**false**".|  
|AUTO\_INCREMENT|**boolean**|Indicates that the data type can be automatically incremented. "**true**" if the type can be auto incremented; otherwise, "**false**".|  
|LOCAL\_TYPE\_NAME|**String**|The localized name of the data type.|  
|MINIMUM\_SCALE|**short**|The maximum number of digits to the right of the decimal point.|  
|MAXIMUM\_SCALE|**short**|The minimum number of digits to the right of the decimal point.|  
|SQL\_DATA\_TYPE|**int**|Not supported by the JDBC driver.|  
|SQL\_DATETIME\_SUB|**int**|Not supported by the JDBC driver.|  
|NUM\_PREC\_RADIX|**int**|The number of bits or digits for calculating the maximum number that a column can hold.|  
|INTERVAL\_PRECISION|**smallint**|The value of interval leading precision.|  
|USERTYPE|**smallint**|The **usertype** value from the **systypes** table. For more information, see [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.|  
  
> [!NOTE]  
>  For more information about the data returned by the getTypeInfo method, see "sp\_datatype\_info \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getTypeInfo method to return information about the data types used in a [!INCLUDE[ssVersion2005](../content/includes/ssVersion2005_md.md)] \(or later\) database.  
  
```  
public static void executeGetTypeInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTypeInfo();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  