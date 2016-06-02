---
title: Users and Groups (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
---
# Users and Groups (Master Data Services)
  To access the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application a user must have a Windows domain account or an account on the server computer where [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] is installed. To grant access to [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] you can either:  
  
-   Add the user account to a domain or local group and then add the group to the list of groups in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
-   Add the user account to the list of users in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
    > [!NOTE]  
    >  When a user belongs to a group that has access to [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], the user's name is automatically added to the list of users the first time the user accesses [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] or the MDS [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)].  
  
 To take action within the **Explorer** functional area of the UI, the group or user must be assigned access to the **Explorer** functional area and assigned permission to model objects.  
  
 If a user or group needs access to other functional areas, the user or group must be assigned access to the specific functional area.  
  
## Best Practice  
 To simplify administration, create groups and assign each group permission to functional areas and model objects. You can then add and remove users from the groups without accessing the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] UI.  
  
 Do not assign additional permissions to an individual user, and do not include a user in multiple groups that have access to [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)]. In addition, do not use hierarchy member permissions unless you want a group to have limited access to specific members.  
  
## See Also  
 [Add a User &#40;Master Data Services&#41;](../Topic/Add%20a%20User%20\(Master%20Data%20Services\).md)   
 [Add a Group &#40;Master Data Services&#41;](../Topic/Add%20a%20Group%20\(Master%20Data%20Services\).md)   
 [Delete Users or Groups &#40;Master Data Services&#41;](../Topic/Delete%20Users%20or%20Groups%20\(Master%20Data%20Services\).md)   
 [Test a User's Permissions &#40;Master Data Services&#41;](../Topic/Test%20a%20User's%20Permissions%20\(Master%20Data%20Services\).md)  
  
  