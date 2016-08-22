---
title: "How users enroll devices with On-premises Mobile Device Management in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
caps.latest.revision: 9
caps.handback.revision: 0
---
# How users enroll devices with On-premises Mobile Device Management in System Center Configuration Manager
With [!INCLUDE[onprem_first](../System Center Configuration Manager/itokens/onprem_first_md.md)], users can enroll devices if they have been granted enrollment permission (by way of updated client settings), and their devices have the required root certificate installed to have trusted communications with the servers hosting the required site system roles. For more information on how to set up enrollment, see [Set up device enrollment for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Set-up-device-enrollment-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md).  
  
 [!INCLUDE[onprem_devices](../System Center Configuration Manager/itokens/onprem_devices_md.md)] The following tasks explain how to enroll and verify enrollment of computers and devices for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)]:  
  
-   [Enroll a Windows 10 computer](#bkmk_enrollDesk)  
  
-   [Enroll a Windows 10 Mobile device](#bkmk_enrollMob)  
  
-   [Verify device enrollment](#bkmk_verify)  
  
##  <a name="bkmk_enrollDesk"></a> Enroll a Windows 10 computer  
  
1.  On a Windows 10 computer, go to **Settings**.  
  
2.  Click **Accounts**, and then click **Work access**.  
  
3.  In Work Access under **Connect to work or school**, click **Connect**, enter your work email address, and click **Continue**.  
  
4.  Enter the FQDN of the server hosting the enrollment proxy point site system role, and click **Continue**.  
  
5.  In Connecting to a service, enter your work email password, and click **Sign in**.  
  
6.  Click **Skip** for remembering the sign-in info, and after a short time the device is connected.  
  
##  <a name="bkmk_enrollMob"></a> Enroll a Windows 10 Mobile device  
  
1.  On a Windows 10 Mobile device, go to **Settings**.  
  
2.  Click **Accounts**, and then click **Work access**.  
  
3.  Click **Connect**.  
  
4.  Enter your work email address and the FQDN of the server hosting the enrollment proxy point site system role. Click **Connect**.  
  
5.  On the next screen, enter your work email address and password, and then click **Sign-in**. After a short time,  the device is enrolled. Click **Done**.  
  
##  <a name="bkmk_verify"></a> Verify device enrollment  
 You can verify that devices have been successfully enrolled in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
1.  Start the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
2.  Click **Assets and Compliance** > **Overview** > **Devices**. The enrolled device appears in the list.  
  
## See Also  
 [Enroll devices for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Enroll-devices-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)