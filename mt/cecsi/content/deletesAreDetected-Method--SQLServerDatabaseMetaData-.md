---
title: deletesAreDetected Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.deletesAreDetected
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 73f3d994-bbd7-43d2-8b64-50057e278983
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
# deletesAreDetected Method (SQLServerDatabaseMetaData)
  Retrieves whether or not a visible row delete can be detected by calling the [rowDeleted](../content/rowDeleted-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.  
  
## Syntax  
  
```  
  
public boolean deletesAreDetected(int type)  
```  
  
#### Parameters  
 *type*  
  
 An **int** that indicates the result set type, which can be one of the following values as defined in java.sql.ResultSet or SQLServerResultSet:  
  
## java.sql.ResultSet Types  
 TYPE\_FORWARD\_ONLY  
  
 TYPE\_SCROLL\_SENSITIVE  
  
 TYPE\_SCROLL\_INSENSITIVE  
  
## SQLServerResultSet Types  
 TYPE\_SS\_SCROLL\_STATIC  
  
 TYPE\_SS\_SCROLL\_KEYSET  
  
 TYPE\_SS\_DIRECT\_FORWARD\_ONLY  
  
 TYPE\_SS\_SERVER\_CURSOR\_FORWARD\_ONLY  
  
 TYPE\_SS\_SCROLL\_DYNAMIC  
  
## Return Value  
 **true** if a hole replaces the deleted row. **false** if the deleted row is removed.  
  
 When using the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] with a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database, this method returns **true** for TYPE\_SS\_SCROLL\_KEYSET cursors and **false** for all other result set types.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This deletesAreDetected method is specified by the deletesAreDetected method in the java.sql.DatabaseMetaData interface.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] detects deleted rows for all updatable cursor types, although the detection is transient for forward and dynamic cursors.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  