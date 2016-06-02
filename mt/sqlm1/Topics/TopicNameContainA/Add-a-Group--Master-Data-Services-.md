---
title: Add a Group (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
---
# Add a Group (Master Data Services)
  Add a group to the **Groups** list in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] to begin the process of assigning permission to the Web application. Before a user in the group can access [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], you must give the group permission to one or more functional areas and model objects.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Users and Group Permissions** functional area.  
  
### To add a group  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **User and Group Permissions**.  
  
2.  On the **Users** page, from the menu bar, click **Manage Groups**.  
  
3.  Click **Add groups**.  
  
4.  Type the group's name preceded by the Active Directory domain name or by the server computer's name, as in *domain\\group\_name* or *computer\\group\_name*.  
  
5.  Optionally, click **Check names**.  
  
6.  Click **OK**.  
  
    > [!NOTE]  
    >  When the user first accesses [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], the user's name is added to the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] list of users.  
  
## Next Steps  
  
-   [Assign Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Assign%20Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Security &#40;Master Data Services&#41;](../Topic/Security%20\(Master%20Data%20Services\).md)  
  
  