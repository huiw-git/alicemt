---
title: "Configure firewalls, ports, and domains for System Center Configuration Manager"
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
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
caps.latest.revision: 15
caps.handback.revision: 0
---
# Configure firewalls, ports, and domains for System Center Configuration Manager
To prepare your network to support [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], plan to configure infrastructure like firewalls to pass the communications used by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
|Consideration|Details|  
|-------------------|-------------|  
|**Ports and protocols** used by different [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] capabilities. Some ports are required, while other **Domains and services** can be customized.|Most [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] communications use common ports such as port 80 for HTTP or 443 for HTTPS communication. However, [some site system roles support use of custom websites](https://technet.microsoft.com/library/mt426625.aspx) and custom ports.<br /><br /> **Before you deploy [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]**, identify the ports you plan to use and configure firewalls accordingly.<br /><br /> **Later, if you need to change a port** after you install [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], don't forget to update firewalls on devices and the network and also change the configuration of the port from within [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].<br /><br /> For more information see, [How to configure client communication ports in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-communication-ports-in-System-Center-Configuration-Manager.md) and [Ports used in System Center Configuration Manager](../System Center Configuration Manager/Ports-used-in-System-Center-Configuration-Manager.md).|  
|**Domains and services** that site servers and clients might need to access.|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] capabilities can require site servers and clients have access to specific services and Domains on the internet, like Windowsudpate.microsoft.com or the [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] service.<br /><br /> If you will use [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] to manage mobile devices, you must also configure access to [ports and domains that are required by Intune.](https://technet.microsoft.com/dn646950.aspx)|  
|**Proxy servers** for site system servers and for client communications. You can specify separate proxy servers for different site system servers and clients.|Because these configurations are made at the time you install a site system role or client, you only need to be aware of the proxy server configurations for later reference when you configure site system roles and clients.<br /><br /> If you’re not sure your deployment will need to use proxy servers, review [Proxy server support in System Center Configuration Manager](../System Center Configuration Manager/Proxy-server-support-in-System-Center-Configuration-Manager.md) to learn about  site system roles and client actions that can use a proxy server.|  
  
## See Also  
 [Prepare your network environment for System Center Configuration Manager](../System Center Configuration Manager/Prepare-your-network-environment-for-System-Center-Configuration-Manager.md)