---
title: getProcedureColumns Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getProcedureColumns
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0df8fe-3cd6-46e4-ae3c-dc23c35676b2
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
# getProcedureColumns Method (SQLServerDatabaseMetaData)
  Retrieves a description of the stored procedure parameters and result columns.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getProcedureColumns(java.lang.String sCatalog,  
                                              java.lang.String sSchema,  
                                              java.lang.String proc,  
                                              java.lang.String col)  
```  
  
#### Parameters  
 *sCatalog*  
  
 A **String** that contains the catalog name. Providing a null to this parameter indicates that the catalog name does not need to be used.  
  
 *sSchema*  
  
 A **String** that contains the schema name pattern. Providing a null to this parameter indicates that the schema name does not need to be used.  
  
 *proc*  
  
 A **String** that contains the procedure name pattern.  
  
 *col*  
  
 A **String** that contains the column name pattern. Providing a null to this parameter returns a row for each column.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getProcedureColumns method is specified by the getProcedureColumns method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getProcedureColumns method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|PROCEDURE\_CAT|**String**|The name of the database in which the specified stored procedure resides.|  
|PROCEDURE\_SCHEM|**String**|The schema for the stored procedure.|  
|PROCEDURE\_NAME|**String**|The name of the stored procedure.|  
|COLUMN\_NAME|**String**|The name of the column.|  
|COLUMN\_TYPE|**short**|The type of the column. It can be one of the following values:<br /><br /> procedureColumnUnknown \(0\)<br /><br /> procedureColumnIn \(1\)<br /><br /> procedureColumnInOut \(2\)<br /><br /> procedureColumnOut \(4\)<br /><br /> procedureColumnReturn \(5\)<br /><br /> procedureColumnResult \(3\)|  
|DATA\_TYPE|**smallint**|The SQL data type from java.sql.Types.|  
|TYPE\_NAME|**String**|The name of the data type.|  
|PRECISION|**int**|The total number of significant digits.|  
|LENGTH|**int**|The length of the data in bytes.|  
|SCALE|**short**|The number of digits to the right of the decimal point.|  
|RADIX|**short**|The base for numeric types.|  
|NULLABLE|**short**|Indicates if the column can contain a null value. It can be one of the following values:<br /><br /> procedureNoNulls \(0\)<br /><br /> procedureNullable \(1\)<br /><br /> procedureNullableUnknown \(2\)|  
|REMARKS|**String**|The description of the procedure column.<br /><br /> <br /><br /> **Note:** [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] does not return a value for this column.|  
|COLUMN\_DEF|**String**|The default value of the column.|  
|SQL\_DATA\_TYPE|**smallint**|This column is the same as the **DATA\_TYPE** column, except for the **datetime** and ISO **interval** data types.|  
|SQL\_DATETIME\_SUB|**smallint**|The **datetime** ISO **interval** subcode if the value of **SQL\_DATA\_TYPE** is **SQL\_DATETIME** or **SQL\_INTERVAL**. For data types other than **datetime** and ISO **interval**, this column is NULL.|  
|CHAR\_OCTET\_LENGTH|**int**|The maximum number of bytes in the column.|  
|ORDINAL\_POSITION|**int**|The index of the column within the table.|  
|IS\_NULLABLE|**String**|Indicates if the column allows null values.|  
|SS\_TYPE\_CATALOG\_NAME|**String**|The name of the catalog that contains the user\-defined type \(UDT\).|  
|SS\_TYPE\_SCHEMA\_NAME|**String**|The name of the schema that contains the user\-defined type \(UDT\).|  
|SS\_UDT\_CATALOG\_NAME|**String**|The fully\-qualified name user\-defined type \(UDT\).|  
|SS\_UDT\_SCHEMA\_NAME|**String**|The name of the catalog where an XML schema collection name is defined. If the catalog name cannot be found, this variable contains an empty string.|  
|SS\_UDT\_ASSEMBLY\_TYPE\_NAME|**String**|The name of the schema where an XML schema collection name is defined. If the schema name cannot be found, this is an empty string.|  
|SS\_XML\_SCHEMACOLLECTION\_CATALOG\_NAME|**String**|The name of an XML schema collection. If the name cannot be found, this is an empty string.|  
|SS\_XML\_SCHEMACOLLECTION\_SCHEMA\_NAME|**String**|The name of the catalog that contains the user\-defined type \(UDT\).|  
|SS\_XML\_SCHEMACOLLECTION\_NAME|**String**|The name of the schema that contains the user\-defined type \(UDT\).|  
|SS\_DATA\_TYPE|**tinyint**|The [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type that is used by extended stored procedures.<br /><br /> <br /><br /> **Note:** For more information about the data types returned by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], see "Data Types \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.|  
  
> [!NOTE]  
>  For more information about the data returned by the getProcedureColumns method, see "sp\_sproc\_columns \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getProcedureColumns method to return information about the uspGetBillOfMaterials stored procedure in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetProcedureColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedureColumns(null, null, "uspGetBillOfMaterials", null);  
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
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  