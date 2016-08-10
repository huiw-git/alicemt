---
title: "Member Revision History (Master Data Services)"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113069c5-12e6-48ec-b443-b42e14f77308
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Member Revision History (Master Data Services)
A member revision history is recorded each time a member is changed, if the entity transaction log type is member.  
  
 For information on transaction log types, see [Change the Entity Transaction Log Type (Master Data Services)](../../Topics/TopicNameNotContainA/Change-the-Entity-Transaction-Log-Type--Master-Data-Services-.md).  
  
 Member revision histories are recorded when the following changes occur.  
  
-   Members are created, deleted, reactivated or purged.  
  
-   Attribute values are changed.  
  
-   Members are moved in a hierarchy or collection  
  
## View and Manage Revision History by Entity  
 In the Explorer functional area, you can view the revisions for all members in the entity. If you have update permissions, you can roll back the member to a previous revision.  
  
 **To view and manage revision history**  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], select the model and version and then click **Explorer**.  
  
2.  Select the entity from the **Entities** menu.  
  
3.  Click **View History** to view all the historical data of the entity.  
  
4.  Click **Filter** to filter the data.  
  
5.  Click the column header to sort the data.  
  
6.  If you have update permissions, click **Revert Member** to roll back to the selected version.  
  
## View and Manage Revision History by Member  
 In the Explorer functional area, you can view the revisions for a member if you have read permissions on the member. If you have update permissions, you can roll back the member to a previous revision or add annotations to the revision.  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], select the model and version and then click **Explorer**.  
  
2.  Select the entity from the **Entities** menu.  
  
3.  Select the member.  
  
4.  Click **View History** in the right pane.  
  
## Log Retention Setting  
 You can configure how long historical data is retained by setting the **Log retention in Days** property in system settings for the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] database, and by setting **Log Retention Days** when you create or edit a model.  
  
## Related Task  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Rollback the member revision history|[Rollback Member Revision History (Master Data Services)](../../Topics/TopicNameNotContainA/Rollback-Member-Revision-History--Master-Data-Services-.md)|  
  
## See Also  
 [Create a Model (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Model--Master-Data-Services-.md)   
 [System Settings (Master Data Services)](../../Topics/TopicNameNotContainA/System-Settings--Master-Data-Services-.md)