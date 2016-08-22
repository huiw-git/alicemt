---
title: "About client installation properties published to Active Directory Domain Services in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 101d7d4d-92db-419d-b2ae-3c1c1dea68e9
caps.latest.revision: 6
caps.handback.revision: 0
---
# About client installation properties published to Active Directory Domain Services in System Center Configuration Manager
When you extend the Active Directory schema for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] and the site is published to Active Directory Domain Services, many client installation properties are published to Active Directory Domain Services. If a computer can locate these client installation properties, it can use them during [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client deployment.  
  
 The advantages of using Active Directory Domain Services to publish client installation properties include the following:  
  
-   Software update point-based client installation and Group Policy client installations do not require setup parameters to be provisioned on each computer.  
  
-   Because this information is automatically generated, the risk of human error associated with manually entering installation properties is eliminated.  
  
> [!NOTE]  
>  For more information about how to extend the Active Directory schema for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and how to publish a site, see [Prepare your network environment for System Center Configuration Manager](../System Center Configuration Manager/Prepare-your-network-environment-for-System-Center-Configuration-Manager.md).  
  
 Client installation (CCMSetup) uses the client installation properties that are published to Active Directory Domain Services only if no other properties are specified by using any of the following methods:  
  
-   Manual installation  
  
-   Provisioning client installation properties by using Group Policy  
  
> [!NOTE]  
>  The client installation properties are used to install the client and might be overwritten with new settings from its assigned site after the client is installed and has successfully assigned to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
 Use the details in the following sections to determine which [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client installation methods use Active Directory Domain Services to obtain client installation properties.  
  
## Client push installation  
 Client push installation does not use Active Directory Domain Services to obtain installation properties.  
  
 Instead, you can specify client.msi installation properties in the **Client** tab of the **Client Push Installation Properties** dialog box. These options and client-related site settings are stored in a file that the client reads during client installation.  
  
> [!NOTE]  
>  You do not have to specify any CCMSetup properties for client push installation, or the fallback status point, or the trusted root key in the **Client** tab. These settings are automatically supplied to clients when they are installed by using client push installation.  
  
 Any client.msi properties that you specify in the **Client** tab are published to Active Directory Domain Services if the site is published to Active Directory Domain Services. These settings are read by client installations where CCMSetup is run with no installation properties.  
  
## Software update point-based installation  
 The software update point-based installation method does not support the addition of installation properties to the CCMSetup command line.  
  
 If no command line properties have been provisioned on the client computer by using Group Policy, CCMSetup searches Active Directory Domain Services for installation properties.  
  
## Group Policy installation  
 The Group Policy installation method does not support the addition of installation properties to the CCMSetup command line.  
  
 If no command line properties have been provisioned on the client computer, CCMSetup searches Active Directory Domain Services for installation properties.  
  
## Manual installation  
 CCMSetup searches Active Directory Domain Services for installation properties under the following circumstances:  
  
-   No command line properties are specified after the CCMSetup.exe command.  
  
-   The computer has not been provisioned with installation properties by using Group Policy.  
  
## Logon script installation  
 CCMSetup searches Active Directory Domain Services for installation properties under the following circumstances:  
  
-   No command line properties are specified after the CCMSetup.exe command.  
  
-   The computer has not been provisioned with installation properties by using Group Policy.  
  
## Software distribution installation  
 CCMSetup searches Active Directory Domain Services for installation properties under the following circumstances:  
  
-   No command line properties are specified after the CCMSetup.exe command.  
  
-   The computer has not been provisioned with installation properties by using Group Policy.  
  
## Installations for clients that cannot access Active Directory Domain Services for published information  
 These clients include:  
  
-   Workgroup computers  
  
-   Clients that are assigned to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that is not published to Active Directory Domain Services  
  
-   Clients that are installed when they are on the Internet  
  
 These client computers cannot read installation properties from Active Directory Domain Services, and so will not be able to access the published installation properties.  
  
## Client installation properties published to Active Directory Domain Services  
 For more information about each  item listed below, see [About client installation properties in System Center Configuration Manager](../System Center Configuration Manager/About-client-installation-properties-in-System-Center-Configuration-Manager.md).  
  
-   The [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site code.  
  
-   The site server signing certificate.  
  
-   The trusted root key.  
  
-   The client communication ports for HTTP and HTTPS.  
  
-   The fallback status point. If the site has multiple fallback status points, only the first one that was installed will be published to Active Directory Domain Services.  
  
-   A setting to indicate that the client must communicate by using HTTPS only.  
  
-   Settings related to PKI certificates:  
  
    -   Whether to use a client PKI certificate.  
  
    -   The selection criteria for certificate selection, if this is required because the client has more than one valid PKI certificate that can be used for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
    -   A setting to determine which certificate to use if the client has multiple valid certificates after the certificate selection process.  
  
    -   The certificate issuers list that contains a list of trusted root CA certificates.  
  
-   Client.msi installation properties that are specified in the **Client** tab of the **Client Push Installation Properties** dialog box.  
  
## See Also  
 [Client management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Client-management-technical-reference-for-System-Center-Configuration-Manager.md)