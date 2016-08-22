---
title: "Proxy server support in System Center Configuration Manager"
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
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
caps.latest.revision: 6
caps.handback.revision: 0
---
# Proxy server support in System Center Configuration Manager
Both [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site system servers and  clients can make use of a proxy server.  
  
## Site system servers  
 When site system roles need to connect to the internet, you can configure them to use a proxy server.  
  
-   A  computer that hosts a site system server supports a single proxy server configuration that is shared by all site system roles on that computer. If you need separate proxy servers for different roles or instances of a role, you must place those  roles on separate site system servers.  
  
-   When you configure    new proxy server settings for a site system server that already has a proxy server configuration, the original configuration is overwritten.  
  
-   Connections to the proxy use the **System** account of the computer that hosts the site system role.  
  
 The following site system roles connect to the internet and might require a proxy server.  With one exception, site system roles that can use a proxy do so with no additional configuration. The exception is the software update point. The following list contains information about the additional configurations a software update point requires:  
  
 **Asset Intelligence synchronization point** - This site system role connects to Microsoft and will use a proxy server configuration on the computer that hosts the Asset Intelligence synchronization point.  
  
 **Cloud-based distribution point** - To configure a proxy server for a cloud-based distribution point, you configure the proxy on the primary site that manages the cloud-based distribution point.  
  
 For this configuration, the primary site server:  
  
-   Must be able to connect to Microsoft Azure to provision, monitor, and distribute content to the distribution point.  
  
-   Uses that computers System account to make the connection.  
  
-   Uses that computers default web browser.  
  
 You cannot configure a proxy server on the cloud-based-distribution point in Microsoft Azure.  
  
 **Cloud connection point** - This site system role connects to the Configuration Manager cloud service to download version updates for Configuration Manager and will use a proxy server configured on the computer that hosts the service connection point.  
  
 **Exchange Server connector** - This site system role connects to an Exchange Server and will use a proxy server configuration on the computer that hosts the Exchange Server connector.  
  
 **Service connection point** - This site system role connects to [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] and will use a proxy server configuration on the computer that hosts the service connection point.  
  
 **Software updates point** - This site system role can use the proxy when it connects to Microsoft Update to download patches and synchronize information about updates.   
Software update points only use a proxy for the two following options when you enable that option when you configure the software update point:  
  
-   **Use a proxy server when synchronizing software updates**  
  
-   **Use a proxy server when downloading content by using automatic deployment rules** (While available for use, this setting is not used by software update points at secondary sites)  
  
 Configure the proxy server settings on the Active Software Update Point page of the Add Site System Roles wizard or on the General tab in Software Update Point Component Properties.  
  
-   The proxy server settings are associated only with the software update point at the site.  
  
-   Proxy server options are only available when there is already a proxy server configured for the site system server that hosts the software update point.  
  
> [!NOTE]  
>  By default, the **System** account for the server on which an automatic deployment rule was created is used to connect to the Internet and download software updates when the automatic deployment rules run.  
>   
>  When this account does not have access to the Internet, software updates fail to download and the following entry is logged to ruleengine.log: **Failed to download the update from internet. Error = 12007.**  
  
#### To configure the proxy server for a site system server  
  
1.  In the Configuration Manager console, click Administration, expand Site Configuration, and then click Servers and Site System Roles.  
  
2.  Select the site system server that you want to edit, and then in the details pane, right-click Site system, and then click Properties.  
  
3.  In Site system Properties, select the Proxy tab, and then configure the proxy settings for this primary site server.  
  
4.  Click OK to save the new proxy server configuration.  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)