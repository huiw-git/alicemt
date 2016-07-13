---
title: getColumnPrivileges Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.getColumnPrivileges
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4ab6a671-9573-4b95-8c23-364306c60d25
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
# getColumnPrivileges Method (SQLServerDatabaseMetaData)
  Retrieves a description of the access rights for the columns in a table.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getColumnPrivileges(java.lang.String catalog,  
                                              java.lang.String schema,  
                                              java.lang.String table,  
                                              java.lang.String col)  
```  
  
#### Parameters  
 *catalog*  
  
 A **String** that contains the catalog name.  
  
 *schema*  
  
 A **String** that contains the schema name.  
  
 *table*  
  
 A **String** that contains the table name.  
  
 *col*  
  
 A **String** that contains the column name pattern.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getColumnPrivileges method is specified by the getColumnPrivileges method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getColumnPrivileges method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE\_CAT|**String**|The catalog name.|  
|TABLE\_SCHEM|**String**|The table schema name.|  
|TABLE\_NAME|**String**|The table name.|  
|COLUMN\_NAME|**String**|The column name.|  
|GRANTOR|**String**|The object granting the access.|  
|GRANTEE|**String**|The object receiving the access.|  
|PRIVILEGE|**String**|The type of access granted.|  
|IS\_GRANTABLE|**String**|Indicates if the grantee is allowed to grant access to other users.|  
  
> [!NOTE]  
>  For more information about the data returned by the getColumnPrivileges method, see "sp\_column\_privileges \(Transact\-SQL\)" in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] Books Online.  
  
## Example  
 The following example demonstrates how to use the getColumnPrivileges method to return the access rights for the FirstName column in the Person.Contact table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetColumnPrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getColumnPrivileges("AdventureWorks", "Person", "Contact", "FirstName");  
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
  
  