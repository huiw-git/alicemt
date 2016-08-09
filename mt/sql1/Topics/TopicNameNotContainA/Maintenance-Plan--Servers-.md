---
title: "Maintenance Plan (Servers)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Maintenance Plan (Servers)
Use the **Servers** dialog box to select the servers where you want to run the maintenance plan.  
  
 A multiserver environment containing one master server and one or more target servers must be configured to create a multiserver maintenance plan. For multiserver maintenance plans, the local server should be configured as a master server. In multiserver environments, this dialog box displays the **(local)** master server and all corresponding target servers. One [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent job is created for the local server. It is enabled or disabled depending on whether you select the **(local)** server. If target servers are selected, a multiserver job is created and downloaded to each of the selected target servers. If no target servers are selected, the multiserver job is deleted.  
  
## See Also  
 [Maintenance Plans](../../Topics/TopicNameNotContainA/Maintenance-Plans.md)   
 [Creating a Multiserver Environment](assetId:///edc2b60d-15da-40a1-8ba3-f1d473366ee6)   
 [How to: Make a Master Server (SQL Server Management Studio)](assetId:///05739a73-1fdf-4d9d-92a6-70f328380322)   
 [How to: Make a Target Server (SQL Server Management Studio)](assetId:///13aabe2d-67fe-4c67-8d49-2928dd705b7a)