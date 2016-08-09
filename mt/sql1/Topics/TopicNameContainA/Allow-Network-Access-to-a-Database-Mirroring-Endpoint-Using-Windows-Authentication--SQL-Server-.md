---
title: "Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
caps.latest.revision: 34
manager: jhubbard
---
# Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)
Using Windows Authentication for connecting the database mirroring endpoints of two instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] requires manual configuration of login accounts under the following conditions:  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] run as services under different domain accounts (in the same or trusted domains), the login of each account must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.  
  
-   If the instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] run as the Network Service account, the login of the each host computer account (*DomainName***\\***ComputerName$*) must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint. This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.  
  
> [!NOTE]  
>  Ensure that an endpoint exists for each of the server instances. For more information, see [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)](../../Topics/TopicNameContainA/Create-a-Database-Mirroring-Endpoint-for-Windows-Authentication--Transact-SQL-.md).  
  
### To configure logins for Windows Authentication  
  
1.  For the user account of each instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], create a login on the other instances of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Use a [CREATE LOGIN](assetId:///eb737149-7c92-4552-946b-91085d8b1b01) statement with the FROM WINDOWS clause.  
  
     For more information, see [Create a Login](../../Topics/TopicNameContainA/Create-a-Login.md).  
  
2.  Also, to ensure that the login user has access to the endpoint, use the [GRANT](assetId:///a760c16a-4d2d-43f2-be81-ae9315f38185) statement to grant connect permissions on the endpoint to the login. Note that granting connect permissions to the endpoint is unnecessary if the user is an Administrator.  
  
     For more information, see [Grant a Permission to a Principal](../../Topics/TopicNameContainA/Grant-a-Permission-to-a-Principal.md).  
  
## Example  
 The following [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] example creates a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login for a user account named `Otheruser` that belongs to a domain called `Adomain`. The example then grants this user connect permissions to a pre-existing database mirroring endpoint named `Mirroring_Endpoint`.  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Database Mirroring (SQL Server)](../../Topics/TopicNameNotContainA/Database-Mirroring--SQL-Server-.md)   
 [Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Transport-Security-for-Database-Mirroring-and-Always-On-Availability-Groups--SQL-Server-.md)   
 [The Database Mirroring Endpoint (SQL Server)](../../Topics/TopicNameNotContainA/The-Database-Mirroring-Endpoint--SQL-Server-.md)