---
title: isNullable Method (SQLServerParameterMetaData)
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
  - SQLServerParameterMetaData.sNullable
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d7e07cff-6fc4-4c9c-8e8f-838c77734bc5
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
# isNullable Method (SQLServerParameterMetaData)
  Retrieves whether null values are allowed in the designated parameter.  
  
## Syntax  
  
```  
  
public int isNullable(int param)  
```  
  
#### Parameters  
 *param*  
  
 An **int** that indicates parameter index.  
  
## Return Value  
 An **int** that indicates the nullability of the designated parameter, which can be one of the following values:  
  
 ParameterMetaData.parameterNoNulls  
  
 ParameterMetaData.parameterNullable  
  
 ParameterMetaData.parameterNullabilityUnknown  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This isNullable method is specified by the isNullable method in the java.sql.ParameterMetaData interface.  
  
## See Also  
 [SQLServerParameterMetaData Methods](../content/SQLServerParameterMetaData-Methods.md)   
 [SQLServerParameterMetaData Members](../content/SQLServerParameterMetaData-Members.md)   
 [SQLServerParameterMetaData Class](../content/SQLServerParameterMetaData-Class.md)  
  
  