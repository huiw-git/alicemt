---
title: Always On Client Connectivity (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
---
# Always On Client Connectivity (SQL Server)
  This topic describes considerations for client connectivity to Always On Availability Groups, including prerequisites, restrictions, and recommendations for client configurations and settings.  
  
 **In this Topic:**  
  
-   [Client Connectivity Support](#ClientConnSupport)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="ClientConnSupport"></a> Client Connectivity Support  
 The section below provides information about [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] support for client connectivity.  
  
 **Driver Support**  
  
 The following table summarizes driver support for [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)]:  
  
|Driver|Multi\-Subnet Failover|Application Intent|Read\-Only Routing|Multi\-Subnet Failover: Faster Single Subnet Endpoint Failover|Multi\-Subnet Failover: Named Instance Resolution For SQL Clustered Instances|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Yes|Yes|Yes|Yes|Yes|  
|SQL Native Client 11.0 OLEDB|No|Yes|Yes|No|No|  
|ADO.NET with .NET Framework 4.0 with connectivity patch\*|Yes|Yes|Yes|Yes|Yes|  
|ADO.NET with .NET Framework 3.5 SP1 with connectivity patch\*\*|Yes|Yes|Yes|Yes|Yes|  
|Microsoft JDBC driver 4.0 for SQL Server|Yes|Yes|Yes|Yes|Yes|  
  
 \*Download the connectivity patch for ADO .NET with .NET Framework 4.0: [http:\/\/support.microsoft.com\/kb\/2600211](http://support.microsoft.com/kb/2600211).  
  
 \*\*Download the connectivity patch for ADO.NET with .NET Framework 3.5 SP1: [http:\/\/support.microsoft.com\/kb\/2654347](http://support.microsoft.com/kb/2654347).  
  
> [!IMPORTANT]  
>  To connect to an availability group listener, a client must use a TCP connection string.  
  
##  <a name="RelatedTasks"></a> Related Tasks  
  
-   [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../Topic/Creation%20and%20Configuration%20of%20Availability%20Groups%20\(SQL%20Server\).md)  
  
-   [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](../Topic/Create%20or%20Configure%20an%20Availability%20Group%20Listener%20\(SQL%20Server\).md)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Failover Clustering and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Failover%20Clustering%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../Topic/Availability%20Group%20Listeners,%20Client%20Connectivity,%20and%20Application%20Failover%20\(SQL%20Server\).md)   
 [About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](../Topic/About%20Client%20Connection%20Access%20to%20Availability%20Replicas%20\(SQL%20Server\).md)   
 [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)   
 [SQL Server Always On Team Blog: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)   
 [A long time delay occurs when you reconnect an IPSec connection from a computer that is running Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2](http://support.microsoft.com/kb/980915)   
 [The Cluster service takes about 30 seconds to fail over IPv6 IP addresses in Windows Server 2008 R2](http://support.microsoft.com/kb/2578113)   
 [Slow failover operation if no router exists between the cluster and an application server](http://support.microsoft.com/kb/2582281)  
  
  