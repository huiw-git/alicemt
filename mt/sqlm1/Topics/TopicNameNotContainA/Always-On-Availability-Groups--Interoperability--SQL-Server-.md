---
title: Always On Availability Groups: Interoperability (SQL Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
---
# Always On Availability Groups: Interoperability (SQL Server)
  This topic documents interoperability of [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] with other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 **In This Topic:**  
  
-   [Features That Interoperate with Always On Availability Groups](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md#Interop)  
  
-   [Features that Interoperate with Always On Availability Groups with Restrictions](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md#restrictions)  
  
-   [Features that Do Not Interoperate with Always On Availability Groups](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md#NoInterop)  
  
-   [Related Content](../Topic/Always%20On%20Availability%20Groups:%20Interoperability%20\(SQL%20Server\).md#RelatedContent)  
  
##  <a name="Interop"></a> Features That Interoperate with Always On Availability Groups  
 The following table lists [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features that interoperate with [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. A link in the **More Information** column indicates that interoperability considerations exist for a given feature.  
  
|Feature|More Information|  
|-------------|----------------------|  
|Change data capture|[Replication, Change Tracking, Change Data Capture, and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Replication,%20Change%20Tracking,%20Change%20Data%20Capture,%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Change tracking|[Replication, Change Tracking, Change Data Capture, and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Replication,%20Change%20Tracking,%20Change%20Data%20Capture,%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Contained databases|[Contained Databases with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Contained%20Databases%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Database encryption|[Encrypted Databases with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Encrypted%20Databases%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Database snapshots|[Database Snapshots with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Database%20Snapshots%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|FILESTREAM and FileTable|[FILESTREAM and FileTable with Always On Availability Groups &#40;SQL Server&#41;](../Topic/FILESTREAM%20and%20FileTable%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Full\-text search|Note: Full\-Text indexes are synchronized with Always On secondary databases.|  
|Log shipping|[Prerequisites for Migrating from Log Shipping to Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites%20for%20Migrating%20from%20Log%20Shipping%20to%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Remote Blob Store \(RBS\)|[Remote Blob Store &#40;RBS&#41; and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Remote%20Blob%20Store%20\(RBS\)%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Replication|[Configure Replication for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Configure%20Replication%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)<br /><br /> [Maintaining an Always On Publication Database &#40;SQL Server&#41;](../Topic/Maintaining%20an%20Always%20On%20Publication%20Database%20\(SQL%20Server\).md)<br /><br /> [Replication, Change Tracking, Change Data Capture, and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Replication,%20Change%20Tracking,%20Change%20Data%20Capture,%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)<br /><br /> [Replication Subscribers and Always On Availability Groups &#40;SQL Server&#41;](../Topic/Replication%20Subscribers%20and%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Analysis Services|[Analysis Services with Always On Availability Groups](../../Topics\TopicNameNotContainA/Analysis-Services-with-Always-On-Availability-Groups.md)|  
|Reporting Services|Utilize read only secondary replicas as a reporting data source and reduce the load on your primary read\-write replica.<br /><br /> [Reporting Services with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Reporting%20Services%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|Service Broker|[Service Broker with Always On Availability Groups &#40;SQL Server&#41;](../Topic/Service%20Broker%20with%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)|  
|SQL Server Agent||  
  
##  <a name="restrictions"></a> Features that Interoperate with Always On Availability Groups with Restrictions  
 The following features interoperate with [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] with specific restrictions. See the linked topics for details.  
  
-   Cross\-database transactions\/distributed transactions \([!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] and Windows Server 2016 Technical Preview 2\). For more information, see [Cross-Database Transactions and Distributed Transactions for Always On Availability Groups and Database Mirroring &#40;SQL Server&#41;](../Topic/Cross-Database%20Transactions%20and%20Distributed%20Transactions%20for%20Always%20On%20Availability%20Groups%20and%20Database%20Mirroring%20\(SQL%20Server\).md)  
  
##  <a name="NoInterop"></a> Features that Do Not Interoperate with Always On Availability Groups  
 [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] does not interoperate with the following features:  
  
-   Database mirroring. For more information, see [Cross-Database Transactions and Distributed Transactions for Always On Availability Groups and Database Mirroring &#40;SQL Server&#41;](../Topic/Cross-Database%20Transactions%20and%20Distributed%20Transactions%20for%20Always%20On%20Availability%20Groups%20and%20Database%20Mirroring%20\(SQL%20Server\).md).  
  
##  <a name="RelatedContent"></a> Related Content  
  
-   **Blogs:**  
  
     [Migration Guide: Migrating to SQL Server 2012 Failover Clustering and Availability Groups from Prior Clustering and Mirroring Deployments](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [SQL Server Always On Team Blogs: The official SQL Server Always On Team Blog](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [CSS SQL Server Engineers Blogs](http://blogs.msdn.com/b/psssql/)  
  
-   **Whitepapers:**  
  
     [Migration Guide: Migrating to Always On Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping](http://msdn.microsoft.com/library/jj635217)  
  
     [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft White Papers for SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server Customer Advisory Team Whitepapers](http://sqlcat.com/)  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Prerequisites, Restrictions, and Recommendations for Always On Availability Groups &#40;SQL Server&#41;](../Topic/Prerequisites,%20Restrictions,%20and%20Recommendations%20for%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)  
  
  