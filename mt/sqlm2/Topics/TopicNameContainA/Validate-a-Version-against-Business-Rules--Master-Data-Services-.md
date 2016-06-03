---
title: Validate a Version against Business Rules (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
---
# Validate a Version against Business Rules (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], validate a version to apply business rules to all members in the model version.  
  
 This procedure explains how to use the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application to validate data. If you have permission in the MDS database, you can use a stored procedure instead. For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../../Topics\TopicNameNotContainA/Validation-Stored-Procedure--Master-Data-Services-.md).  
  
> [!NOTE]  
>  All members must pass validation before a version can be committed.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Version Management** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../../Topics\TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
-   The version's status must be **Open** or **Locked**.  
  
-   On the **Validate Versions** page, members must exist with a status other than **Validation succeeded**.  
  
### To validate a version  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **Version Management**.  
  
2.  On the **Manage Versions** page, from the menu bar, click **Validate Version**.  
  
3.  On the **Validate Versions** page, select the model and version you want to validate.  
  
4.  Click **Validate**.  
  
5.  In the confirmation dialog box, click **OK**.  
  
    > [!NOTE]  
    >  When the progress indicator is no longer displayed, the version has finished validation.  
  
## Next Steps  
  
-   [Lock a Version &#40;Master Data Services&#41;](../../Topics\TopicNameContainA/Lock-a-Version--Master-Data-Services-.md)  
  
## See Also  
 [Validation Statuses &#40;Master Data Services&#41;](../../Topics\TopicNameNotContainA/Validation-Statuses--Master-Data-Services-.md)   
 [Validation Stored Procedure &#40;Master Data Services&#41;](../../Topics\TopicNameNotContainA/Validation-Stored-Procedure--Master-Data-Services-.md)   
 [Versions &#40;Master Data Services&#41;](../../Topics\TopicNameNotContainA/Versions--Master-Data-Services-.md)   
 [Business Rules &#40;Master Data Services&#41;](../../Topics\TopicNameNotContainA/Business-Rules--Master-Data-Services-.md)   
 [Validate Specific Members against Business Rules &#40;Master Data Services&#41;](../../Topics\TopicNameNotContainA/Validate-Specific-Members-against-Business-Rules--Master-Data-Services-.md)  
  
  