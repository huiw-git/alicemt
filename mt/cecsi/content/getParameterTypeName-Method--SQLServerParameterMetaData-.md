---
title: "getParameterTypeName Method (SQLServerParameterMetaData)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerParameterMetaData.getParameterTypeName
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: ebe7ff0f-3cc0-408e-9503-4ca754c9c37f
caps.latest.revision: 8
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
# getParameterTypeName Method (SQLServerParameterMetaData)
  Retrieves the database-specific type name of the designated parameter.  
  
## Syntax  
  
```  
  
public java.lang.String getParameterTypeName(int param)  
```  
  
#### Parameters  
 *param*  
  
 An **int** that indicates parameter index.  
  
## Return Value  
 A **String** that contains type name.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getParameterTypeName method is specified by the getParameterTypeName method in the java.sql.ParameterMetaData interface.  
  
## See Also  
 [SQLServerParameterMetaData Methods](../content/SQLServerParameterMetaData-Methods.md)   
 [SQLServerParameterMetaData Members](../content/SQLServerParameterMetaData-Members.md)   
 [SQLServerParameterMetaData Class](../content/SQLServerParameterMetaData-Class.md)  
  
  