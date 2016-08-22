---
title: "Creating Windows Phone applications with System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 866113ff-efd0-40d2-ac3a-2edd49732a24
caps.latest.revision: 10
author: barlanmsft
---
# Creating Windows Phone applications with System Center Configuration Manager
In addition to the other [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] requirements and procedures for creating an application, you must also take the following considerations into account when you create and deploy applications for Windows Phone devices.  
  
## General considerations  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] supports deploying the following app types:  
  
|Device Type|Supported Files|  
|-----------------|---------------------|  
|Windows Phone 8|*.xap|  
|Windows Phone 8.1|*.xap, \*.appx, \*.appxbundle|  
  
 The following deployment actions are supported:  
  
|Device type|Supported actions|  
|-----------------|-----------------------|  
|Windows Phone 8 and Windows Phone 8.1|Available, Required, Uninstall|  
  
## Steps to deploy the latest Windows Phone Company Portal app with supersedence  
 The following table provides the steps, details, and more information for creating and deploying the latest Windows Phone 8 company portal app.  
  
|Step|More Information|  
|----------|----------------------|  
|**Step 1:** Get the latest company portal app.|Download the [Windows Phone 8 company portal app](http://go.microsoft.com/fwlink/?LinkId=268440).|  
|**Step 2:** Sign the company portal app with your Symantec certificate.|For information on how to sign the company portal app, see [Set up Windows Phone and Windows 10 Mobile hybrid device management with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Set-up-Windows-Phone-and-Windows-10-Mobile-hybrid-device-management-with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).|  
|**Step 3:** Create a new application with the latest version of the company portal app and specify a supersedence relationship.|For more information, see [How to create applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-create-applications-with-System-Center-Configuration-Manager.md) and [How to revise and supersede applications in System Center Configuration Manager](../System Center Configuration Manager/How-to-revise-and-supersede-applications-in-System-Center-Configuration-Manager.md).|  
|**Step 4:** Add the application to the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] Subscription Wizard.|Add the application Windows Phone 8 page of the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] Subscription Wizard. For more information, see [Set up Windows Phone and Windows 10 Mobile hybrid device management with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Set-up-Windows-Phone-and-Windows-10-Mobile-hybrid-device-management-with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).|  
|**Step 5:** Delete the deployment that is automatically created when you added the company portal app to the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] Subscription Wizard.|The [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] subscription has created an automatic deployment of this app, as this deployment will not support supersedence.|  
|**Step 6:** Create a new deployment of the application and check **Automatically upgrade any superceded versions of this application** on the **Deployment Settings** page of the **Deploy Software Wizard**.|Create a new deployment with supersedence using the application you created with the supersedence relationship.|  
|**Step 7 (Optional):** The superseding apps would install on devices after 7 days by default. To deploy the company portal app sooner to previously enrolled devices, you can change the **schedule re-evaluation for deployments** setting to a lower value.<br /><br /> If you sett this value to a lower value than the default, it might negatively affect the performance of your network and client computers.|For more information, see [Deploy and manage applications with System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-applications-with-System-Center-Configuration-Manager.md).|  
  
## See Also  
 [Deploy and manage applications with System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-applications-with-System-Center-Configuration-Manager.md)