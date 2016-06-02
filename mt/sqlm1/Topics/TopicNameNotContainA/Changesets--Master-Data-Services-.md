---
title: Changesets (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f227c49a-ed46-4e0f-8992-83093456cf94
---
# Changesets (Master Data Services)
  [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] now supports the ability to save any pending changes to an entity as changesets. There are two usage scenarios for this feature.  
  
-   **Changes when “Approval Required” is turned on by Entity Administrator**  
  
     If an Entity administrator specifies that the changes to a given entity require approval before they are committed, any changes to the entity have to be saved into a new or an existing changeset before they can be submitted for approval.  For more information, see [Approval Required &#40;Master Data Services&#41;](../Topic/Approval%20Required%20\(Master%20Data%20Services\).md)  
  
     You would follow this workflow.  
  
    1.  You create a changeset. The changeset is in the Open state. See [Create a Changeset &#40;Master Data Services&#41;](../Topic/Create%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
    2.  You apply the changeset and add some changes to the changeset. See [Apply and Update a Changeset &#40;Master Data Services&#41;](../Topic/Apply%20and%20Update%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
    3.  You submit the changeset to the entity administrator for approval. The changeset is in the Pending state. See [Commit or Submit a Changeset &#40;Master Data Services&#41;](../Topic/Commit%20or%20Submit%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
    4.  The entity administrator gets an email notification that a changeset is waiting for approval. If the entity administrator approves the changeset, the changeset is in the Approved state. See [Approve or Reject a Changeset &#40;Master Data Services&#41;](../Topic/Approve%20or%20Reject%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
    5.  The approved changeset will be committed automatically. If the change is committed successfully, the changeset is in the committed state.  
  
-   **Local User changes**  
  
     If you merely want to save your local changes so you can use or retrieve them later, you can use changesets to achieve that.  
  
     You would follow this workflow.  
  
    1.  You create a changeset. The changeset is in the Open state. See [Create a Changeset &#40;Master Data Services&#41;](../Topic/Create%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
    2.  You apply the changeset and adds some changes to the changeset. See [Apply and Update a Changeset &#40;Master Data Services&#41;](../Topic/Apply%20and%20Update%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
    3.  When ready, you commit the changeset. See [Commit or Submit a Changeset &#40;Master Data Services&#41;](../Topic/Commit%20or%20Submit%20a%20Changeset%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Create a Changeset &#40;Master Data Services&#41;](../Topic/Create%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Apply and Update a Changeset &#40;Master Data Services&#41;](../Topic/Apply%20and%20Update%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Commit or Submit a Changeset &#40;Master Data Services&#41;](../Topic/Commit%20or%20Submit%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Approve or Reject a Changeset &#40;Master Data Services&#41;](../Topic/Approve%20or%20Reject%20a%20Changeset%20\(Master%20Data%20Services\).md)   
 [Manage Changesets &#40;Master Data Services&#41;](../Topic/Manage%20Changesets%20\(Master%20Data%20Services\).md)  
  
  