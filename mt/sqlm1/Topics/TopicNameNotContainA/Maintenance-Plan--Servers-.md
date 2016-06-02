---
title: Maintenance Plan (Servers)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
---
# Maintenance Plan (Servers)
  Use the **Servers** dialog box to select the servers where you want to run the maintenance plan.  
  
 A multiserver environment containing one master server and one or more target servers must be configured to create a multiserver maintenance plan. For multiserver maintenance plans, the local server should be configured as a master server. In multiserver environments, this dialog box displays the **\(local\)** master server and all corresponding target servers. One [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job is created for the local server. It is enabled or disabled depending on whether you select the **\(local\)** server. If target servers are selected, a multiserver job is created and downloaded to each of the selected target servers. If no target servers are selected, the multiserver job is deleted.  
  
## See Also  
 [Maintenance Plans](../../Topics\TopicNameNotContainA/Maintenance-Plans.md)   
 [Create a Multiserver Environment](../Topic/Create%20a%20Multiserver%20Environment.md)   
 [Make a Master Server](../Topic/Make%20a%20Master%20Server.md)   
 [Make a Target Server](../Topic/Make%20a%20Target%20Server.md)  
  
  