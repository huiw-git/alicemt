---
title: Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
---
# Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)
  Using Windows Authentication for connecting the database mirroring endpoints of two instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] requires manual configuration of login accounts under the following conditions:  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] run as services under different domain accounts \(in the same or trusted domains\), the login of each account must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] run as the Network Service account, the login of the each host computer account \(*DomainName***\\***ComputerName$*\) must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint. This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.  
  
> [!NOTE]  
>  Ensure that an endpoint exists for each of the server instances. For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md).  
  
### To configure logins for Windows Authentication  
  
1.  For the user account of each instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], create a login on the other instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Use a [CREATE LOGIN](../Topic/CREATE%20LOGIN%20\(Transact-SQL\).md) statement with the FROM WINDOWS clause.  
  
     For more information, see [Create a Login](../../Topics\TopicNameContainA/Create-a-Login.md).  
  
2.  Also, to ensure that the login user has access to the endpoint, use the [GRANT](../Topic/GRANT%20\(Transact-SQL\).md) statement to grant connect permissions on the endpoint to the login. Note that granting connect permissions to the endpoint is unnecessary if the user is an Administrator.  
  
     For more information, see [Grant a Permission to a Principal](../../Topics\TopicNameContainA/Grant-a-Permission-to-a-Principal.md).  
  
## Example  
 The following [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] example creates a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login for a user account named `Otheruser` that belongs to a domain called `Adomain`. The example then grants this user connect permissions to a pre\-existing database mirroring endpoint named `Mirroring_Endpoint`.  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Database Mirroring &#40;SQL Server&#41;](../Topic/Database%20Mirroring%20\(SQL%20Server\).md)   
 [Transport Security for Database Mirroring and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)  
  
  