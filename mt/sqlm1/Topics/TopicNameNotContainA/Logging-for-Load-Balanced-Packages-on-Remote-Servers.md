---
title: Logging for Load Balanced Packages on Remote Servers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
---
# Logging for Load Balanced Packages on Remote Servers
  It is easier for an administrator to manage the logs for all the child packages that are running on various servers when all the child packages use the same log provider and they all write to the same destination. One way that you can create a common log file for all child packages is to configure the child packages to log their events to a SQL Server log provider. You can configure all the packages to use the same database, the same server, and the same instance of the server.  
  
 To view the log files, the administrator only has to log on to a single server to view the log files for all child packages.  
  
## Related Tasks  
 For information about how to enable logging in a package, see [Enable Package Logging in SQL Server Data Tools](../../Topics\TopicNameNotContainA/Enable-Package-Logging-in-SQL-Server-Data-Tools.md).  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md)  
  
  