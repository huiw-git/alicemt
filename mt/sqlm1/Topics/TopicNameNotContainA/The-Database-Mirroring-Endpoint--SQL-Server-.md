---
title: The Database Mirroring Endpoint (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 39332dc5-678e-4650-9217-6aa3cdc41635
---
# The Database Mirroring Endpoint (SQL Server)
  To participate in [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] or database mirroring a server instance requires its own, dedicated *database mirroring endpoint*. This endpoint is a special\-purpose endpoint that is used exclusively to receive connections from other server instances. On a given server instance, every [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] or database mirroring connection to any other server instance uses a single database mirroring endpoint.  
  
 Database mirroring endpoints use Transmission Control Protocol \(TCP\) to send and receive messages between the server instances participating database mirroring sessions or hosting availability replicas. The database mirroring endpoint listens on a unique TCP port number.  
  
> [!NOTE]  
>  Client connections to a principal server or primary replica do not use the database mirroring endpoint.  
  
> [!NOTE]  
>  The database mirroring feature will be removed in a future version of Microsoft SQL Server. Avoid using this feature in new development work, and plan to modify applications that currently use database mirroring to use [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] instead.  
  
  
##  <a name="ServerNetworkAddress"></a> Server Network Address  
 The network address of a server instance \(its *server network address* or *Endpoint URL*\) contains the port number of its endpoint, as well as the system and domain name of its host computer. The port number uniquely identifies a specific server instance.  
  
 The following figure illustrates how two server instances on the same server are uniquely identified. The server network addresses of both server instances contain the same system name, `MYSYSTEM`, and domain name, `Adventure-Works.MyDomain.com`. To enable the system to route connections to a server instance, a server network address includes the port number associated with the mirroring endpoint of a particular server instance.  
  
 ![Server network addresses of a default instance](../../Images\Image\ImageContaina/DBM_2_instances_ports_1_system.gif "DBM_2_instances_ports_1_system")  
  
 By default, an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not contain a database mirroring endpoint. These must be created manually as part of setting up a database mirroring session. The system administrator must create a separate endpoint in each server instance that is to participate in database mirroring. Note that if more than one server instance on a given computer requires a database mirroring endpoint, specify a different port number for each endpoint.  
  
> [!IMPORTANT]  
>  If the computer running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has a firewall, the firewall configuration must allow both incoming and outgoing connections for the port specified in the endpoint.  
  
 For database mirroring and [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)], authentication and encryption are configured on the endpoint. For more information, see [Transport Security for Database Mirroring and Always On Availability Groups (SQL Server)](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
> [!IMPORTANT]  
>  Do not reconfigure an in\-use database mirroring endpoint. The server instances use each other's endpoints to learn the state of the other systems. If the endpoint is reconfigured, it might restart, which can appear to be an error to the other server instances. This is particularly important for automatic failover mode, in which reconfiguring the endpoint on a partner could cause a failover to occur.  
  
  
##  <a name="EndpointAuthenticationTypes"></a> Determining the Authentication Type for a Database Mirroring Endpoint  
 It is important to understand that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service accounts of your server instances determine what type of authentication you can use for your database mirroring endpoints, as follows:  
  
-   If every server instance is running under a domain service account, you can use Windows Authentication for your database mirroring endpoints. If all the server instances run as the same domain user account, the correct user logins exist automatically in both **master** databases. This simplifies the security configuration for the availability databases and is recommended.  
  
     If any server instances that are hosting the availability replicas for an availability group run as different accounts, the login each account must be created in **master** on the other server instance. Then, that login must be granted CONNECT permissions to connect to the database mirroring endpoint of that server instance. For more information, [Set Up Login Accounts for Database Mirroring or Always On Availability Groups (SQL Server)](../Topic/Set%20Up%20Login%20Accounts%20for%20Database%20Mirroring%20or%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md).  
  
     If your server instances use Windows Authentication, you can create database mirroring endpoints by using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)], PowerShell, or the New Availability Group Wizard.  
  
    > [!NOTE]  
    >  If a server instance that is to host an availability replica lacks a database mirroring endpoint, the New Availability Group Wizard can automatically create a database mirroring endpoint that uses Windows Authentication. For more information, see [Use the Availability Group Wizard (SQL Server Management Studio)](../Topic/Use%20the%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md).  
  
-   If any server instance is running under a built\-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication. If you are using certificates for your database mirroring endpoints, your system administrator must configure each server instance to use certificates on both outbound and inbound connections.  
  
     There is no automated method for configuring database mirroring security using certificates. You will need to use either CREATE ENDPOINT [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] statement or the **New\-SqlHadrEndpoint** PowerShell cmdlet. For more information, see [CREATE ENDPOINT (Transact-SQL)](../Topic/CREATE%20ENDPOINT%20\(Transact-SQL\).md). For information about enabling certificate authentication on a server instance, see [Use Certificates for a Database Mirroring Endpoint (Transact-SQL)](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md).  
  
  
##  <a name="RelatedTasks"></a> Related Tasks  
 **To Configure a Database Mirroring Endpoint**  
  
-   [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL)](../Topic/Create%20a%20Database%20Mirroring%20Endpoint%20for%20Windows%20Authentication%20\(Transact-SQL\).md)  
  
-   [Use Certificates for a Database Mirroring Endpoint (Transact-SQL)](../Topic/Use%20Certificates%20for%20a%20Database%20Mirroring%20Endpoint%20\(Transact-SQL\).md)  
  
    -   [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Outbound%20Connections%20\(Transact-SQL\).md)  
  
    -   [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)](../Topic/Allow%20a%20Database%20Mirroring%20Endpoint%20to%20Use%20Certificates%20for%20Inbound%20Connections%20\(Transact-SQL\).md)  
  
-   [Specify a Server Network Address (Database Mirroring)](../Topic/Specify%20a%20Server%20Network%20Address%20\(Database%20Mirroring\).md)  
  
-   [Specify the Endpoint URL When Adding or Modifying an Availability Replica (SQL Server)](../Topic/Specify%20the%20Endpoint%20URL%20When%20Adding%20or%20Modifying%20an%20Availability%20Replica%20\(SQL%20Server\).md)  
  
-   [Use the Availability Group Wizard (SQL Server Management Studio)](../Topic/Use%20the%20Availability%20Group%20Wizard%20\(SQL%20Server%20Management%20Studio\).md)  
  
 **To View Information About the Database Mirroring Endpoint**  
  
-   [sys.database_mirroring_endpoints (Transact-SQL)](../Topic/sys.database_mirroring_endpoints%20\(Transact-SQL\).md)  
  
  
## See Also  
 [Transport Security for Database Mirroring and Always On Availability Groups SQL Server)](../Topic/Transport%20Security%20for%20Database%20Mirroring%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Troubleshoot Database Mirroring Configuration (SQL Server)](../Topic/Troubleshoot%20Database%20Mirroring%20Configuration%20\(SQL%20Server\).md)   
 [sys.dm_hadr_availability_replica_states (Transact-SQL)](../Topic/sys.dm_hadr_availability_replica_states%20\(Transact-SQL\).md)   
 [sys.dm_db_mirroring_connections (Transact-SQL)](../Topic/sys.dm_db_mirroring_connections%20\(Transact-SQL\).md)  
  
  