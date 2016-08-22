---
title: "Prepare your network environment for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: e86e9bfc-c994-4d84-bed1-a02153b8b859
caps.latest.revision: 14
caps.handback.revision: 0
---
# Prepare your network environment for System Center Configuration Manager
Before you can successfully install and use Configuration Manager, you must configure your network, Windows infrastructure, and supporting technologies to support Configuration Manager. This can include:  
  
-   [Extend the Active Directory schema](https://technet.microsoft.com/library/mt345589.aspx) so that sites can publish information about their configuration and capabilities where clients can then find it. If you don’t extend the schema, you might need to configure workaround to help clients locate available services and resources.  
  
-   [Configure network infrastructure](https://technet.microsoft.com/library/mt427452.aspx) like firewalls and ports to enable sites, site system servers, and clients to communicate across your network.  
  
-   [Prepare Windows Servers to support System Center Configuration Manager](../System Center Configuration Manager/Prepare-Windows-Servers-to-support-System-Center-Configuration-Manager.md) by installing Windows features, Windows roles, and configuring IIS. Not all site systems have the same prerequisites or configuration requirements, but some might require you to  reboot servers after they are configured – so plan ahead to reduce time to deployment later.  
  
-   [Configure custom websites](https://technet.microsoft.com/library/mt426625.aspx) for site system roles that require IIS and accept communications from clients.  
  
-   [Prepare cloud services](http://technet.microsoft.com/library/mt449632.aspx) like Microsoft Azure and [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] for integration with your deployment.  
  
-   [PKI certificate requirements for System Center Configuration Manager](../System Center Configuration Manager/PKI-certificate-requirements-for-System-Center-Configuration-Manager.md)  
  
-   [Step-by-step example deployment of the PKI certificates for System Center Configuration Manager: Windows Server 2008 Certification Authority](../Topic/Step-by-step%20example%20deployment%20of%20the%20PKI%20certificates%20for%20System%20Center%20Configuration%20Manager:%20Windows%20Server%202008%20Certification%20Authority.md)  
  
## See Also  
 [Get ready for System Center Configuration Manager](../System Center Configuration Manager/Get-ready-for-System-Center-Configuration-Manager.md)