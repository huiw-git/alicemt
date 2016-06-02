---
title: Use Certificates for a Database Mirroring Endpoint (Transact-SQL)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
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
  
 For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md).  
  
## Configuring Inbound Connections  
 Next, follow these steps for each partner that you are configuring for database mirroring. In the **master** database:  
  
1.  Create a login for the other system.  
  
2.  Create a user for that login.  
  
3.  Obtain the certificate for the mirroring endpoint of the other server instance.  
  
4.  Associate the certificate with the user created in step 2.  
  
5.  Grant CONNECT permission on the login for that mirroring endpoint.  
  
 If there is a witness, you must also set up inbound connections for it. This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.  
  
 For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md).  
  
## Security  
 Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections. For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md).  
  
 When copying a certificate to another system, use a secure copy method. Be extremely careful to keep all of your certificates secure.  
  
## See Also  
 [Create a Database Master Key](../../Topics\TopicNameContainA/Create-a-Database-Master-Key.md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../Topic/CREATE%20MASTER%20KEY%20\(Transact-SQL\).md)   
 [Transport Security for Database Mirroring and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)   
 [The Database Mirroring Endpoint &#40;SQL Server&#41;](../Topic/The%20Database%20Mirroring%20Endpoint%20\(SQL%20Server\).md)  
  
  