---
title: "How to install certificates on Android devices in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 4036f3d7-6658-4118-9bd0-6c1a3b276f56
caps.latest.revision: 4
caps.handback.revision: 0
---
# How to install certificates on Android devices in System Center Configuration Manager
When certificates are installed on Android devices, the end-user must perform a number of actions in order to accept and install the certificate. It is important to educate your end-users about the actions they might need to take, because if the user does not take the correct action, then the certificate will not be installed correctly.  
  
 The following procedure details the actions that much be taken on Android devices by the end-user to accept and install certificates.  
  
## Certificate installation  
  
#### To install a certificate on an Android device  
  
1.  The user receives a notification, titled **Company Portal**, on the Android device. Click the notification to begin.  
  
2.  In the **Extract from:***<certificate name\>* box, the user is asked to enter a password to extract the certificate. The user must click **OK**, without entering a password.  
  
3.  In the **Certificate name** box, the certificate name is displayed and the user must click **OK** to continue.  
  
    > [!IMPORTANT]  
    >  The user must not edit the certificate name in this box or else the certificate will not function correctly.  
  
4.  In the **Choose certificate** box, the user must click **Allow**, to allow the company portal to use the certificate.  
  
    > [!NOTE]  
    >  The user must not click the **Install** button which allows you to select another certificate from a storage device.  
  
## See Also  
 [Certificate profiles technical reference for System Center Configuration Manager](../System Center Configuration Manager/Certificate-profiles-technical-reference-for-System-Center-Configuration-Manager.md)