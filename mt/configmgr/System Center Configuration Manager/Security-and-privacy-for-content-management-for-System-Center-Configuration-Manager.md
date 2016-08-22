---
title: "Security and privacy for content management for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 5f38b726-dc00-433a-ba05-5b7dbb0d8e99
caps.latest.revision: 8
---
# Security and privacy for content management for System Center Configuration Manager
This topic contains security and privacy information for content management in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. Read it in conjunction with the following topics:  
  
-   [Security and privacy for application management in System Center Configuration Manager](../System Center Configuration Manager/Security-and-privacy-for-application-management-in-System-Center-Configuration-Manager.md)  
  
-   [Security and privacy for software updates in System Center Configuration Manager](../System Center Configuration Manager/Security-and-privacy-for-software-updates-in-System-Center-Configuration-Manager.md)  
  
-   [Security and privacy for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Security-and-privacy-for-operating-system-deployment-in-System-Center-Configuration-Manager.md)  
  
##  <a name="BKMK_Security_ContentManagement"></a> Security best practices for content management  
 Use the following security best practices for content management:  
  
 **For distribution points on the intranet, consider the advantages and disadvantages of using HTTPS and HTTP** - In most scenarios, using HTTP and package access accounts for authorization provides more security than using HTTPS with encryption but without authorization. However, if you have sensitive data in your content that you want to encrypt during transfer, use HTTPS.  
  
-   **When you use HTTPS for a distribution point**, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not use package access accounts to authorize access to the content, but the content is encrypted when it transferred over the network.  
  
-   **When you use HTTP for a distribution point**, you can use package access accounts for authorization, but the content is not encrypted when it is transferred over the network.  
  
 **If you use a PKI client authentication certificate rather than a self-signed certificate for the distribution point, protect the certificate file (.pfx) with a strong password. If you store the file on the network, secure the network channel when you import the file into [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]** - When you require a password to import the client authentication certificate that you use for the distribution point to communicate with management points, this helps to protect the certificate from an attacker. Use SMB signing or IPsec between the network location and the site server to prevent an attacker from tampering with the certificate file.  
  
 **Remove the distribution point role from the site server** - By default, a distribution point is installed on the same server as the site server. Clients do not have to communicate directly with the site server, so to reduce the attack surface, assign the distribution point role to other site systems and remove it from the site server.  
  
 **Secure content at the package access level** -  The distribution point share allows Read access to all users. To restrict which users can access the content, use package access accounts when the distribution point is configured for HTTP. This does not apply to cloud-based distribution points,  which do not support package access accounts. For more information about the Package Access Account, see [Manage accounts to access content](../System Center Configuration Manager/Manage-accounts-to-access-content-in-System-Center-Configuration-Manager.md).
 
  
 **If [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installs IIS when you add a distribution point site system role, remove HTTP Redirection and IIS Management Scripts and Tools when the distribution point installation is complete** - The distribution point does not require HTTP Redirection and IIS Management Scripts and Tools. To reduce the attack surface, remove these role services for the web server (IIS) role.  For more information about the role services for the web server (IIS) role for distribution points, see   [Supported operating systems for sites and clients for System Center Configuration Manager](../Topic/Supported%20operating%20systems%20for%20sites%20and%20clients%20for%20System%20Center%20Configuration%20Manager.md).  
  
 **Set package access permissions when you create the package** -  Because changes to the access accounts on the package files become effective only when you redistribute the package, set the package access permissions carefully when you first create the package. This is particularly important when the package is large or distributed to many distribution points, and when the network bandwidth capacity for content distribution is limited.  
  
 **Implement access controls to protect media that contains prestaged content** - Prestaged content is compressed but not encrypted. An attacker could read and modify the files that are then downloaded to devices. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients will reject content that is tampered with, but they still download it.  
  
 **Import prestaged content by using only the ExtractContent command-line tool (ExtractContent.exe) that is supplied with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and make sure that is signed by Microsoft** -  To avoid tampering and elevation of privileges, use only the authorized command-line tool that is supplied with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 **Secure the communication channel between the site server and the package source location** - Use IPsec or SMB signing between the site server and the package source location for when you create applications and packages. This helps to prevent an attacker from tampering with the source files.  
  
 **If you change the site configuration option to use a custom website rather than the default website after any distribution point roles are installed, remove the default virtual directories** - When you change from using the default website to using a custom website, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not remove the old virtual directories. Remove the virtual directories that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] originally created under the default website:  
  
-   SMS_DP_SMSPKG$  
  
-   SMS_DP_SMSSIG$  
  
-   NOCERT_SMS_DP_SMSPKG$  
  
-   NOCERT_SMS_DP_SMSSIG$  
  
 **For cloud-based distribution points, protect your subscription details and certificates** - When you use cloud-based distribution points, protect high-value items including the user name and password for your  Azure subscription, the Azure management certificate, and the cloud-based distribution point service certificate. Store the certificates securely and if you browse to them over the network when you configure the cloud-based distribution point, use IPsec or SMB signing between the site system server and the source location.  
  
 **For cloud-based distribution points: For service continuity, monitor the expiry date of the certificates** -   
                [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not warn you when the imported certificates for management of the cloud-based distribution point service is about to expire. You must monitor the expiry dates independently from [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and make sure that you renew and then import the new certificate before the expiry date. This is particularly important if you purchase a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cloud-based distribution point service certificate from an external certification authority (CA), because you might need additional time to obtain a renewed certificate.  
  
 If either certificate expires, **Cloud Services Manager** generates the status message ID **9425** and the **CloudMgr.log** file contains an entry to indicate that the certificate **is in expired state**, with the expiry date also logged in UTC.  
  
## Security considerations for content management  
Consider the folowing when planning for content management:  
  
-   Clients do not validate content until after it is downloaded  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients validate the hash on content only after it is downloaded to their client cache. If an attacker tampers with the list of files to download or with the content itself, the download process can take up considerable network bandwidth for the client to then discard the content when it encounters the invalid hash.  
  
-   When you use cloud-based distribution points, access to the content is automatically restricted to your enterprise and you cannot restrict it further to selected users or groups.  
  
-   When you use cloud-based distribution points, clients are authenticated by the management point and then use a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] token to access cloud-based distribution points. The token is valid for 8 hours so if you block a client because it is no longer trusted, it can continue to download content from a cloud-based distribution point until the validity period of this token is expired. At this point, the management point will not issue another token for the client because the client is blocked.  
  
     To avoid a blocked client from downloading content within this 8 hour window, you can stop the cloud service from the **Cloud** node, **Hierarchy Configuration**, in the **Administration** workspace in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
##  <a name="BKMK_Privacy_ContentManagement"></a> Privacy information for content management  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] does not include any user data in content files, although an administrative user might choose to do this.  
  
 Before you configure content management, consider your privacy requirements.  
    
## See Also  
 [Fundamental concepts for content management in System Center Configuration Manager](../System Center Configuration Manager/Fundamental-concepts-for-content-management-in-System-Center-Configuration-Manager.md)   
 [Security and privacy for System Center Configuration Manager](../System Center Configuration Manager/Security-and-privacy-for-System-Center-Configuration-Manager.md)