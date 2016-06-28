---
title: getExportedKeys Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getExportedKeys
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
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
# getExportedKeys Method (SQLServerDatabaseMetaData)
  Retrieves a description of the foreign key columns that reference the primary key columns of the given table.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
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
 This getExportedKeys method is specified by the getExportedKeys method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getExportedKeys method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|PKTABLE\_CAT|**String**|The name of the catalog that contains the primary key table.|  
|PKTABLE\_SCHEM|**String**|The name of the schema of the primary key table.|  
|PKTABLE\_NAME|**String**|The name of the primary key table.|  
|PKCOLUMN\_NAME|**String**|The column name of the primary key.|  
|FKTABLE\_CAT|**String**|The name of the catalog that contains the foreign key table.|  
|FKTABLE\_SCHEM|**String**|The name of the schema of the foreign key table.|  
|FKTABLE\_NAME|**String**|The name of the foreign key table.|  
|FKCOLUMN\_NAME|**String**|The column name of the foreign key.|  
|KEY\_SEQ|**short**|The sequence number of the column in a multicolumn primary key.|  
|UPDATE\_RULE|**short**|The action applied to the foreign key when the SQL operation is an update. It can be one of the following values:<br /><br /> importedKeyNoAction \(3\)<br /><br /> importedKeyCascade \(0\)<br /><br /> importedKeySetNull \(2\)<br /><br /> importedKeySetDefault \(4\)<br /><br /> importedKeyRestrict \(1\)|  
|DELETE\_RULE|**short**|The action applied to the foreign key when the SQL operation is a deletion. It can be one of the following values:<br /><br /> importedKeyNoAction \(3\)<br /><br /> importedKeyCascade \(0\)<br /><br /> importedKeySetNull \(2\)<br /><br /> importedKeySetDefault \(4\)<br /><br /> importedKeyRestrict \(1\)|  
|FK\_NAME|**String**|The name of the foreign key.|  
|PK\_NAME|**String**|The name of the primary key.|  
|DEFERRABILITY|**short**|Indicates if the evaluation of the foreign key constraint can be deferred until a commit. It can be one of the following values:<br /><br /> importedKeyInitiallyDeferred \(5\)<br /><br /> importedKeyInitiallyImmediate \(6\)<br /><br /> importedKeyNotDeferrable \(7\)|  
  
> [!NOTE]  
>  For more information about the data returned by the getExportedKeys method, see "sp\_fkeys \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getExportedKeys method to return information about all the foreign keys that reference the primary keys of the Person.Contact table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
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
  
  