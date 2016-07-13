---
title: supportsResultSetHoldability Method (SQLServerDatabaseMetaData)
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
  - SQLServerDatabaseMetaData.supportsResultSetHoldability
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ab575792-fd11-4ff3-8847-1368e7a322c5
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
# supportsResultSetHoldability Method (SQLServerDatabaseMetaData)
  Retrieves whether this database supports the given result set holdability.  
  
## Syntax  
  
```  
  
public boolean supportsResultSetHoldability(int holdability)  
```  
  
#### Parameters  
 *holdability*  
  
 An **int** that indicates the result set holdability, which can be one of the following values:  
  
 ResultSet.HOLD\_CURSORS\_OVER\_COMMIT  
  
 ResultSet.CLOSE\_CURSORS\_AT\_COMMIT  
  
## Return Value  
 **true** if supported. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This supportsResultSetHoldability method is specified by the supportsResultSetHoldability method in the java.sql.DatabaseMetaData interface.  
  
## See Also  
 [SQLServerDatabaseMetaData Methods](../content/SQLServerDatabaseMetaData-Methods.md)   
 [SQLServerDatabaseMetaData Members](../content/SQLServerDatabaseMetaData-Members.md)   
 [SQLServerDatabaseMetaData Class](../content/SQLServerDatabaseMetaData-Class.md)  
  
  