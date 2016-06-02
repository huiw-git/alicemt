---
title: Run System Monitor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
---
# Run System Monitor
  System Monitor uses remote procedure calls \(RPCs\) to collect information from Microsoft [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Any user who has Microsoft Windows permissions to run System Monitor can use System Monitor to monitor [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
> [!NOTE]  
>  When using System Monitor or Performance Monitor, you cannot connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that is running on Windows 98.  
  
 As with all performance monitoring tools, expect some performance overhead when you use System Monitor to monitor [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The actual overhead in any specific instance depends on the hardware platform, the number of counters, and the selected update interval. However, the integration of System Monitor with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is designed to minimize any reduction in performance.  
  
> [!NOTE]  
>  If you have selected [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] performance counters to monitor in the System Monitor snap\-in, you will see the counters even if [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is not running.  
  
 For information about starting System Monitor, see [Start System Monitor &#40;Windows&#41;](../Topic/Start%20System%20Monitor%20\(Windows\).md).  
  
  