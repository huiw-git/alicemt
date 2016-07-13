---
title: setResponseBuffering Method (SQLServerDataSource)
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
  - SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation: 
  - SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
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
# setResponseBuffering Method (SQLServerDataSource)
  Sets the response buffering mode for connections created by using this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.  
  
## Syntax  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### Parameters  
 *value*  
  
 A **String** that contains the buffering and streaming mode. The valid mode can be one of the following case\-insensitive Strings: **full** or **adaptive**.  
  
## Remarks  
 The **full** value specifies reading the entire result from the server at run time.  
  
 The **adaptive** value specifies buffering the minimum possible data when necessary. The **adaptive** value is the default buffering mode.  
  
 For more information about using the response buffering mode, see [Using Adaptive Buffering](../content/Using-Adaptive-Buffering.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  