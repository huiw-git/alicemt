---
title: "getParameterClassName Method (SQLServerParameterMetaData)"
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
  - SQLServerParameterMetaData.getParameterClassName
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 545634d8-f06b-429a-9293-0087d758f359
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
# getParameterClassName Method (SQLServerParameterMetaData)
  Retrieves the fully-qualified name of the Java class whose instances should be passed to the [setObject](../content/setObject-Method--SQLServerPreparedStatement-.md) method of the [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) class.  
  
## Syntax  
  
```  
  
public java.lang.String getParameterClassName(int param)  
```  
  
#### Parameters  
 *param*  
  
 An **int** that indicates parameter index.  
  
## Return Value  
 A **String** that contains the fully-qualified class name.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getParameterClassName method is specified by the getParameterClassName method in the java.sql.ParameterMetaData interface.  
  
## See Also  
 [SQLServerParameterMetaData Methods](../content/SQLServerParameterMetaData-Methods.md)   
 [SQLServerParameterMetaData Members](../content/SQLServerParameterMetaData-Members.md)   
 [SQLServerParameterMetaData Class](../content/SQLServerParameterMetaData-Class.md)  
  
  