---
title: "Plan for On-premises Mobile Device Management in System Center Configuration Manager"
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
ms.assetid: 02979fb8-ea7e-4ec6-b7e0-ecbfda73e52d
caps.latest.revision: 9
caps.handback.revision: 0
---
# Plan for On-premises Mobile Device Management in System Center Configuration Manager
Consider the following requirements before preparing the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure to handle [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)]:  
  
-   [Supported devices](#bkmk_devices)  
  
-   [Use of the Microsoft Intune subscription](#bkmk_intune)  
  
-   [Required site system roles](#bkmk_roles)  
  
-   [Required trusted communications](#bkmk_trustedComs)  
  
-   [Enrollment considerations](#bkmk_enrollment)  
  
##  <a name="bkmk_devices"></a> Supported devices  
 [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] allows you to manage mobile devices using the management capabilities built into the device operating systems.  The management capability is based on the Open Mobile Alliance (OMA) Device Management (DM) standard, and many device platforms use this standard to allow the devices to be managed.  We call these **modern devices** (in the documentation and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console user interface) to distinguish them from other devices that require the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client to manage them.  
  
 [!INCLUDE[onprem_devices](../System Center Configuration Manager/itokens/onprem_devices_md.md)]   
##  <a name="bkmk_intune"></a> Use of the  Microsoft Intune subscription  
 To start using [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)], you will need a [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] subscription. The subscription is only required to track licensing of the devices and is not used to manage or store management information for the devices. All management is handled in your organization's enterprise using the on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure.  
  
> [!IMPORTANT]  
>  [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not support using both [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] and on-premises [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] infrastructure as management authorities at the same time. So when you set up the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription for on-premises management, you effectively disable [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] management.  
  
 If your site has devices with internet connectivity, the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] service can be used to notify devices to  check the device management point for policy updates. This use of  [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] is strictly for notification only of internet-facing devices. Devices without internet connections (and cannot be contacted by [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)]) rely on the configured polling interval to check in with site system roles for management functions.  
  
> [!TIP]  
>  We recommend that you set up the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] before you set up the required site system roles to minimize the time required for the site system roles to become functional.  
  
 For information on how to set up the [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] subscription, see [Set up a Microsoft Intune subscription for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Set-up-a-Microsoft-Intune-subscription-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md).  
  
##  <a name="bkmk_roles"></a> Required site system roles  
 [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] requires at least one of each of the following site system roles:  
  
-   **Enrollment proxy point** to support enrollment requests.  
  
-   **Enrollment point** to support device enrollment.  
  
-   **Device management point** for policy delivery. This site system role is a variation of the management point role that has been configured to allow for mobile device management.  
  
-   **Distribution point** for content delivery.  
  
-   **Service connection point** for connecting to [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)] to notify devices outside the firewall.  
  
 These site system roles can be installed on the single site system server or can be run separately on different servers depending the needs of your organization. Each site system server used for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] must be configured as an HTTPS endpoint for communicating with trusted devices. For more information, see [Required trusted communications](#bkmk_trustedComs).  
  
 For more information on planning for site system roles, see [Plan for site system servers and site system roles for System Center Configuration Manager](../System Center Configuration Manager/Plan-for-site-system-servers-and-site-system-roles-for-System-Center-Configuration-Manager.md).  
  
 For more information on how to add the required site system roles, see [Install site system roles for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Install-site-system-roles-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md).  
  
##  <a name="bkmk_trustedComs"></a> Required trusted communications  
 [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)] requires site system roles to be enabled for HTTPS communications. Depending on your needs, you can use your enterprise's certificate authority (CA) to establish the trusted connections between servers and devices or you could use a publicly available CA to be the trusted authority.  Either way, you will need a web server certificate to be configured with IIS on the site system servers hosting the required site system roles, and you will need the root certificate of that CA installed on the devices that need to connect to those servers.  
  
 If you use your enterprise's CA to establish trusted communications, you need to do the following tasks:  
  
-   Create and issue the web server certificate template on the CA.  
  
-   Request a web server certificate for each site system server hosting a required site system role.  
  
-   Configure IIS on the site system server to use the requested web server certificate.  
  
 For devices joined to the corporate Active Directory domain, the root certificate of the enterprise CA is already available on the device for trusted connections. This means that domain-joined devices (like desktop computers) will automatically be trusted for HTTPS connections with the site system servers. However, non-domain-joined devices (typically mobile) will not have the required root certificate installed. Those devices will require the root certificate to be manually installed on them to successfully communicate with site system servers supporting [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)].  
  
 You must export the root certificate of the issuing CA for use by individual devices. To get the root certificate file, you can export it using the CA, or a simpler method is to use the web server certificate issued by the CA to extract the root and create a root certificate file.   Then, the root certificate must be delivered to the device.  Some example delivery methods include  
  
-   File system  
  
-   Email attachment  
  
-   Memory card  
  
-   Tethered device  
  
-   Cloud storage (such as OneDrive)  
  
-   Near field communication (NFC) connection  
  
-   Barcode scanner  
  
-   Out of box experience (OOBE) provisioning package  
  
 For more information, see [Set up certificates for trusted communications for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Set-up-certificates-for-trusted-communications-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
##  <a name="bkmk_enrollment"></a> Enrollment considerations  
 To enable device enrollment for [!INCLUDE[onprem_next](../System Center Configuration Manager/itokens/onprem_next_md.md)], users must be granted permission to enroll and their devices must be able to have trusted communications with the site system servers hosting the required site system roles.  
  
 Granting user enrollment permission can be accomplished through setting up an enrollment profile in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client settings. You can use the default client settings to push the enrollment profile to all discovered users or you can set up the enrollment profile in custom client settings and push the settings to one or more user collections.  
  
 With user enrollment permission granted, users can enroll their own devices. To get enrolled, the user's device must have the root certificate of the certification authority (CA) that issued the web server certificate used on the site system servers hosting the required site system roles.  
  
 As an alternative to user-initiated enrollment, you can set up a bulk enrollment package that allows the device to be enrolled without user intervention. This package can be delivered to the device before it is initially provisioned for use or after the device goes through its OOBE process.  
  
 For more information on how to set up and enroll devices, see  
  
-   [Set up device enrollment for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Set-up-device-enrollment-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
-   [Enroll devices for On-premises Mobile Device Management in System Center Configuration Manager](../System Center Configuration Manager/Enroll-devices-for-On-premises-Mobile-Device-Management-in-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Manage mobile devices with on-premises infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Manage-mobile-devices-with-on-premises-infrastructure-in-System-Center-Configuration-Manager.md)