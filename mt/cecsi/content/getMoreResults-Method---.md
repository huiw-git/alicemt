---
title: getMoreResults Method ()
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerStatement.getMoreResults ()
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: df89db50-0b2f-4094-820a-30be25ad72fe
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
# getMoreResults Method ()
  Moves to the next result of this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.  
  
## Syntax  
  
```  
  
public final boolean getMoreResults()  
```  
  
## Return Value  
 **true** if the returned result is a result set. Otherwise, **false**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getMoreResults method is specified by the getMoreResults method in the java.sql.Statement interface.  
  
 Calling the getMoreResults method implicitly closes any currently open result set objects that are obtained with the [getResultSet](../content/getResultSet-Method--SQLServerStatement-.md) method.  
  
## See Also  
 [getMoreResults Method &#40;SQLServerStatement&#41;](../content/getMoreResults-Method--SQLServerStatement-.md)   
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  