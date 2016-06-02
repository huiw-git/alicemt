---
title: Permissions or Securables Page
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3bf077a-bec2-4161-ac0c-460586199906
---
# Permissions or Securables Page
  Use the **Permissions** page or the **Securables** page to view or set the permissions for securables. This page can be opened from many locations. The contents of the page can change slightly, depending on how the page is opened and what it contains. The top grid of the page might be populated when the page opens, or it might be empty. To add items to the upper grid, click **Search**. In the upper grid, select an item, and then set the appropriate permissions on the **Explicit** tab. To view aggregated permissions, use the **Effective** tab.  
  
 To understand the possible combinations of securables and principals, see the securable\-specific syntax links in the topic [GRANT &#40;Transact-SQL&#41;](../Topic/GRANT%20\(Transact-SQL\).md). For more information, see [Securables](../../Topics\TopicNameNotContainA/Securables.md).  
  
## Page Header  
 The header of the **Permissions** or **Securables** page varies depending on the securable or principal. It displays information relevant to the item, such as its name.  
  
## Upper Grid  
 The upper grid contains one or more items for which permissions can be set. This dialog box provides the **Search** button for selecting objects or principals to add to the upper grid. The name of the grid might display **Securables** or one or more types of securables or principals. The columns that are displayed in the upper grid vary depending on the principal or securable.  
  
 **Name**  
 The name of each principal or securable that is added to the grid.  
  
 **Type**  
 Describes the type of each item.  
  
## Explicit Tab  
 The **Explicit** tab lists the possible permissions for the securable that are selected in the upper grid. To configure the permissions, select or clear the **Grant** \(or **Allow**\), **With Grant**, and **Deny** check boxes. All options are not available for all explicit permissions.  
  
 **Permissions**  
 The name of the permission.  
  
 **Grantor**  
 The principal that granted the permission.  
  
 **Grant**  
 Select to grant this permission to the login. Clear to revoke this permission.  
  
 **With Grant**  
 Reflects the state of the WITH GRANT option for the listed permission. This box is read\-only. To apply this permission, use the [GRANT](../Topic/GRANT%20\(Transact-SQL\).md) statement.  
  
 **Deny**  
 Select to deny this permission to the login. Clear to revoke this permission.  
  
 **Column Permissions**  
 For objects that contain columns \(such as tables, views, or table\-valued functions\), the **Column Permissions** button opens the **Column Permissions** dialog box. In this dialog box, you can set **Grant**, **Allow**, or **Deny** permissions on individual columns of a table or view. This option is not available for all object types or permissions.  
  
## Effective Tab  
 The permissions that a principal has related to a securable may come from permissions that are set for several different principals. For example, a login might be granted permissions individually and also as a member of a group. The **Effective** tab shows the result of combining explicit permissions and the permissions that are received from group or role memberships. Grant permissions are aggregated. A deny permission overrides all grant permissions.  
  
 **Permissions**  
 The name of the permission.  
  
 **Column**  
 The names of columns that are affected by the permission.  
  
## See Also  
 [Database-Level Roles](../../Topics\TopicNameNotContainA/Database-Level-Roles.md)   
 [Security Center for SQL Server Database Engine and Azure SQL Database](../../Topics\TopicNameNotContainA/Security-Center-for-SQL-Server-Database-Engine-and-Azure-SQL-Database.md)  
  
  