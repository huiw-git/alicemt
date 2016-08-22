---
title: "Client installation methods in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 51b5964b-374d-4abc-8619-414a9fffad2d
caps.latest.revision: 9
caps.handback.revision: 0
---
# Client installation methods in System Center Configuration Manager
You can use different methods to install the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] client software on Windows devices, UNIX/Linux servers, and Mac computers in your enterprise. You can use one or any combination of these methods that suit your requirements.  
  
 The following sections outline the advantages and disadvantages of each client installation method to help you determine which will work best in your organization.  
  
## Client push installation  
 **Supported client platform:** Windows  
  
 **Advantages**  
  
-   Can be used to install the client on a single computer, a collection of computers, or to the results from a query.  
  
-   Can be used to automatically install the client on all discovered computers.  
  
-   Automatically uses client installation properties defined on the **Client** tab in the **Client Push Installation Properties** dialog box.  
  
 **Disadvantages**  
  
-   Can cause high network traffic when pushing to large collections.  
  
-   Can only be used on computers that have been discovered by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   Cannot be used to install clients in a workgroup.  
  
-   A client push installation account must be specified that has administrative rights to the intended client computer.  
  
-   Windows Firewall must be configured on client computers with exceptions so that client push installation can be completed.  
  
-   You cannot cancel client push installation. When you use this client installation method for a site, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] tries to install the client on all discovered resources and retries any failures for up to 7 days.  
  
 For more information about this installation method, see [How to deploy clients to Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md).  
  
## Software update point-based installation  
 **Supported client platform:** Windows  
  
 **Advantages:**  
  
-   Can use your existing software updates infrastructure to manage the client software.  
  
-   Can automatically install the client software on new computers if Windows Server Update Services (WSUS) and Group Policy settings in Active Directory Domain Services are configured correctly.  
  
-   Does not require computers to be discovered before the client can be installed.  
  
-   Computers can read client installation properties that have been published to Active Directory Domain Services.  
  
-   Will reinstall the client software if it is removed.  
  
-   Does not require you to configure and maintain an installation account for the intended client computer.  
  
 **Disadvantages:**  
  
-   Requires a functioning software updates infrastructure as a prerequisite.  
  
-   Must use the same server for client installation and software updates, and this server must reside in a primary site.  
  
-   To install new clients, you must configure a Group Policy Object (GPO) in Active Directory Domain Services with the client's active software update point and port.  
  
-   If the Active Directory schema is not extended for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you must use Group Policy settings to provision computers with client installation properties.  
  
 For more information about this installation method, see [How to deploy clients to Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md).  
  
## Group Policy installation  
 **Supported client platform:** Windows  
  
 **Advantages:**  
  
-   Does not require computers to be discovered before the client can be installed.  
  
-   Can be used for new client installations or for upgrades.  
  
-   Computers can read client installation properties that have been published to Active Directory Domain Services.  
  
-   Does not require you to configure and maintain an installation account for the intended client computer.  
  
 **Disadvantages:**  
  
-   Can cause high network traffic if a large number of clients are being installed.  
  
-   If the Active Directory schema is not extended for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], you must use Group Policy settings to add client installation properties to computers in your site.  
  
 For more information about this installation method, see [How to deploy clients to Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md).  
  
## Logon script installation  
 **Supported client platform:** Windows  
  
 **Advantages:**  
  
-   Does not require computers to be discovered before the client can be installed.  
  
-   Supports using command-line properties for CCMSetup.  
  
 **Disadvantages:**  
  
-   Can cause high network traffic if a large number of clients are being installed over a short time period.  
  
-   Can take a long time to install on all client computers if users do not frequently log on to the network.  
  
 For more information about this installation method, see [How to deploy clients to Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md).  
  
## Manual installation  
 **Supported client platform:** Windows, UNIX/Linux, Mac OS X  
  
 **Advantages:**  
  
-   Does not require computers to be discovered before the client can be installed.  
  
-   Can be useful for testing purposes.  
  
-   Supports using command-line properties for CCMSetup.  
  
 **Disadvantages:**  
  
-   No automation, therefore time consuming.  
  
 For more information about how to manually install the client on each of platform, see the following:  
  
-   [How to deploy clients to Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Windows-computers-in-System-Center-Configuration-Manager.md)  
  
-   [How to deploy clients to UNIX and Linux servers in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-UNIX-and-Linux-servers-in-System-Center-Configuration-Manager.md)  
  
-   [How to deploy clients to Macs in System Center Configuration Manager](../System Center Configuration Manager/How-to-deploy-clients-to-Macs-in-System-Center-Configuration-Manager.md)  
  
## See Also  
 [Planning considerations for deploying clients in System Center Configuration Manager](../System Center Configuration Manager/Planning-considerations-for-deploying-clients-in-System-Center-Configuration-Manager.md)