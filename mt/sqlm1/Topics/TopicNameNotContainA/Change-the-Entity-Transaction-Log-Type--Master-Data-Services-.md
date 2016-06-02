---
title: Change the Entity Transaction Log Type (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
---
# Change the Entity Transaction Log Type (Master Data Services)
  You can change the transaction log type of an entity, to attribute, member, or none.  
  
|Transaction Log Type|Description|  
|--------------------------|-----------------|  
|Attribute|Entity change logs are saved at the attribute level.<br /><br /> The transaction log is saved, as it is for [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].|  
|Member|Entity change logs as saved at the row level.<br /><br /> Any attribute change triggers a new row revision.<br /><br /> When using row transaction log type, the entity is stored as a slowly changing dimension Type 4. Type 2 subscription view and Type 4 \(History\) subscription view are supported. For more information, see [Subscription View Formats &#40;Master Data Services&#41;](../Topic/Subscription%20View%20Formats%20\(Master%20Data%20Services\).md)<br /><br /> Provides better performance.|  
|None|No change logs are saved.<br /><br /> Provides the best performance.|  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the System Administration functional area.For more information, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   The entity must exist. For more information, see [Create an Entity &#40;Master Data Services&#41;](../Topic/Create%20an%20Entity%20\(Master%20Data%20Services\).md).  
  
 **To change the transaction log type**  
  
1.  In Master Data Manager, click **System Administration**.  
  
2.  On the **Manage Model** page, select the row for the model  of the entity that you want to edit and then click **Entities**.  
  
3.  On the **Manage Entity** page, select the row for  the entity that you want to update and then click **Edit**.  
  
4.  Choose the transaction log type in the drop\-down list.  
  
5.  Click **Save**.  
  
  