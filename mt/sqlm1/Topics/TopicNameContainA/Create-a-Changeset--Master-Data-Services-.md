---
title: Create a Changeset (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
---
# Create a Changeset (Master Data Services)
  A changeset is a collection of the pending changes on the master data. If the entity requires approval for changes, the pending changes must be saved in a changeset and then submitted for administrator approval.  
  
## Prerequisites  
  
-   You must have permission to access the Explorer functional area. For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   You must have at least read access to the entity or one of its attributes.  
  
## To create a local changeset  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] home page, select  the model and version and then click **Explorer**.  
  
2.  Click an entity on the **Entities** menu.  
  
3.  In the right pane, select **Changesets** and click **Create**.  
  
4.  Enter a name for the changeset, and click **Save**.  
  
     The name of the changeset must be unique within a model.  
  
## To create a changeset for approval  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] home page, select  the model and version and then click **Explorer**.  
  
2.  Click an entity on the **Entities** menu.  
  
3.  Make changes to the entity and click on**OK**.  
  
4.  **Choose A changeset** dialog box is displayed.  
  
5.  Click **New**, enter a name for the changeset, and click **Save**. The changeset name must be unique within a model.  
  
6.  To use  an existing changeset, click **Existing** and choose the changeset from the list. Only changesets that are in an open or rejected state are available.  
  
## Next Steps  
 [Apply and Update a Changeset &#40;Master Data Services&#41;](../Topic/Apply%20and%20Update%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Commit or Submit a Changeset &#40;Master Data Services&#41;](../Topic/Commit%20or%20Submit%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Approve or Reject a Changeset &#40;Master Data Services&#41;](../Topic/Approve%20or%20Reject%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
  