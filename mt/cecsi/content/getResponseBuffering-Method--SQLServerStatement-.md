---
title: "getResponseBuffering Method (SQLServerStatement)"
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
  - SQLServerStatement.getResponseBuffering()
apilocation: 
  - SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
caps.latest.revision: 23
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
# getResponseBuffering Method (SQLServerStatement)
  Retrieves the response buffering mode for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object.  
  
## Syntax  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## Return Value  
 A **String** that contains a lower-case **full** or **adaptive**.  
  
## Remarks  
 **adaptive** specifies buffering the minimum possible data when necessary.  
  
 **full** specifies reading the entire result from the server at run time.  
  
 **adaptive** is the default value in JDBC Driver version 2.0 and 3.0. **full** was the default prior to JDBC Driver version 2.0.  
  
 For more information about using the response buffering mode, see [Using Adaptive Buffering](../content/Using-Adaptive-Buffering.md).  
  
## See Also  
 [setResponseBuffering Method &#40;SQLServerStatement&#41;](../content/setResponseBuffering-Method--SQLServerStatement-.md)   
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  