---
title: getLockTimeout Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.getLockTimeout
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
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
# getLockTimeout Method (SQLServerDataSource)
  Returns an **int** value that indicates the number of milliseconds that the database will wait before reporting a lock time out.  
  
## Syntax  
  
```  
  
public int getLockTimeout()  
```  
  
## Return Value  
 An **int** value that contains the number of milliseconds that the database will wait.  
  
## Remarks  
 The lock time out is the number of milliseconds to wait before the database reports a lock time out. The default value of \-1 means that it will wait indefinitely. If specified, this value will be the default for all statements on the connection.  
  
> [!NOTE]  
>  A value of 0 means no wait. If the lockTimeout property is not set, the getLockTimeout method returns the default value of \-1.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  