---
title: "Set up a Microsoft Intune subscription for On-premises Mobile Device Management in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
caps.latest.revision: 8
caps.handback.revision: 0
---
# Set up a Microsoft Intune subscription for On-premises Mobile Device Management in System Center Configuration Manager
[!INCLUDE[onprem_first](../System Center Configuration Manager/itokens/onprem_first_md.md)] requires a [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] subscription to track licensing. The [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] service is not used to manage the devices or to store management information. For [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)], all device management is handled by the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure.  
  
> [!IMPORTANT]  
>  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support using both [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] and on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure as management authorities at the same time. So when you set up the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription for on-premises management, you effectively disable [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] management.  
  
 Setting up the  [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] service to work with  [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] involves the following high-level steps:  
  
-   [Sign up for Microsoft Intune](#bkmk_signup)  
  
-   [Add the Intune subscription to Configuration Manager](#bkmk_addSub)  
  
-   [Configure the Intune subscription for On-premises Mobile Device Management](#bkmk_configure)  
  
> [!TIP]  
>  We recommend that you set up the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] before you install the required site system roles to minimize the time required for the newly installed site system roles to become functional.  
  
##  <a name="bkmk_signup"></a> Sign up for Microsoft Intune  
 [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] is required to make [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] functional. Simply [sign up](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/) for a trial or paid subscription and go to the next step to add the subscription to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
##  <a name="bkmk_addSub"></a> Add the Intune subscription to Configuration Manager  
 To add the subscription to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you follow the same basic steps as you would when adding the subscription for mobile device management with  [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]. Read the notes below for specific differences , and then use the instructions in [To create the Microsoft Intune subscription](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md#bkmk_subscription) in [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).  
  
> [!NOTE]  
>  When adding the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription, keep the following in mind:  
>   
>  -   The collection specified in the Add Microsoft Intune Subscription Wizard is not used for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] user right delegation. It is only used for mobile device management with [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]. However, you are required to specify a collection for the wizard to proceed.  
> -   The site code setting specified in the wizard is ignored for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)]. The site code that is used is the one you specify in the enrollment profile that grants users permission to enroll devices.  
> -   Do not enable multi factor authentication. It is not supported in [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)].  
  
##  <a name="bkmk_configure"></a> Configure the Intune subscription for On-premises Mobile Device Management  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, right-click  the **Microsoft Intune Subscription**, and click **Properties**.  
  
2.  In the On Premises Mobile Device Management box, click the check box next to **Only manage devices on-premises**, and click **OK**.  
  
    > [!NOTE]  
    >  By clicking this check box, you configure the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription to keep all management information on-premises and not replicate data to the cloud.  
  
3.  If you plan to manage Windows 10 Mobile devices, right-click the **Microsoft Intune Subscription**, click **Configure Platforms**, and then click  **Windows Phone**.  
  
4.  Click the check box next to **Windows Phone 8.1 and Windows 10 Mobile**, and then click **OK**.  
  
5.  If you plan to manage Windows 10 desktop computers, right-click the **Microsoft Intune Subscription**, click **Configure Platforms**, and then click **Enable Windows Enrollment**.  
  
6.  Click the check box next to **Enable Windows enrollment**, and then click **OK**.  
  
## See Also  
 [Preparation steps for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Preparation-steps-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)