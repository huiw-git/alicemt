---
title: "Overlapping User and Group Permissions (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Overlapping User and Group Permissions (Master Data Services)
A user's permissions are based on:  
  
-   Permissions from group memberships.  
  
-   Permissions assigned explicitly to the user.  
  
 If a user is a member of multiple groups, and those groups have access to [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], the following rules apply:  
  
-   **Deny** overrides all other permissions. If the object permission is **Deny** in one group, the effective permission is deny.  
  
-   Access permission is a union all effective permissions on a group. If the object permission is **Create** from one group and **Update** from other group, the effective permission is **Create** and **Update**.  
  
 These rules apply to both the **Models** and **Hierarchy Members** tabs. Permissions are resolved for each tab and then combined. For more information, see [How Permissions Are Determined (Master Data Services)](../../Topics/TopicNameNotContainA/How-Permissions-Are-Determined--Master-Data-Services-.md).  
  
> [!NOTE]  
>  You can view the resolution of user and group overlapping permissions in the user interface. Both the **Models** and **Hierarchy Members** tab have a drop-down list from which you can choose **Effective** to view effective permissions.  
  
## Example 1  
 ![mds&#95;conc&#95;user&#95;group&#95;ex&#95;1](../../Topics/TopicNameNotContainA/images/mds_conc_user_group_ex_1.gif "mds_conc_user_group_ex_1")  
  
 The user belongs to Group 1 and Group 2.  
  
 The user has **Read** permission to the Product entity.  
  
 Group 1 has **Update** permission to the Product entity.  
  
 Group 2 has **Read** permission to the Product entity.  
  
 Result: The user's effective permission is **Update** to the Product entity.  
  
## Example 2  
 ![mds&#95;conc&#95;user&#95;group&#95;ex&#95;2](../../Topics/TopicNameNotContainA/images/mds_conc_user_group_ex_2.gif "mds_conc_user_group_ex_2")  
  
 The user belongs to Group 1 and Group 2.  
  
 The user has **Read** permission to the Product entity.  
  
 Group 1 has **Update** permission to Product entity.  
  
 Group 2 has **Deny** permission to the Product entity.  
  
 Result: The user's effective permission is **Deny** to the Product entity.  
  
## Example 3  
 ![mds&#95;conc&#95;user&#95;group&#95;ex&#95;3](../../Topics/TopicNameNotContainA/images/mds_conc_user_group_ex_3.gif "mds_conc_user_group_ex_3")  
  
 The user belongs to Group 1 and Group 2.  
  
 The user has **Update** permission to a group of members in a hierarchy node.  
  
 Group 1 has **Read** permission to a group of members in a hierarchy node.  
  
 Group 2 has **Read** permission to a group of members in a hierarchy node.  
  
 Result: The user's effective permission is **Update** to the members.  
  
## See Also  
 [How Permissions Are Determined (Master Data Services)](../../Topics/TopicNameNotContainA/How-Permissions-Are-Determined--Master-Data-Services-.md)   
 [Overlapping Model and Member Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Overlapping-Model-and-Member-Permissions--Master-Data-Services-.md)