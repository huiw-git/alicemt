---
title: getClientInfoProperties Method (SQLServerDatabaseMetaData)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
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
# getClientInfoProperties Method (SQLServerDatabaseMetaData)
  Retrieves a list of the client information properties that the driver supports.  
  
## Syntax  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## Return Value  
 A ResultSet object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getClientInfoProperties method is specified by the getClientInfoProperties method in the java.sql.DatabaseMetaData interface.  
  
> [!NOTE]  
>  This method returns an empty result set. The driver supports setting only the **applicationName** and sets the **applicationName** only at connection time. SQL Server does not support updating the client application information after the connection is established.  
  
## See Also  
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  