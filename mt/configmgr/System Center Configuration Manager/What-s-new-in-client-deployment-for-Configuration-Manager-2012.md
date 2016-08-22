---
title: "What&#39;s new in client deployment for Configuration Manager 2012"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89766eeb-0c01-4154-a4a0-1eb779113756
caps.latest.revision: 4
---
# What&#39;s new in client deployment for Configuration Manager 2012
## What’s New in Configuration Manager for Windows-Based Computers  
  
> [!NOTE]  
>  [!INCLUDE[cm5reuse]()] the [Getting Started with Configuration Manager 2012](assetId:///ff235204-7390-4f48-b211-f3707dee3035) guide.  
  
 The following items are new or have changed for client deployment since [!INCLUDE[sccmshortname]()]:  
  
-   Clients are no longer configured for mixed mode or native mode, but instead use HTTPS together with public key infrastructure (PKI) certificates or HTTP together with self-signed certificates. Clients use HTTPS or HTTP according to the configuration of the site system roles that the clients connect to and whether they have a valid PKI certificate that performs client authentication.  
  
     On the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, in **Properties**, on the **General** tab, review the **Client certificate** value to determine the current client communication method. This value displays **PKI certificate** when the client communicates with a management point over HTTPS, and **Self-signed** when the client communicates with a management point over HTTP. Just as the client property value for the **Connection type** updates, depending on the current network status of the client, so the **Client certificate** client property value updates, depending on with which management point the client communicates.  
  
-   Because [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] does not use mixed mode and native mode, the client installation property **/native: [<native mode option\>]** is no longer used. Instead, use **/UsePKICert** to use a PKI certificate that has client authentication capability, if it is available, but fall back to an HTTP connection if no certificate is available. If **/UsePKICert** is not specified, the client does not attempt to communicate by using a PKI certificate, but communicates by using HTTP only. Additionally, use the new command **/NoCRLCheck** if you do not want a client to check the certificate revocation list (CRL) before it establishes an HTTPS communication.  
  
-   The client.msi property **SMSSIGNCERT** is still used but requires the exported self-signed certificate of the site server. This certificate is stored in the **SMS** certificate store and has the Subject name **Site Server** and the friendly name **Site Server Signing Certificate**.  
  
-   When you reassign a client from a [!INCLUDE[cm5long](../System Center Configuration Manager/itokens/cm5long_md.md)] hierarchy to another [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] hierarchy, the client can automatically replace the trusted root key, if the new site is published to Active Directory Domain Services and the client can access that information from a global catalog server. For this scenario in [!INCLUDE[sccmshortname]()], you had to remove the trusted root key, manually replace the trusted root key, or uninstall and reinstall the client.  
  
-   The server locator point is no longer used for site assignment or to locate management points. This functionality is replaced by the management point. The CCMSetup Client.msi property **SMSSLP** remains supported, but only to specify the computer name of management points.  
  
-   You no longer install International Client Packs when you want to support different languages on the client. Instead, select the client languages that you want during Setup. Then, during the client installation, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically installs support for those languages on the client, enabling the display of information in a language that matches the user’s language preferences. If a matching language is not available, the client displays information in the default of English. For more information, see the [Planning for Client Language Packs](assetId:///cac5835c-bc12-4d35-bc46-b61931559f26#BKMK_ClientLangPack) section in the [Planning for Sites and Hierarchies in Configuration Manager](assetId:///cac5835c-bc12-4d35-bc46-b61931559f26) topic.  
  
-   Decommissioned clients are no longer displayed in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and they are automatically removed from the database by the **Delete Aged Discovery Data** task.  
  
-   The Client.msi property for CCMSetup, **SMSDIRECTORYLOOKUP=WINSPROMISCUOUS**, is no longer supported. This setting allowed the client to use Windows Internet Name Service (WINS) to find a management point without verifying the management point's self-signed certificate.  
  
-   To support the new 64-bit client, the location of the **CCM** folder for client-related files (such as the client cache and log files) has changed from %*windir*%\\**system32** to %*windir*%. If you reference the **CCM** folder for your own script files, update these references for the new folder location for [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] clients. [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] does not support the **CCM** folder on paths that support redirection (such as **Program Files** and %*windir*%\\**system32**) on 64-bit operating systems.  
  
-   Automatic, site-wide client push now installs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] on existing computer resources if the client is not installed, and not just newly discovered computer resources.  
  
-   Client push installation starts and tracks the installation of the client by using the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database and no longer creates individual .CCR files. When you enable client push installation for a site, all discovered resources that are assigned to the site and that do not have a client installed are immediately added to the database, and client installation begins.  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can automatically upgrade [!INCLUDE[sccmshortname]()] and [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] clients to the latest [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] version when they are below a version that you specify. For more information see the [How to Automatically Upgrade the Configuration Manager Client](assetId:///2ad4b21a-43bd-434e-b3bb-fc8744da7e9c#BKMK_upgrade) section in the topic [How to Install Clients on Computers in Configuration Manager](assetId:///2ad4b21a-43bd-434e-b3bb-fc8744da7e9c).  
  
## What’s New in Configuration Manager SP1 for Windows-Based Computers  
  
> [!NOTE]  
>  [!INCLUDE[cm5reuse]()] the [Getting Started with Configuration Manager 2012](assetId:///ff235204-7390-4f48-b211-f3707dee3035) guide.  
  
 The following items are new or have changed for client deployment in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1:  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can automatically upgrade Configuration Manager 2007 and System Center 2012 Configuration Manager clients to the version of their assigned [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] site. For more information see the [How to Automatically Upgrade the Configuration Manager Client for the Hierarchy](assetId:///2ad4b21a-43bd-434e-b3bb-fc8744da7e9c#BKMK_upgrade) section in the topic [How to Install Clients on Windows Computers in Configuration Manager](assetId:///2ad4b21a-43bd-434e-b3bb-fc8744da7e9c).  
  
-   You can now specify the following CCMSetup.exe properties as installation options when you use client push:  
  
    -   /forcereboot  
  
    -   /skipprereq  
  
    -   /logon  
  
    -   /BITSPriority  
  
    -   /downloadtimeout  
  
    -   /forceinstall  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SP1 clients now use Microsoft Silverlight 5 for the Application Catalog. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically installs this version of Silverlight on clients if it is not already installed, and by default, configures the **Computer Agent** client setting **Allow Silverlight applications to run in elevated trust mode** to **Yes**. For more information, see the [Certificates for Silverlight 5 and Elevated Trust Mode Required for the Application Catalog](assetId:///4cfd0485-12c1-48b2-bdea-97009e30dec8#BKMK_CertificatesSilverlight5) section in the [Security and Privacy for Application Management in Configuration Manager](assetId:///4cfd0485-12c1-48b2-bdea-97009e30dec8) topic.  
  
-   There is a new value that is now the default for the **Computer Agent** client setting **PowerShell execution policy**: **All Signed**. This new value restricts the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client to running Windows PowerShell scripts only if they are signed by a trusted publisher, regardless of the current Windows PowerShell configuration on the client computer. For more information, see the [Computer Agent](assetId:///4acd0c29-e453-4863-8194-e479263291c8#BKMK_ComputerAgentDeviceSettings) section in the [About Client Settings in Configuration Manager](assetId:///4acd0c29-e453-4863-8194-e479263291c8) topic.  
  
-   The new **Computer Agent** client setting, **Disable deadline randomization**, by default, disables the installation randomization delay for required software updates and required application deployments. For more information, see the [Computer Agent](assetId:///4acd0c29-e453-4863-8194-e479263291c8#BKMK_ComputerAgentDeviceSettings) section in the [About Client Settings in Configuration Manager](assetId:///4acd0c29-e453-4863-8194-e479263291c8) topic.  
  
-   Client notification in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] enables some client operations to be performed as soon as possible, instead of during the usual client policy polling interval. For example, you can use the client management task **Download Computer Policy** to instruct computers to download policy as soon as possible. Additionally, you can initiate some actions for Endpoint Protection, such as a malware scan of a client.  
  
     By default, client notification communication uses TCP port 10123, which is configurable as a site property for a primary site. You might have to configure Windows Firewall on the management point, clients, and any intervening firewalls for this new port communication. However, client notification can fall back to using the established client-to-management point communication of HTTP or HTTPS. Actions taken by client notification are displayed in the new **Client Operations** node in the **Monitoring** workspace.  
  
    > [!NOTE]  
    >  Client notification does not support role-based administration. All users of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console can see notifications in the **Client Operations** node in the **Monitoring** workspace.  
  
     For more information, see [How to Configure Client Communication Port Numbers in Configuration Manager](assetId:///50797b78-ca28-4423-9196-c71c2c1d2af7) and [How to Manage Clients in Configuration Manager](assetId:///782a762c-7178-4fca-8613-4f1d125bb5e7).  
  
-   You can install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on computers that run Mac OS X. You can then manage this client by using compliance settings, deploying software, and by collecting hardware inventory. For more information, see [How to Install Clients on Mac Computers in Configuration Manager](assetId:///d3416e89-3c8f-4c51-97ff-1bba3c1ca5fc).  
  
-   You can install the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client on servers that run a supported version of Linux or UNIX. You can then manage this client by using deploying software, and by collecting hardware inventory. For more information, see [How to Install Clients on Linux and UNIX Computers in Configuration Manager](assetId:///2d2ba997-9d2c-4e5d-80c6-f59e18a3cc6e).  
  
## What’s New in System Center 2012 R2 Configuration Manager for Windows-Based Computers  
  
> [!NOTE]  
>  [!INCLUDE[cm5reuse]()] the [Getting Started with Configuration Manager 2012](assetId:///ff235204-7390-4f48-b211-f3707dee3035) guide.  
  
 The following items are new or have changed for client deployment in [!INCLUDE[sccm2012r2_1](../System Center Configuration Manager/itokens/sccm2012r2_1_md.md)]:  
  
-   You can now select **Resultant Client Settings** from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to view the effective client settings that will be applied to the selected device. The resultant client setting accounts for the prioritization or combination of attributes where multiple client settings have been deployed to the same device. For more information, see [Viewing the Resultant Client Settings](assetId:///dcc11cdf-d87e-4931-9cd5-125bb8140d3e#BKMK_ResultantClientSettings).  
  
-   You can now reassign [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients, including managed mobile devices, to another primary site in the hierarchy. Clients can be reassigned individually or can be multi-selected and reassigned in bulk to a new site.  
  
-   If you use wake-up proxy, you no longer have to manually configure Windows Firewall on clients to allow TCP/IP ping commands when you specify the **Power Management** client setting, **Firewall exception for wake-up proxy**.  
  
-   A new property has been added for Ccmsetup.exe, **/ExcludeFeatures:<feature\>**. This property prevents the specified feature from installing the client installation. For this release, the only supported feature is **ClientUI**, which prevents the Software Center from installing on the client. For more information, see [CCMSetup.exe Command-Line Properties](assetId:///048dbf2d-5132-4fc0-ad8a-d90322b6db96#BKMK_CCMSetupCommandLine).