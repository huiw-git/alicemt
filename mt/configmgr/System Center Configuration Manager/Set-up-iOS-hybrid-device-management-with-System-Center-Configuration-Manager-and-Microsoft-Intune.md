---
title: "Set up iOS hybrid device management with System Center Configuration Manager and Microsoft Intune"
ms.custom: na
ms.date: 2016-03-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 5eae4400-58ca-4c71-804c-6a585cd3df5d
caps.latest.revision: 10
caps.handback.revision: 0
---
# Set up iOS hybrid device management with System Center Configuration Manager and Microsoft Intune
With [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)], you can enable BYOD ("bring your own device") iOS and Mac OS X device enrollment to give access to company email and resources to iPhone, iPad and Mac users. Once users install the Intune company portal app, their devices can be targeted with policy. Before you can manage iOS and Mac devices, you must import an Apple Push Notification service (APNs) certificate from Apple. This certificate allows Intune to manage iOS and Mac devices and establishes an accredited and encrypted IP connection with the mobile device management authority services.  
  
 You can also enroll corporate-owned iOS devices.  See [Corporate-owned device (COD) management using Configuration Manager with Microsoft Intune](../System Center Configuration Manager/Corporate-owned-device--COD--management-using-Configuration-Manager-with-Microsoft-Intune.md).  
  
## Enable iOS device enrollment  
 To support enrollment of iOS  devices, you must follow these steps:  
  
#### Set up iOS device enrollment in Configuration Manager  
  
1.  **Prerequisites** - Before you can set up enrollment for any platform, complete the prerequisites and procedures in [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](../System Center Configuration Manager/Hybrid-mobile-device-management--MDM--with-System-Center-Configuration-Manager-and-Microsoft-Intune.md).  
  
2.  **Download a certificate signing request** - A certificate signing request file (.csr) is required to request an APNs certificate from Apple.  
  
    1.  In the Configuration Manager console in the **Administration** workspace, go to **Cloud Services**> **Microsoft Intune Subscriptions**.  
  
    2.  On the **Home** tab, click **Create APNs certificate request**. The **Request Apple Push Notification Service Certificate Signing Request** dialog box opens.  
  
    3.  **Browse** to the path to save the new certificate signing request (.csr) file. Save the certificate signing request (.csr) file locally.  
  
    4.  Click **Download**. The new Microsoft Intune .csr file downloads and is saved by Configuration Manager. The .csr file is used to request a trust relationship certificate from the Apple Push Certificates Portal.  
  
3.  **Request an APNs certificate from Apple** - The Apple Push Notification service (APNs) certificate is used to establish a trust relationship between the management service, Intune, and enrolled iOS mobile devices.  
  
    1.  In a browser, go to the [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) and sign in with your company Apple ID. This Apple ID must be used in future to renew your APNs certificate.  
  
    2.  Complete the wizard using the certificate signing request (.csr) file. Download the APNs certificate and save the .pem file locally. This APNs certificate (.pem) file is used to establish a trust relationship between the Apple Push Notification server and Intune’s mobile device management authority.  
  
4.  **Enable enrollment and upload the APNs certificate** - To enable iOS enrollment, upload the APNs certificate.  
  
    1.  In the Configuration Manager console in the **Administration** workspace, go to **Cloud Services** > **Microsoft Intune Subscription**.  
  
    2.  On the **Home** tab in the **Subscription** group, click **Configure Platforms** > **iOS**.  
  
        > [!NOTE]  
        >  Do not upload the Apple Push Notification service (APNs) certificate until you enable iOS enrollment in the Configuration Manager console.  
  
    3.  In the **Microsoft Intune Subscription Properties** dialog box, select the **iOS** tab and click to select the **Enable iOS enrollment** checkbox.  
  
    4.  Click **Browse**, and go to the APNs certificate (.cer) file downloaded from Apple. Configuration Manager displays the APNs certificate information. Click **OK** to save the APNs certificate to Intune.  
  
 Once you're set up, you'll need to let your users know how to enroll their devices. See [What to tell users about enrolling their devices](https://technet.microsoft.com/library/dn948527.aspx). This information applies to both Microsoft Intune and Configuration Manager-managed mobile devices.