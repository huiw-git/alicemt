---
title: getParameterMetaData Method (SQLServerPreparedStatement)
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
  - SQLServerPreparedStatement.getParameterMetaData
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: c2876dec-ce29-4b61-9d74-ec3173b8cba5
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
# getParameterMetaData Method (SQLServerPreparedStatement)
  Retrieves the number, types, and properties of the parameters of this [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md) object.  
  
## Syntax  
  
```  
  
public final java.sql.ParameterMetaData getParameterMetaData()  
```  
  
## Return Value  
 A [SQLServerParameterMetaData](../content/SQLServerParameterMetaData-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getParameterMetaData method is specified by the getParameterMetaData method in the java.sql.PreparedStatement interface.  
  
## See Also  
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  