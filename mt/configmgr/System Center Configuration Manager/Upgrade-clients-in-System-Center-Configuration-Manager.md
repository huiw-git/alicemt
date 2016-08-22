---
title: "Upgrade clients in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-03-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 446c83b5-c292-4e74-ba19-0792ac6b3472
caps.latest.revision: 8
---
# Upgrade clients in System Center Configuration Manager
You can use different methods to upgrade the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] client software on Windows computers, UNIX and Linux servers, and Mac computers in your enterprise. The following sections outlines the advantages and disadvantages of each client upgrade method to help you determine which will work best for your organization.  
  
> [!TIP]  
>  [!INCLUDE[cm-client-upgrade-tip](../System Center Configuration Manager/itokens/cm-client-upgrade-tip_md.md)]  
  
## Group Policy installation  
 **Supported client platform:** Windows  
  
 **Advantages**  
  
-   Does not require computers to be discovered before the client can be upgraded.  
  
-   Can be used for new client installations or for upgrades.  
  
-   Computers can read client installation properties that have been published to Active Directory Domain Services.  
  
-   Does not require you to configure and maintain an installation account for the intended client computer.  
  
 **Disadvantages**  
  
-   Can cause high network traffic if a large number of clients are being upgraded.  
  
-   If the Active Directory schema is not extended for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you must use Group Policy settings to add client installation properties to computers in your site.  
  
 For more information, see [How to Install Configuration Manager Clients by Using Group Policy](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md#BKMK_ClientGP).  
  
## Logon script installation  
 **Supported client platform:** Windows  
  
 **Advantages**  
  
-   Does not require computers to be discovered before the client can be installed.  
  
-   Can be used for new client installations or for upgrades.  
  
-   Supports using command-line properties for CCMSetup.  
  
 **Disadvantages**  
  
-   Can cause high network traffic if a large number of clients are being upgraded over a short time period.  
  
-   Can take a long time to upgrade on all client computers if users do not frequently log on to the network.  
  
 For more information, see [How to Install Configuration Manager Clients by Using Logon Scripts](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md#BKMK_ClientLogonScript).  
  
## Manual installation  
 **Supported client platform:** Windows, UNIX/Linus, Mac OS X  
  
 **Advantages**  
  
-   Does not require computers to be discovered before the client can be upgraded.  
  
-   Can be useful for testing purposes.  
  
-   Supports using command-line properties for CCMSetup.  
  
 **Disadvantages**  
  
-   No automation, therefore time consuming.  
  
 For more information, see the following topics:  
  
-   [How to Install Configuration Manager Clients Manually](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md#BKMK_Manual)  
  
-   [How to upgrade clients for Linux and UNIX servers in System Center Configuration Manager](../System Center Configuration Manager/How-to-upgrade-clients-for-Linux-and-UNIX-servers-in-System-Center-Configuration-Manager.md)  
  
-   [How to upgrade clients on Mac computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-upgrade-clients-on-Mac-computers-in-System-Center-Configuration-Manager.md)  
  
## Upgrade installation (application management)  
 **Supported client platform:** Windows  
  
> [!NOTE]  
>  You cannot upgrade [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] clients by using this method. In this scenario, you can deploy the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client as a package from the [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] site, or you can use automatic client upgrade which automatically creates and deploys a package that contains the latest version of the client.  
  
 **Advantages**  
  
-   Supports using command-line properties for CCMSetup.  
  
 **Disadvantages**  
  
-   Can cause high network traffic when distributing the client to large collections.  
  
-   Can only be used to upgrade the client software on computers that have been discovered and assigned to the site.  
  
 For more information, see [How to Install Configuration Manager Clients by Using a Package and Program](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md#BKMK_ClientApp).  
  
## Automatic client upgrade  
  
> [!NOTE]  
>  Can be used to upgrade [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] clients to [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] clients. A [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)]client can assign to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, but cannot perform any actions besides automatic client upgrade.  
  
 **Supported client platform:** Windows  
  
 **Advantages**  
  
-   Can be used to automatically keep clients in your site at the latest version.  
  
-   Requires minimal administration by the administrative user.  
  
 **Disadvantages**  
  
-   Can only be used to upgrade the client software and cannot be used to install a new client.  
  
-   Not suitable for upgrading many clients simultaneously.  
  
-   Applies to all clients in the hierarchy that are assigned to a site. Cannot be scoped by collection.  
  
-   Limited scheduling options.  
  
 For more information, see [How to upgrade clients for Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-upgrade-clients-for-Windows-computers-in-System-Center-Configuration-Manager.md).  
  
## Client testing  
 **Supported client platform:** Windows  
  
 **Advantages**  
  
-   Can be used to test new client versions in a smaller preproduction collection.  
  
-   When testing is complete, clients in preproduction are promoted to production and automatically upgraded across the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
 **Disadvantages**  
  
-   Can only be used to upgrade the client software and cannot be used to install a new client.  
  
 [How to test client upgrades in a preproduction collection in System Center Configuration Manager](../System Center Configuration Manager/How-to-test-client-upgrades-in-a-preproduction-collection-in-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Manage computer clients with System Center Configuration Manager](../System Center Configuration Manager/Manage-computer-clients-with-System-Center-Configuration-Manager.md)