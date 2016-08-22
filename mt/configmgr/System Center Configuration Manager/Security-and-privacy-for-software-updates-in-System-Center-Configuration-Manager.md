---
title: "Security and privacy for software updates in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 41d6d5d8-ba84-4efb-b105-4d1eed239824
caps.latest.revision: 6
---
# Security and privacy for software updates in System Center Configuration Manager
This topic contains security and privacy information for software updates in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
##  <a name="BKMK_Security_HardwareInventory"></a> Security best practices for software updates  
 Use the following security best practices when you deploy software updates to clients:  
  
-   Do not change the default permissions on software update packages.  
  
     By default, software update packages are set to allow administrators **Full Control** and users to have **Read** access. If you change these permissions, it might allow an attacker to add, remove, or delete software updates.  
  
-   Control access to the download location for software updates.  
  
     The computer accounts for the SMS Provider, the site server, and the administrative user who will actually download the software updates to the download location require **Write** access to the download location. Restrict access to the download location to reduce the risk of attackers tampering with the software updates source files in the download location.  
  
     In addition, if you use a UNC share for the download location, secure the network channel by using IPsec or SMB signing to prevent tampering of the software updates source files when they are transferred over the network.  
  
-   Use UTC for evaluating deployment times.  
  
     If you use local time instead of UTC, users could potentially delay installation of software updates by changing the time zone on their computers  
  
-   Enable SSL on WSUS and follow the best practices for securing Windows Server Update Services (WSUS).  
  
     Identify and follow the security best practices for the version of WSUS that you use with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
    > [!IMPORTANT]  
    >  If you configure the software update point to enable SSL communications for the WSUS server, you must configure virtual roots for SSL on the WSUS server.  
  
-   Enable CRL checking.  
  
     By default, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not check the certificate revocation list (CRL) to verify the signature on software updates before they are deployed to computers. Checking the CRL each time a certificate is used offers more security against using a certificate that has been revoked, but it introduces a connection delay and incurs additional processing on the computer performing the CRL check.  
  
     For more information about how to enable CRL checking for software updates, see [How to enable CRL checking for software updates in System Center Configuration Manager](../System Center Configuration Manager/How-to-enable-CRL-checking-for-software-updates-in-System-Center-Configuration-Manager.md).  
  
-   Configure WSUS to use a custom website.  
  
     When you install WSUS on the software update point, you have the option to use the existing IIS Default Web site or to create a custom WSUS website. Create a custom website for WSUS so that IIS hosts the WSUS services in a dedicated virtual website instead of sharing the same web site that is used by the other [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site systems or other applications.  
  
     For more information, see [Configure WSUS to use a custom web site](../System Center Configuration Manager/Plan-for-software-updates-in-System-Center-Configuration-Manager.md#BKMK_CustomWebSite).  
  
##  <a name="BKMK_Privacy_HardwareInventory"></a> Privacy information for Software Updates  
 Software updates scans your client computers to determine which software updates you require, and then sends that information back to the site database. During the software updates process, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] might transmit information between clients and servers that identify the computer and logon accounts.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] maintains state information about the software deployment process. State information is not encrypted during transmission or storage. State information is stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database and it is deleted by the database maintenance tasks. No state information is sent to Microsoft.  
  
 The use of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] software updates to install software updates on client computers might be subject to software license terms for those updates, which is separate from the Software License Terms for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. Always review and agree to the Software Licensing Terms prior to installing the software updates by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not implement software updates by default and requires several configuration steps before information is collected.  
  
 Before you configure software updates, consider your privacy requirements.  
  
## See Also  
 [Deploy and manage software updates in System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-software-updates-in-System-Center-Configuration-Manager.md)