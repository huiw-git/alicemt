---
title: insertsAreDetected Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDatabaseMetaData.insertsAreDetected
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: f296cc42-9d26-48c3-a360-bcf51c31f7fb
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
# insertsAreDetected Method (SQLServerDatabaseMetaData)
  Retrieves whether or not a visible row insert can be detected by calling the method [rowInserted](../content/rowInserted-Method--SQLServerResultSet-.md) method of the [SQLServerResultSet](../content/SQLServerResultSet-Class.md) class.  
  
## Syntax  
  
```  
  
public boolean insertsAreDetected(int type)  
```  
  
#### Parameters  
 *type*  
  
 An integer that indicates the result set type, which can be one of the following values as defined in java.sql.ResultSet or SQLServerResultSet:  
  
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
 **true** if the row insert can be detected. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This insertsAreDetected method is specified by the insertsAreDetected method in the java.sql.DatabaseMetaData interface.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] does not detect inserted rows for any cursor type.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  