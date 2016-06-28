---
title: getIndexInfo Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getIndexInfo
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
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
# getIndexInfo Method (SQLServerDatabaseMetaData)
  Retrieves a description of the indexes and statistics for the given table.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### Parameters  
 *cat*  
  
 A **String** that contains the catalog name.  
  
 *schema*  
  
 A **String** that contains the schema name.  
  
 *table*  
  
 A **String** that contains the table name.  
  
 *unique*  
  
 **true** if only indexes for unique values are returned. **false** if all indexes are returned.  
  
 *approximate*  
  
 **true** if the results reflect approximate or out\-of\-date values. **false** if the results are accurate.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getIndexInfo method is specified by the getIndexInfo method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getIndexInfo method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE\_CAT|**String**|The name of the database in which the specified table resides.|  
|TABLE\_SCHEM|**String**|The schema for the table.|  
|TABLE\_NAME|**String**|The name of the table.|  
|NON\_UNIQUE|**boolean**|Indicates whether the index values can be non\-unique.|  
|INDEX\_QUALIFIER|**String**|The name of the index owner. It will be null when TYPE is tableIndexStatistic.|  
|INDEX\_NAME|**String**|The name of the index.|  
|TYPE|**short**|The type of the index. It can be one of the following values:<br /><br /> tableIndexStatistic \(0\)<br /><br /> tableIndexClustered \(1\)<br /><br /> tableIndexHashed \(2\)<br /><br /> tableIndexOther \(3\)|  
|ORDINAL\_POSITION|**short**|The ordinal position of the column in the index. The first column in the index is 1.|  
|COLUMN\_NAME|**String**|The name of the column.|  
|ASC\_OR\_DESC|**String**|The order used in the collation of the index. It can be one of the following values:<br /><br /> A \(ascending\)<br /><br /> D \(descending\)<br /><br /> NULL \(not applicable\)<br /><br /> **Note:**  [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] always returns "A".|  
|CARDINALITY|**int**|The number of rows in the table or unique values in the index.|  
|PAGES|**int**|The number of pages used to store the index or table.|  
|FILTER\_CONDITION|**String**|The filter condition.<br /><br /> **Note:**  [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] always returns null.|  
  
> [!NOTE]  
>  For more information about the data returned by the getIndexInfo method, see "sp\_indexes \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getIndexInfo method to return information about the indexes and statistics of the Person.Contact table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
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
  
  