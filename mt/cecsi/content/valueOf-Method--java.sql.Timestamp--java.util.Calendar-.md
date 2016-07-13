---
title: valueOf Method (java.sql.Timestamp, java.util.Calendar)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
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
# valueOf Method (java.sql.Timestamp, java.util.Calendar)
  Creates a **DateTimeOffset** object representing a point in time at a particular offset from GMT given a java.sql.Timestamp value and a java.util.Calendar value indicating the offset.  
  
## Syntax  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### Parameters  
 *timestamp*  
  
 Ajava.sql.Timestamp value.  
  
 *calendar*  
  
 The offset value.  The date and time components of *calendar* will be set according to the *timestamp* value.  
  
## Return Value  
 Returns a DateTimeOffset object representing the point in time given by the java.sql.Timestamp object at the given java.util.Calendar object’s time zone.  
  
## Remarks  
 This method also sets the java.util.Calendar object to the point in time given by the java.sql.Timestamp object.  
  
## See Also  
 [DateTimeOffset Class](../content/DateTimeOffset-Class.md)   
 [DateTimeOffset Members](../content/DateTimeOffset-Members.md)  
  
  