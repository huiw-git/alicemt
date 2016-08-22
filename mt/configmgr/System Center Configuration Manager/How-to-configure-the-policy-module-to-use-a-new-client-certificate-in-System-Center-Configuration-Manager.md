---
title: "How to configure the policy module to use a new client certificate in System Center Configuration Manager"
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
ms.assetid: 4f27b819-f43a-4dc8-847a-a81d8c880e5d
caps.latest.revision: 4
caps.handback.revision: 0
---
# How to configure the policy module to use a new client certificate in System Center Configuration Manager
Servers that are running the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Policy Module with the Network Device Enrollment Service role service use a client certificate to authenticate the Policy Module to the certificate registration point site system server in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. Typically, a client authentication certificate is valid for one year. Before the certificate expires, renew it, update the registry for the new certificate, and then restart the web server that runs the Network Device Enrollment Service.  
  
> [!NOTE]  
>  If the certificate has already expired, **“ERROR("Failed to send http request <thumbprint\>. Error 12037",** appears in the NDESPlugin.log file on the server that runs the Network Device Enrollment Service. In the error message, *<thumbprint\>* is replaced with the certificate thumbprint of the expired certificate.  
  
 To renew the certificate:  
  
-   If you manually requested this client certificate, manually request a new certificate. If you need help deploying this certificate, you can use the instructions for [Exporting the Client Certificate for Distribution Points](../Topic/Step-by-step%20example%20deployment%20of%20the%20PKI%20certificates%20for%20System%20Center%20Configuration%20Manager:%20Windows%20Server%202008%20Certification%20Authority.md#BKMK_exportclientdistributionpoint22008) in the [Step-by-step example deployment of the PKI certificates for System Center Configuration Manager: Windows Server 2008 Certification Authority](../Topic/Step-by-step%20example%20deployment%20of%20the%20PKI%20certificates%20for%20System%20Center%20Configuration%20Manager:%20Windows%20Server%202008%20Certification%20Authority.md) topic, with one exception: Do not select the **Allow private key to be exported** check box on the **Request Handling** tab of the certificate template properties.  
  
-   If you automatically deployed this client certificate by using Group Policy enrollment, the default configuration is to automatically request a new certificate before the original certificate expires.  
  
 After the new certificate is deployed on the server that runs the Network Device Enrollment Service and the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Policy Module, use the following procedure to configure the server to use the new certificate.  
  
### To configure the Policy Module to use the new client certificate  
  
1.  On the server that runs the Network Device Enrollment Service and the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] Policy Module, open the registry editor and replace the old certificate thumbprint with the new certificate thumbprint by using the following registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\Modules\NDESPolicy\NDESCertThumbprint.  
  
    > [!TIP]  
    >  To identify the thumbprint for the new certificate, locate the certificate in the Computer store by using the Certificates snap-in. Then, right-click the certificate, click **Properties**, click **View Certificate**, click the **Details** tab, and then scroll and select **Thumbprint**. You will then see and be able to copy the string of hexadecimal characters that is the certificate thumbprint for this certificate.  
  
2.  Restart the services for the web server by using one of the following methods:  
  
    1.  From Internet Information Services (IIS) Manager: Browse to the web server node in the tree. In the **Actions** pane, click **Restart**.  
  
    2.  From the command line: Type **iisreset /restart** and press Enter.  
  
     For more information, see [Start or Stop the Web Server (IIS 8)](http://go.microsoft.com/fwlink/p/?LinkId=320507) in the Windows Server library on TechNet.  
  
 You can confirm that the Policy Module is using the new certificate by checking for the following entry in the NDESPlugin.log file on the server that runs the Network Device Enrollment Service: **INFO("NDES thumbprint is <thumbprint\>.", wszBuffer);**  
  
## See Also  
 [Certificate profiles technical reference for System Center Configuration Manager](../System Center Configuration Manager/Certificate-profiles-technical-reference-for-System-Center-Configuration-Manager.md)