---
title: setWorkstationID Method (SQLServerDataSource)
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
  - SQLServerDataSource.setWorkstationID
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
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
# setWorkstationID Method (SQLServerDataSource)
  Sets the name of the client computer name that is used to connect to the data source.  
  
## Syntax  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### Parameters  
 *workstationID*  
  
 A **String** that contains the client computer name.  
  
## Remarks  
 The workstationID is the name of the client computer or workstation. If the workstationID property is not set, the default value is constructed by calling InetAddress.getLocalHost\(\).getHostName\(\) method. If getHostName returns a blank value, the getHostAddress\(\).toString\(\) method is called.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  