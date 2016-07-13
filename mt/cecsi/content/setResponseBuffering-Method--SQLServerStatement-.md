---
title: setResponseBuffering Method (SQLServerStatement)
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
  - SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation: 
  - SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
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
# setResponseBuffering Method (SQLServerStatement)
  Sets the response buffering mode for this [SQLServerStatement](../content/SQLServerStatement-Class.md) object to case\-insensitive **String full** or **adaptive**.  
  
## Syntax  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### Parameters  
 *value*  
  
 A **String** that contains the response buffering mode. The valid mode can be one of the following case\-insensitive Strings: **full** or **adaptive**.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 **adaptive** specifies buffering the minimum possible data when necessary.  
  
 **full** specifies reading the entire result from the server at run time.  
  
 adaptive is the default value in JDBC Driver version 2.0 and 3.0. full was the default prior to JDBC Driver version 2.0.  
  
 The [setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md) method allows you to override the **responseBuffering** connection **String** property for the current [SQLServerStatement](../content/SQLServerStatement-Class.md) object. For more information about using the response buffering mode, see [Using Adaptive Buffering](../content/Using-Adaptive-Buffering.md).  
  
 If the application specifies an invalid parameter value to the [setResponseBuffering](../content/setResponseBuffering-Method--SQLServerStatement-.md) method, a [SQLServerException](../content/SQLServerException-Class.md) is thrown.  
  
## See Also  
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)   
 [Using Adaptive Buffering](../content/Using-Adaptive-Buffering.md)  
  
  