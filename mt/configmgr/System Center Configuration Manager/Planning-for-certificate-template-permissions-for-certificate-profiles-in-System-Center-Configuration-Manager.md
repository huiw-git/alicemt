---
title: "Planning for certificate template permissions for certificate profiles in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: eab0e09d-b09e-4c14-ab14-c5f87472522e
caps.latest.revision: 5
caps.handback.revision: 0
---
# Planning for certificate template permissions for certificate profiles in System Center Configuration Manager
The following information can help you plan for how to configure permissions for the certificate templates that [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] uses when you deploy certificate profiles.  
  
## Default Security Permissions and Considerations  
 The default security permissions that are required for the certificate templates that [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] will use to request certificates for users and devices are as follows:  
  
-   Read and Enroll for the account that the Network Device Enrollment Service application pool uses  
  
-   Read for the account that runs the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console  
  
 For more information about these security permissions, see [Step 1: Install and Configure the Network Device Enrollment Service and Dependencies](../System Center Configuration Manager/Configuring-certificate-profiles-in-System-Center-Configuration-Manager.md#BKMK_Step1) in [Configuring certificate profiles in System Center Configuration Manager](../System Center Configuration Manager/Configuring-certificate-profiles-in-System-Center-Configuration-Manager.md).  
  
 When you use this default configuration, users and devices cannot directly request certificates from the certificate templates and all requests must be initiated by the Network Device Enrollment Service. This is an important restriction, because these certificate templates must be configured with **Supply in the request** for the certificate Subject, which means that there is a risk of impersonation if a rogue user or a compromised device requests a certificate. In the default configuration, the Network Device Enrollment Service must initiate such a request. However, this risk of impersonation remains if the service that runs the Network Device Enrollment Service is compromised. To help avoid this risk, follow all security best practices for the Network Device Enrollment Service and the computer that runs this role service.  
  
 If the default security permissions do not fulfill your business requirements, you have another option for configuring the security permissions on the certificate templates: You can add Read and Enroll permissions for users and computers.  
  
## Adding Read and Enroll Permissions for Users and Computers  
 Adding Read and Enroll permissions for users and computers might be appropriate if a separate team manages your certification authority (CA) infrastructure team, and that separate team wants [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] to verify that users have a valid Active Directory Domain Services account before sending them a certificate profile to request a user certificate. For this configuration, you must specify one or more security groups that contain the users, and then grant those groups Read and Enroll permissions on the certificate templates. In this scenario, the CA administrator manages the security control.  
  
 You can similarly specify one or more security groups that contain computer accounts and grant these groups Read and Enroll permissions on the certificate templates. If you deploy a computer certificate profile to a computer that is a domain member, the computer account of that computer must be granted Read and Enroll permissions. These permissions are not required if the computer is not a domain member—for example, if it is a workgroup computer or personal mobile device.  
  
 Although this configuration uses an additional security control, we do not recommend it as a best practice. The reason is that the specified users or owners of the devices might request certificates independently from [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] and supply values for the certificate Subject that might be used to impersonate another user or device.  
  
 In addition, if you specify accounts that cannot be authenticated at the time that the certificate request occurs, the certificate request will fail by default. For example, the certificate request will fail if the server that is running the Network Device Enrollment Service is in an Active Directory forest that is untrusted by the forest that contains the certificate registration point site system server. You can configure the certificate registration point to continue if an account cannot be authenticated because there is no response from a domain controller. However, this is not a security best practice.  
  
 Note that if the certificate registration point is configured to check for account permissions and a domain controller is available and rejects the authentication request (for example, the account is locked out or has been deleted), the certificate enrollment request will fail.  
  
#### To check for Read and Enroll permissions for users and domain-member computers  
  
1.  On the site system server that hosts the certificate registration point, create the following DWORD registry key to have a value of 0: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheck  
  
2.  If an account cannot be authenticated because there is no response from a domain controller, and you want to bypass the permissions check:  
  
    -   On the site system server that hosts the certificate registration point, create the following DWORD registry key to have a value of 1: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheckOnlyIfAccountAccessDenied  
  
3.  On the issuing CA, on the **Security** tab in the properties for the certificate template, add one or more security groups to grant the user or device accounts Read and Enroll permissions.  
  
## See Also  
 [Planning for certificate profiles in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-certificate-profiles-in-System-Center-Configuration-Manager.md)