---
title: getPrimaryKeys Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getPrimaryKeys
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ebfe236a-dc02-493e-a3ab-5353d3769e36
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
# getPrimaryKeys Method (SQLServerDatabaseMetaData)
  Retrieves a description of the primary key columns of the given table.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getPrimaryKeys(java.lang.String cat,  
                                         java.lang.String schema,  
                                         java.lang.String table)  
```  
  
#### Parameters  
 *cat*  
  
 A **String** that contains the catalog name.  
  
 *schema*  
  
 A **String** that contains the schema name.  
  
 *table*  
  
 A **String** that contains the table name.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getPrimaryKeys method is specified by the getPrimaryKeys method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getPrimaryKeys method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE\_CAT|String|The name of the database in which the specified table resides.|  
|TABLE\_SCHEM|String|The schema for the table.|  
|TABLE\_NAME|String|The name of the table.|  
|COLUMN\_NAME|String|The name of the column.|  
|KEY\_SEQ|short|The sequence number of the column in a multicolumn primary key.|  
|PK\_NAME|String|The name of the primary key.|  
  
> [!NOTE]  
>  For more information about the data returned by the getPrimaryKeys method, see "sp\_pkeys \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getPrimaryKeys method to return information about the primary keys of the Person.Contact table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetPrimaryKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getPrimaryKeys("AdventureWorks", "Person", "Contact");  
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
  
  