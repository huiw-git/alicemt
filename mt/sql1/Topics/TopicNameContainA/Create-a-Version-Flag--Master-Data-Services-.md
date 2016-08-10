---
title: "Create a Version Flag (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Create a Version Flag (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], create a version flag to assign to a version. The flag can indicate the version that users or subscribing systems should use.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Version Management** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
-   You must have permission to access the Version Management functional area. For more information, see [Functional Area Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Functional-Area-Permissions--Master-Data-Services-.md).  
  
### To create a version flag  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **Version Management**.  
  
2.  On the **Manage Versions** page, from the menu bar, point to **Manage** and then click **Flags**.  
  
3.  On the **Manage Version Flags** page, from the **Model** field, select the model for which you want to create a flag.  
  
4.  Click **Add**.  
  
5.  In the **Name** box, type a name.  
  
6.  In the **Description** box, type a description.  
  
7.  In the **Committed Versions Only** field, select **True** to indicate that the flag can be assigned to versions with a status of **Committed** only. Select **False** to indicate that the flag can be assigned to versions with any status.  
  
8.  Click **Save**.  
  
## Next Steps  
  
-   [Assign a Flag to a Version (Master Data Services)](../../Topics/TopicNameContainA/Assign-a-Flag-to-a-Version--Master-Data-Services-.md)  
  
## See Also  
 [Versions (Master Data Services)](../../Topics/TopicNameNotContainA/Versions--Master-Data-Services-.md)   
 [Change a Version Flag Name (Master Data Services)](../../Topics/TopicNameContainA/Change-a-Version-Flag-Name--Master-Data-Services-.md)