---
title: getFunctions Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44335cbd-c84d-4ef3-a6a1-fca7eb7ec768
manager:jhubbard
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
# getFunctions Method (SQLServerDatabaseMetaData)
  Retrieves a description of the system and user functions.  
  
## Syntax  
  
```  
  
public ResultSet getFunctions(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern)  
```  
  
#### Parameters  
 *catalog*  
  
 The name of a catalog in the database. If it is an empty string "", the result includes the functions without a catalog. If it is **null**, the catalog name is not used for search.  
  
 *schemaPattern*  
  
 The name of a schema. If it is an empty string "", the result includes the functions without a schema. If it is **null**, the schema name is not used for search.  
  
 *functionNamePattern*  
  
 The name of a function.  
  
## Return Value  
 A [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getFunctions method is specified by the getFunctions method in the java.sql.DatabaseMetaData interface.  
  
 This method returns only the system and user functions that match the specified schema and function name.  
  
> [!IMPORTANT]  
>  The returned result set can contain functions that the calling user does not have permissions to execute.  
  
 Each function description includes the following columns:  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|FUNCTION\_CAT|**String**|The name of the database in which the function resides.|  
|FUNCTION\_SCHEM|**String**|The name of the schema in which the function resides.|  
|FUNCTION\_NAME|**String**|The name of the function.|  
|NUM\_INPUT\_PARAMS|**int**|Reserved for future use, currently returns a \-1 value.|  
|NUM\_OUTPUT\_PARAMS|**int**|Reserved for future use, currently returns a \-1 value.|  
|NUM\_RESULT\_SETS|**int**|Reserved for future use, currently returns a \-1 value.|  
|REMARKS|**String**|The comments about the function.|  
|FUNCTION\_TYPE|**short**|The type of the function. It can be one of the following values:<br /><br /> SQL\_PT\_UNKNOWN \(0\)<br /><br /> SQL\_PT\_PROCEDURE \(1\)<br /><br /> SQL\_PT\_FUNCTION \(2\)|  
  
 All the descriptions in the returned result set are ordered by FUNCTION\_CAT, FUNCTION\_SCHEM, FUNCTION\_NAME, and SPECIFIC\_NAME.  
  
## See Also  
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  