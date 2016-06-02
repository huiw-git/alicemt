---
title: Topologies for Web Synchronization
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
---
# Topologies for Web Synchronization
  You can choose from a variety of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Web synchronization replication topologies. Common ways to configure Web synchronization include:  
  
-   Single server  
  
-   Two servers  
  
-   Multiple [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Internet Information Services \(IIS\) systems and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] republishing  
  
 For information about configuring Web synchronization, see [Configure Web Synchronization](../../Topics\TopicNameNotContainA/Configure-Web-Synchronization.md).  
  
## Single Server  
 In the simplest topology, IIS, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Publisher, and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Distributor all reside on a single server. Subscribers synchronize by connecting to IIS on the Publisher. The Publisher can be located behind a firewall.  
  
> [!NOTE]  
>  This configuration is recommended only for intranet scenarios. For other scenarios, it is recommended that the IIS server and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Publisher\/Distributor be on separate computers.  
  
 ![Web synchronization with a single server](../../Images\Image\ImageContaina/web_sync02.gif "web_sync02")  
  
## Two Servers  
 You can place IIS on one server and configure the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Publisher and Distributor on another server. The server running IIS can be isolated from the Internet by a firewall. Subscribers synchronize by connecting to IIS.  
  
 ![Web synchronization with two servers](../../Images\Image\ImageNotContaina/web_sync03.gif "web_sync03")  
  
## Multiple IIS Systems and SQL Server Republishing  
 If you need to support very large numbers of Subscribers that synchronize at the same time, you can partition the work across multiple computers running IIS.  
  
 ![Web synchronization with multiple IIS servers](../../Images\Image\ImageNotContaina/web_sync04.gif "web_sync04")  
  
 If further load balancing is required on the computer running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can create a republishing hierarchy on multiple computers. The top\-level Publisher publishes data to Subscribers, which in turn republish the data, load balancing requests from the Subscribers.  
  
> [!NOTE]  
>  Subscribers can only synchronize with a specific Publisher. For example, a Subscriber to republisher A cannot synchronize with republisher B when A is not available.  
  
 ![Web synchronization with republishing](../../Images\Image\ImageNotContaina/web_sync05.gif "web_sync05")  
  
## See Also  
 [Configure Web Synchronization](../../Topics\TopicNameNotContainA/Configure-Web-Synchronization.md)   
 [Web Synchronization for Merge Replication](../../Topics\TopicNameNotContainA/Web-Synchronization-for-Merge-Replication.md)  
  
  