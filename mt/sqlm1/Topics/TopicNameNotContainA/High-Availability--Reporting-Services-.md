---
title: High Availability (Reporting Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
---
# High Availability (Reporting Services)
  A [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server is a stateless server that stores application data, content, properties, and session information in two [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] relational databases. As such, the best way to ensure the availability of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] functionality is to do the following:  
  
-   Use the high availability features of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to maximize the uptime of the report server databases. If you configure a [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance to run in a failover cluster, you can select that instance when you create a report server database.  
  
-   Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] with the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] databases and for data sources, as possible. For more information, see [Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;](../Topic/Reporting%20Services%20with%20AlwaysOn%20Availability%20Groups%20\(SQL%20Server\).md).  
  
-   Configure multiple report servers to run in a scale\-out deployment, where all the servers share a single report server database. Deploying multiple report server instances, preferably on different servers, in a scale\-out deployment can help provide uninterrupted service in the event one of the report server instances goes down.  
  
 A scale\-out deployment provides a way to share a database. If one report server goes down, other servers in the same deployment will continue to work.  
  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is not cluster\-aware. By itself, a scale\-out deployment does not provide load balancing; it does not detect the processing loads on a report server and route new processing requests to the least busy server. It does not re\-route processing requests that failed before completion. To get load balancing features, you must configure load balancing for the Web servers that host the report servers, and then configure the report servers in a scale\-out deployment so that they share the same report server database.  
  
 The Report Server Web service and Windows service are tightly integrated and run together as a single report server instance. You cannot configure availability for one service separately from the other.  
  
## See Also  
 [High Availability Solutions &#40;SQL Server&#41;](../Topic/High%20Availability%20Solutions%20\(SQL%20Server\).md)   
 [Scale-out Deployment  - Reporting Services Native mode &#40;Configuration Manager&#41;](../Topic/Scale-out%20Deployment%20%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md)  
  
  