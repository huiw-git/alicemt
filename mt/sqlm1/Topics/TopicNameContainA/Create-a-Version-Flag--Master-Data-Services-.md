---
title: Create a Version Flag (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
---
# Create a Version Flag (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], create a version flag to assign to a version. The flag can indicate the version that users or subscribing systems should use.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Version Management** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   You must have permission to access the Version Management functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
### To create a version flag  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **Version Management**.  
  
2.  On the **Manage Versions** page, from the menu bar, point to **Manage** and then click **Flags**.  
  
3.  On the **Manage Version Flags** page, from the **Model** field, select the model for which you want to create a flag.  
  
4.  Click **Add**.  
  
5.  In the **Name** box, type a name.  
  
6.  In the **Description** box, type a description.  
  
7.  In the **Committed Versions Only** field, select **True** to indicate that the flag can be assigned to versions with a status of **Committed** only. Select **False** to indicate that the flag can be assigned to versions with any status.  
  
8.  Click **Save**.  
  
## Next Steps  
  
-   [Assign a Flag to a Version &#40;Master Data Services&#41;](../Topic/Assign%20a%20Flag%20to%20a%20Version%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Versions &#40;Master Data Services&#41;](../Topic/Versions%20\(Master%20Data%20Services\).md)   
 [Change a Version Flag Name &#40;Master Data Services&#41;](../Topic/Change%20a%20Version%20Flag%20Name%20\(Master%20Data%20Services\).md)  
  
  