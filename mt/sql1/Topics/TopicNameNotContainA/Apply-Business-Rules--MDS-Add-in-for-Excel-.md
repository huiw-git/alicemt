---
title: "Apply Business Rules (MDS Add-in for Excel)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
caps.latest.revision: 8
caps.handback.revision: 0
manager: jhubbard
---
# Apply Business Rules (MDS Add-in for Excel)
In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/tokens/ssMDSXLS_md.md)] apply business rules when you want to validate data and confirm that it is valid. You can correct validations and re-publish the data.  
  
> [!NOTE]  
>  Data validation occurs automatically when you publish data. For more information, see [Validation (Master Data Services)](../../Topics/TopicNameNotContainA/Validation--Master-Data-Services-.md).  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have access to the **Explorer** functional area.  
  
-   You must have an active worksheet that contains MDS-managed data.  
  
### To apply business rules  
  
1.  In the **Publish and Validate** group, click **Apply Rules**.  
  
    > [!NOTE]  
    >  The number of members (rows) that are validated at one time depends on a setting in [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)]. For more information, see [Business Rule Settings](../../Topics/TopicNameNotContainA/System-Settings--Master-Data-Services-.md#BusinessRules).  
  
2.  The data is validated against business rules and two status columns are displayed. If these columns are not displayed automatically, in the **Publish and Validate** group, click **Show Status** to view them.  
  
## See Also  
 [Overview: Importing Data from Excel (MDS Add-in for Excel)](../Topic/Overview:%20Importing%20Data%20from%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)