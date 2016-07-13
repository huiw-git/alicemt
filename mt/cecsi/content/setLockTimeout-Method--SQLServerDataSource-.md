---
title: setLockTimeout Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setLockTimeout
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
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
# setLockTimeout Method (SQLServerDataSource)
  Sets an **int** value that indicates the number of milliseconds to wait before the database reports a lock time out.  
  
## Syntax  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### Parameters  
 *lockTimeout*  
  
 An **int** value that contains the number of milliseconds to wait.  
  
## Remarks  
 The lock time out is the number of milliseconds to wait before the database reports a lock time out. The default value of \-1 means that it will wait indefinitely. If specified, this value will be the default for all statements on the connection.  
  
> [!NOTE]  
>  A value of 0 means no wait. If the lockTimeout property is not set, the [getLockTimeout](../content/getLockTimeout-Method--SQLServerDataSource-.md) method returns the default value of \-1.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  