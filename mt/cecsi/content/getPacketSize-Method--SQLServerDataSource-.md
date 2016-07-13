---
title: getPacketSize Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.getPacketSize
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
manager:jhubbard
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
# getPacketSize Method (SQLServerDataSource)
  Returns the current network packet size used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)], specified in bytes.  
  
## Syntax  
  
```  
  
public int getPacketSize()  
```  
  
## Return Value  
 An **int** value containing the current network packet size.  
  
## Remarks  
 If the packetSize property is not set, the getPacketSize method returns the default value of 8000.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  