---
title: getTablePrivileges Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.getTablePrivileges
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 0610d667-a16d-4201-a14b-0a40048911e1
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
# getTablePrivileges Method (SQLServerDatabaseMetaData)
  Retrieves a description of the access rights for each table that is available in the given catalog, schema, or table name pattern.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getTablePrivileges(java.lang.String catalog,  
                                             java.lang.String schema,  
                                             java.lang.String table)  
```  
  
#### Parameters  
 *catalog*  
  
 A **String** that contains the catalog name. Providing a null to this parameter indicates that the catalog name does not need to be used.  
  
 *schema*  
  
 A **String** that contains the schema name pattern. Providing a null to this parameter indicates that the schema name does not need to be used.  
  
 *table*  
  
 A **String** that contains the table name pattern.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getTablePrivileges method is specified by the getTablePrivileges method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getTablePrivileges method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE\_CAT|**String**|The catalog name.|  
|TABLE\_SCHEM|**String**|The table schema name.|  
|TABLE\_NAME|**String**|The table name.|  
|GRANTOR|**String**|The object granting the access.|  
|GRANTEE|**String**|The object receiving the access.|  
|PRIVILEGE|**String**|The type of access granted.|  
|IS\_GRANTABLE|**String**|Indicates if the grantee is allowed to grant access to other users.|  
  
> [!NOTE]  
>  For more information about the data returned by the getTablePrivileges method, see "sp\_table\_privileges \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getTablePrivileges method to return the access rights for the Person.Contact table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetTablePrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTablePrivileges("AdventureWorks", "Person", "Contact");  
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
  
  