---
title: Configure Business Rules to Send Notifications (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
---
# Configure Business Rules to Send Notifications (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], configure business rules to send notifications when you want to notify users about attribute value changes.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** and **User and Group Permissions** functional areas. If you do not have permission to the **User and Group Permissions** functional area, you cannot view the list of users and groups to send notifications to.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   A business rule that uses a validation action must already exist. For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../Topic/Create%20and%20Publish%20a%20Business%20Rule%20\(Master%20Data%20Services\).md).  
  
-   The user or group that receives the notification must have at least **Read\-only** permission to the attribute that fails validation. Users or groups that are explicitly or implicitly denied permission to the attribute will receive the email but will not be able to access the attribute in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].  
  
-   If mail is sent to a group, only members of the group that have accessed [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] will get the email.  
  
### To configure business rules to send notifications  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  From the menu bar, point to **Manage** and click **Business Rules**.  
  
3.  On the **Business Rules** page, from the **Model** list, select a model.  
  
4.  From the **Entity** drop\-down list, select an entity.  
  
5.  From the **Member Types** drop\-down list, select a type of member.  
  
6.  In the grid, select the row for the business rule you want to edit and click **Edit**.  
  
7.  Select the **Send Notifications** check\-box and from the drop\-down list select a user or group to send the email notification to.  
  
8.  Click **Save**.  
  
9. Click **Publish All**.  
  
10. On the confirmation dialog box, click **OK**. The value in the **Business Rule State** column changed to **Active** and the **Notification** column shows the selected user or group to send notification to.  
  
## Next Steps  
  
-   Apply business rules to data by following one of these procedures:  
  
    -   [Validate Specific Members against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20Specific%20Members%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)  
  
    -   [Validate a Version against Business Rules &#40;Master Data Services&#41;](../Topic/Validate%20a%20Version%20against%20Business%20Rules%20\(Master%20Data%20Services\).md)  
  
-   Configure the email protocol as follows:  
  
    -   [Configure Email Notifications &#40;Master Data Services&#41;](../Topic/Configure%20Email%20Notifications%20\(Master%20Data%20Services\).md)  
  
## See Also  
 [Notifications &#40;Master Data Services&#41;](../Topic/Notifications%20\(Master%20Data%20Services\).md)   
 [Configure Email Notifications &#40;Master Data Services&#41;](../Topic/Configure%20Email%20Notifications%20\(Master%20Data%20Services\).md)  
  
  