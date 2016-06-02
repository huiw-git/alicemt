---
title: Resource Governor Workload Group
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
---
# Resource Governor Workload Group
  In the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Resource Governor, a workload group serves as a container for session requests that have similar classification criteria. A workload allows for aggregate monitoring of the sessions, and defines policies for the sessions. Each workload group is in a resource pool, which represents a subset of the physical resources of an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]. When a session is started, the Resource Governor classifier assigns the session to a specific workload group, and the session must run using the policies assigned to the workload group and the resources defined for the resource pool.  
  
## Workload Group Concepts  
 A workload group serves as a container for session requests that are similar according to the classification criteria that are applied to each request. A workload group allows the aggregate monitoring of resource consumption and the application of a uniform policy to all the requests in the group. A group defines the policies for its members.  
  
> [!NOTE]  
>  User\-defined workload groups can be moved from one resource pool to another.  
  
 Resource Governor predefines two workload groups: the internal group and the default group. A user cannot change anything classified as an internal group, but can monitor it. Requests are classified into the default group when the following conditions exist:  
  
-   There are no criteria to classify a request.  
  
-   There is an attempt to classify the request into a non\-existent group.  
  
-   There is a general classification failure.  
  
 Resource Governor also provides DDL statements for creating, changing, and dropping workload groups.  
  
## Workload Group Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to create a workload group.|[Create a Workload Group](../../Topics\TopicNameContainA/Create-a-Workload-Group.md)|  
|Describes how to change workload group settings.|[Change Workload Group Settings](../../Topics\TopicNameNotContainA/Change-Workload-Group-Settings.md)|  
|Describes how to delete a workload group.|[Delete a Workload Group](../../Topics\TopicNameContainA/Delete-a-Workload-Group.md)|  
  
## See Also  
 [Resource Governor](../../Topics\TopicNameNotContainA/Resource-Governor.md)   
 [Enable Resource Governor](../../Topics\TopicNameNotContainA/Enable-Resource-Governor.md)   
 [Resource Governor Resource Pool](../../Topics\TopicNameNotContainA/Resource-Governor-Resource-Pool.md)   
 [Resource Governor Classifier Function](../../Topics\TopicNameNotContainA/Resource-Governor-Classifier-Function.md)   
 [Configure Resource Governor Using a Template](../../Topics\TopicNameContainA/Configure-Resource-Governor-Using-a-Template.md)   
 [View Resource Governor Properties](../../Topics\TopicNameNotContainA/View-Resource-Governor-Properties.md)  
  
  