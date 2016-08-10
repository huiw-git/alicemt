---
title: "View the Log Shipping Report (SQL Server Management Studio)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b549f2f-3683-45e5-b8e8-8095276c41ab
caps.latest.revision: 19
caps.handback.revision: 0
manager: jhubbard
---
# View the Log Shipping Report (SQL Server Management Studio)
This topic explains how to view the Transaction Log Shipping Status report in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]. You can run a status report at a monitor server, primary server, or secondary server. To see the  most complete information about your log shipping configuration, view the report at the monitor server instance.  
  
 The report displays the status of any log shipping activity whose status is available from the server instance to which you are connected. If that server instance is involved in multiple configurations in different roles (such as serving as a monitor for one database and a secondary for another database), the displayed results contain the information of every configuration from the perspective of each role. If the stored procedure can connect to the monitor server instance for a given log shipping configuration, the report displays additional status for that configuration.  
  
 For each role performed by the current server instance, you can view the following information:  
  
|Role|Information displayed|  
|----------|---------------------------|  
|Monitor|The name and status of every primary server and secondary server that uses this server instance as its monitor server.|  
|Primary|For each primary database, the status and name of the current server instance (as the primary server), along with the primary database name. The report displays the status of the backup job (which is stored locally on the primary server).<br /><br /> The report also contains a row for each of the corresponding secondary servers. If the configuration uses a monitor server and the stored procedure can connect to the monitor, these rows display the copy status and restore status for the most recent log backup.|  
|Secondary|For each secondary database, the status and name of the current server instance (as the secondary server), along with the secondary database name.<br /><br /> The report displays the status of the copy and restore jobs at the secondary server.<br /><br /> The report also contains a row for the corresponding primary server. If the configuration uses a monitor server and the stored procedure can connect to the monitor, this row displays the status of the most recent log backup.|  
  
 The information displayed depends on whether the server instance is a monitor server, primary server, or secondary server. If information is not available, the corresponding cells are grayed out.  
  
 The report calls **sp_help_log_shipping_monitor** to get the data. For information about the required permissions, see [sp_help_log_shipping_monitor](assetId:///a4e96c45-6dcd-471a-a494-b5c619459855).  
  
### To display the Transaction Log Shipping Status report on a server instance  
  
1.  Connect to a monitor server, primary server, or secondary server.  
  
2.  Right-click the server instance in Object Explorer, point to **Reports**, and point to **Standard Reports**.  
  
3.  Click **Transaction Log Shipping Status**.  
  
## See Also  
 [Monitor Log Shipping (Transact-SQL)](../../Topics/TopicNameNotContainA/Monitor-Log-Shipping--Transact-SQL-.md)