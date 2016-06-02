---
title: Monitor Disk Usage
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
---
# Monitor Disk Usage
  Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] uses Microsoft Windows operating system input\/output \(I\/O\) calls to perform read and write operations on your disk. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] manages when and how disk I\/O is performed, but the Windows operating system performs the underlying I\/O operations. The I\/O subsystem includes the system bus, disk controller cards, disks, tape drives, CD\-ROM drive, and many other I\/O devices. Disk I\/O is frequently the cause of bottlenecks in a system.  
  
 Monitoring disk activity involves two areas of focus:  
  
-   Monitoring Disk I\/O and Detecting Excess Paging  
  
-   Isolating Disk Activity That [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Creates  
  
 For more information see, [Monitoring Disk Usage](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  