---
title: getCatalogs Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.getCatalogs
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
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
# getCatalogs Method (SQLServerDatabaseMetaData)
  Retrieves the catalog names that are available in the connected server.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getCatalogs method is specified by the getCatalogs method in the java.sql.DatabaseMetaData interface.  
  
> [!NOTE]  
>  On SQL Azure, you should connect to the master database to call **SQLServerDatabaseMetaData.getCatalogs**. SQL Azure does not support returning the entire set of catalogs from a user database. **SQLServerDatabaseMetaData.getCatalogs** uses the sys.databases view to get the catalogs. Please refer to the discussion of permissions in [sys.databases \(SQL Azure Database\)](http://go.microsoft.com/fwlink/?LinkId=217396) to understand **SQLServerDatabaseMetaData.getCatalogs** behavior on SQL Azure.  
  
 The result set returned by the getCatalogs method will contain the following information:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TABLE\_CAT|**String**|The name of the catalog, including system databases in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].|  
  
## Example  
 The following example demonstrates how to use the getCatalogs method to return the names of all the databases that are contained in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], including the system databases.  
  
```  
public static void executeGetCatalogs(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCatalogs();  
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
  
  