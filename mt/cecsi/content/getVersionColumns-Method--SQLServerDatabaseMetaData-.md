---
title: getVersionColumns Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.getVersionColumns
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 6dd275d3-d9b2-4db7-938a-d4406c940a7a
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
# getVersionColumns Method (SQLServerDatabaseMetaData)
  Retrieves a description of the columns of a table that is automatically updated when any value in a row is updated.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getVersionColumns(java.lang.String catalog,  
                                            java.lang.String schema,  
                                            java.lang.String table)  
```  
  
#### Parameters  
 *catalog*  
  
 A **String** that contains the catalog name.  
  
 *schema*  
  
 A **String** that contains the schema name pattern.  
  
 *table*  
  
 A **String** that contains the table name.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getVersionColumns method is specified by the getVersionColumns method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getVersionColumns method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|SCOPE|**short**|Not supported by the JDBC driver.|  
|COLUMN\_NAME|**String**|The column name.|  
|DATA\_TYPE|**short**|The SQL data type from java.sql.Types.|  
|TYPE\_NAME|**String**|The name of the data type.|  
|COLUMN\_SIZE|**int**|The precision of the column.|  
|BUFFER\_LENGTH|**int**|The length of the column in bytes.|  
|DECIMAL\_DIGITS|**short**|The scale of the column.|  
|PSEUDO\_COLUMN|**short**|Indicates if the column is a pseudo column. It can be one of the following values:<br /><br /> versionColumnUnknown \(0\)<br /><br /> versionColumnNotPseudo \(1\)<br /><br /> versionColumnPseudo \(2\)|  
  
> [!NOTE]  
>  For more information about the data returned by the getVersionColumns method, see "sp\_datatype\_info \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getVersionColumns method to return information about the columns that are automatically updated in the Person.Contact table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetVersionColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getVersionColumns("AdventureWorks", "Person", "Contact");  
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
  
  