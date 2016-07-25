---
title: "getParameterMode Method (SQLServerParameterMetaData)"
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
  - SQLServerParameterMetaData.getParameterMode
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d93c9b70-18c2-44bb-a6de-70a7e940d806
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
# getParameterMode Method (SQLServerParameterMetaData)
  Retrieves the mode of the designated parameter.  
  
## Syntax  
  
```  
  
public int getParameterMode(int param)  
```  
  
#### Parameters  
 *param*  
  
 An **int** that indicates parameter index.  
  
## Return Value  
 An **int** that indicates the mode of the designated parameter, which can be one of the following values:  
  
 ParameterMetaData.parameterModeIn  
  
 ParameterMetaData.parameterModeInOut  
  
 ParameterMetaData.parameterModeOut  
  
 ParameterMetaData.parameterModeUnknown  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getParameterMode method is specified by the getParameterMode method in the java.sql.ParameterMetaData interface.  
  
## See Also  
 [SQLServerParameterMetaData Methods](../content/SQLServerParameterMetaData-Methods.md)   
 [SQLServerParameterMetaData Members](../content/SQLServerParameterMetaData-Members.md)   
 [SQLServerParameterMetaData Class](../content/SQLServerParameterMetaData-Class.md)  
  
  