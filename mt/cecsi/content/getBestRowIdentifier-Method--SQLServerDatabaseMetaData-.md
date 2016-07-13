---
title: getBestRowIdentifier Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.getBestRowIdentifier
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: c19e9ca6-2a53-4a0c-91ab-80090c3f7229
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
# getBestRowIdentifier Method (SQLServerDatabaseMetaData)
  Retrieves a description of the optimal set of columns of a table that uniquely identifies a row.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getBestRowIdentifier(java.lang.String catalog,  
                                               java.lang.String schema,  
                                               java.lang.String table,  
                                               int scope,  
                                               boolean nullable)  
```  
  
#### Parameters  
 *catalog*  
  
 A **String** that contains the catalog name.  
  
 *schema*  
  
 A **String** that contains the schema name.  
  
 *table*  
  
 A **String** that contains the table name.  
  
 *scope*  
  
 An **int** that indicates the scope of interest. Values can include the following:  
  
 bestRowTemporary \(0\)  
  
 bestRowTransaction \(1\)  
  
 bestRowSession \(2\)  
  
 *nullable*  
  
 **true** to include nullable columns. Otherwise, **false**.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getBestRowIdentifier method is specified by the getBestRowIdentifier method in the java.sql.DatabaseMetaData interface.  
  
 The result set returned by the getBestRowIdentifier method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|SCOPE|short|The scope of the returned results. It can be one of the following values:<br /><br /> bestRowTemporary \(0\)<br /><br /> bestRowTransaction \(1\)<br /><br /> bestRowSession \(2\)|  
|COLUMN\_NAME|String|The name of the column.|  
|DATA\_TYPE|short|The SQL data type from java.sql.Types.|  
|TYPE\_NAME|String|The name of the data type.|  
|COLUMN\_SIZE|int|The precision of the column.|  
|BUFFER\_LENGTH|int|The buffer length.|  
|DECIMAL\_DIGITS|short|The scale of the column.|  
|PSEUDO\_COLUMN|short|Indicates if the column is a pseudo column. It can be one of the following values:<br /><br /> bestRowUnknown \(0\)<br /><br /> bestRowNotPseudo \(1\)<br /><br /> bestRowPseudo \(2\)|  
  
## Example  
 The following example demonstrates how to use the getBestRowIdentifier method to return information about the best row identifier for the Person.Contact table in the [!INCLUDE[ssSampleDBnormal](../content/includes/ssSampleDBnormal_md.md)] sample database.  
  
```  
public static void executeGetBestRowIdentifier(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getBestRowIdentifier(null, "Person", "Contact", 0, true);  
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
  
  