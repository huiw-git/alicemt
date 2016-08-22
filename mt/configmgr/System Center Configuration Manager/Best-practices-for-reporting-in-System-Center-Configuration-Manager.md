---
title: "Best practices for reporting in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 64f9d931-33f1-456f-a4e4-0ec077465bd0
caps.latest.revision: 4
caps.handback.revision: 0
---
# Best practices for reporting in System Center Configuration Manager
Use the following best practices for reporting in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]:  
  
## For best performance, install the reporting services point on a remote site system server  
 Although you can install the reporting services point on the site server or a remote site system, performance is increased when you install the reporting services point on a remote site system server.  
  
## Optimize SQL Server Reporting Services queries  
 Typically, any reporting delays are because of the time it takes to run queries and retrieve the results. If you are using Microsoft SQL Server, tools such as Query Analyzer and Profiler can help you optimize queries.  
  
## Schedule report subscription processing to run outside standard office hours  
 Whenever possible, schedule report subscription processing to run outside normal office standard hours to minimize the CPU processing on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database server. This practice also improves availability for unpredicted report requests.  
  
## See Also  
 [Planning for reporting in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-reporting-in-System-Center-Configuration-Manager.md)