---
title: My Settings for Power BI Integration (web portal)
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
---
# My Settings for Power BI Integration (web portal)
  The **My Settings** page in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] [!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)] is used by individual users to manage their sign\-in with [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)]. When you  go through the steps to pin a report item, you will automatically be prompted to sign.  However,  you can use the **My Settings** page if you need to manually sign in or if you need to sign out.  If the **My Settings** menu option is not visible, the report server has not been integrated with  [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)].  For more information, see [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md).  
  
![ssRS_WebPortal_MySettings](../../Images\Image\ImageNotContaina/ssRS_WebPortal_MySettings.png)  
  
## Why Sign\-in  
 When you sign in, you establish a relationship between your [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] user account and  your [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] account.  The sign\-in creates a security token that is good for 90 days. If the token expires, and you have items pinned to Power BI, you will see a notification.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../../Images\Image\ImageNotContaina/ssRS_WebPortal_PowerBI_Notification.png)    
   
Tiles within [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] dashboards will not refresh until you sign in again through **MySettings**.  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../../Images\Image\ImageNotContaina/ssRS_WebPortal_PowerBI_SignIn_Again.png)  
  
Once you sign in, a new security token will be created.  Your dashboard tiles will begin updating on their previously configured schedules.  
  
## See Also  
 [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md)   
 [Pin Reporting Services items to Power BI Dashboards](../../Topics\TopicNameNotContainA/Pin-Reporting-Services-items-to-Power-BI-Dashboards.md)   
 [Dashboards in Power BI](https://support.powerbi.com/knowledgebase/articles/424868-dashboards-in-power-bi)  
  
  