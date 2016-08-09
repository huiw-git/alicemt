---
title: "Use Certificates for a Database Mirroring Endpoint (Transact-SQL)"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# Use Certificates for a Database Mirroring Endpoint (Transact-SQL)
To enable certificate authentication for database mirroring on a given server instance, the system administrator must configure each server instance to use certificates on both outbound and inbound connections. Outbound connections must be configured first.  
  
> [!NOTE]  
>  All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint. Therefore, you can use only one form of authentication per server instance for database mirroring.  
  
## Configuring Outbound Connections  
 Follow these steps on each server instance that you are configuring for database mirroring:  
  
1.  In the **master** database, create a database master key.  
  
2.  In the **master** database, create an encrypted certificate on the server instance.  
  
3.  Create an endpoint for the server instance using its certificate.  
  
4.  Back up the certificate to a file and securely copy it to the other system or systems.  
  
 You must complete these steps for each partner and the witness, if there is one.  
  
 For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Outbound-Connections--Transact-SQL-.md).  
  
## Configuring Inbound Connections  
 Next, follow these steps for each partner that you are configuring for database mirroring. In the **master** database:  
  
1.  Create a login for the other system.  
  
2.  Create a user for that login.  
  
3.  Obtain the certificate for the mirroring endpoint of the other server instance.  
  
4.  Associate the certificate with the user created in step 2.  
  
5.  Grant CONNECT permission on the login for that mirroring endpoint.  
  
 If there is a witness, you must also set up inbound connections for it. This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.  
  
 For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)](../../Topics/TopicNameContainA/Allow-a-Database-Mirroring-Endpoint-to-Use-Certificates-for-Inbound-Connections--Transact-SQL-.md).  
  
## Security  
 Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections. For more information, see [The Database Mirroring Endpoint (SQL Server)](../../Topics/TopicNameNotContainA/The-Database-Mirroring-Endpoint--SQL-Server-.md).  
  
 When copying a certificate to another system, use a secure copy method. Be extremely careful to keep all of your certificates secure.  
  
## See Also  
 [Create a Database Master Key](../../Topics/TopicNameContainA/Create-a-Database-Master-Key.md)   
 [CREATE MASTER KEY (Transact-SQL)](assetId:///1710a305-1a4f-48ec-836c-11ffd0356d76)   
 [Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Transport-Security-for-Database-Mirroring-and-Always-On-Availability-Groups--SQL-Server-.md)   
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics/TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)   
 [The Database Mirroring Endpoint (SQL Server)](../../Topics/TopicNameNotContainA/The-Database-Mirroring-Endpoint--SQL-Server-.md)