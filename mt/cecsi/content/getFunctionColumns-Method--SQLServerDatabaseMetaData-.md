---
title: getFunctionColumns Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
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
# getFunctionColumns Method (SQLServerDatabaseMetaData)
  Retrieves a description of the specified catalog's system\- or user\-function parameters and return type.  
  
## Syntax  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### Parameters  
 *catalog*  
  
 A **String** that contains the catalog name. If it is an empty string "", the result includes the functions without a catalog. If it is **null**, the catalog name is not used for search.  
  
 *schemaPattern*  
  
 A **String** that contains the schema name pattern. If it is an empty string "", the result includes the functions without a schema. If it is **null**, the schema name is not used for search.  
  
 *functionNamePattern*  
  
 A **String** that contains the name of a function.  
  
 *columnNamePattern*  
  
 A **String** that contains the name of a parameter.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getFunctionColumns method is specified by the getFunctionColumns method in the java.sql.DatabaseMetaData interface.  
  
 This method returns only the functions and parameters matching the specified schema, function name, and parameter name within the specified catalog.  
  
 Each row in the result set includes the following columns for a parameter description, a column description, or a return type:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|FUNCTION\_CAT|**String**|The name of the database in which the function resides.|  
|FUNCTION\_SCHEM|**String**|The schema for the function.|  
|FUNCTION\_NAME|**String**|The name of the function.|  
|COLUMN\_NAME|**String**|The name of a parameter or column.|  
|COLUMN\_TYPE|**short**|**The type of the column. It can be one of the following values:**<br /><br /> functionColumnUnknown \(0\): Unknown type.<br /><br /> functionColumnIn \(1\): Input parameter.<br /><br /> functionColumnInOut \(2\): Input\/Output parameter.<br /><br /> functionColumnOut \(3\): Output parameter.<br /><br /> functionReturn \(4\): Function return value.<br /><br /> functionColumnResult \(5\): A parameter or column is a column in the result set.|  
|DATA\_TYPE|**smallint**|The SQL data type value from Java.sql.Types.|  
|TYPE\_NAME|**String**|The name of the data type.|  
|PRECISION|**int**|The total number of significant digits.|  
|LENGTH|**int**|The length of the data in bytes.|  
|SCALE|**short**|The number of digits to the right of the decimal point.|  
|RADIX|**short**|The base for numeric types.|  
|NULLABLE|**short**|Indicates if the parameter or return value can contain a **null** value.<br /><br /> **It can be one of the following values:**<br /><br /> functionNoNulls \(0\): NULL value is not allowed.<br /><br /> functionNullable \(1\): NULL value is allowed.<br /><br /> functionNullableUnknown \(2\): Unknown.|  
|REMARKS|**String**|The comments about a column or a parameter.|  
|COLUMN\_DEF|**String**|The default value of the column.<br /><br /> **Note:** This information is available with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and is JDBC driver\-specific.|  
|SQL\_DATA\_TYPE|**smallint**|This column is the same as the **DATA\_TYPE** column, except for the **datetime** and ISO **interval** data types.<br /><br /> **Note:** This information is available with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and is JDBC driver\-specific.|  
|SQL\_DATETIME\_SUB|**smallint**|The **datetime** ISO **interval** subcode if the value of **SQL\_DATA\_TYPE** is **SQL\_DATETIME** or **SQL\_INTERVAL**. For data types other than **datetime** and ISO **interval**, this column is NULL.<br /><br /> **Note:**This information is available with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and is JDBC driver\-specific.|  
|CHAR\_OCTET\_LENGTH|**int**|The maximum length of binary and character based parameters or columns. For other data types, it is NULL.|  
|ORDINAL\_POSITION|**int**|For input and output parameters, it represents the position starting from 1.<br /><br /> For result set columns, it is the position of the column in the result set starting from 1.<br /><br /> For return value, it is 0.|  
|IS\_NULLABLE|**String**|Determines the nullability of a parameter or column.<br /><br /> It can be one of the following values:<br /><br /> **YES**: The parameter or column can include NULL values.<br /><br /> **NO**: The parameter or column can not include NULL values.<br /><br /> Empty string \(""\): Unknown.|  
|SS\_TYPE\_CATALOG\_NAME|**String**|The name of the catalog that contains the user\-defined type \(UDT\).|  
|SS\_TYPE\_SCHEMA\_NAME|**String**|The name of the schema that contains the user\-defined type \(UDT\).|  
|SS\_UDT\_CATALOG\_NAME|**String**|The fully\-qualified name user\-defined type \(UDT\).|  
|SS\_UDT\_SCHEMA\_NAME|**String**|The name of the catalog where an XML schema collection name is defined. If the catalog name cannot be found, this variable contains an empty string.|  
|SS\_UDT\_ASSEMBLY\_TYPE\_NAME|**String**|The name of the schema where an XML schema collection name is defined. If the schema name cannot be found, this is an empty string.|  
|SS\_XML\_SCHEMACOLLECTION\_CATALOG\_NAME|**String**|The name of an XML schema collection. If the name cannot be found, this is an empty string.|  
|SS\_XML\_SCHEMACOLLECTION\_SCHEMA\_NAME|**String**|The name of the catalog that contains the user\-defined type \(UDT\).|  
|SS\_XML\_SCHEMACOLLECTION\_NAME|**String**|The name of the schema that contains the user\-defined type \(UDT\).|  
|SS\_DATA\_TYPE|**tinyint**|The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type that is used by extended stored procedures.<br /><br /> **Note** For more information about the data types returned by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], see "Data Types \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.|  
  
## See Also  
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  