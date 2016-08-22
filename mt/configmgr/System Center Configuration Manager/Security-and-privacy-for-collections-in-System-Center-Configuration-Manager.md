---
title: "Security and privacy for collections in System Center Configuration Manager"
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
ms.assetid: 30bf2451-5415-4be2-ba8d-21759370cd83
caps.latest.revision: 5
caps.handback.revision: 0
author: barlanmsft
---
# Security and privacy for collections in System Center Configuration Manager
This topic contains security best practices and privacy information for collections in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
 There is no privacy information specifically for collections in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. Collections are containers for resources, such as users and devices. Collection membership often depends on the information that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collects during standard operation. For example, by using resource information that has been collected from discovery or inventory, a collection can be configured to contain the devices that meet specified criteria. Collections might also be based on the current status information for client management operations, such as deploying software and checking for compliance. In addition to these query-based collections, administrative users can also add resources to collections.  
  
 For more information about collections, see [Introduction to collections in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-collections-in-System-Center-Configuration-Manager.md). For more information about any security best practices and privacy information for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operations that can be used to configure collection membership, see [Security best practices and privacy information for System Center Configuration Manager](../System Center Configuration Manager/Security-best-practices-and-privacy-information-for-System-Center-Configuration-Manager.md).  
  
## Security Best Practices for Collections  
 Use the following security best practice for collections.  
  
|Security best practice|More information|  
|----------------------------|----------------------|  
|When you export or import a collection by using a Managed Object Format (MOF) file that is saved to a network location, secure the location, and secure the network channel.|Restricts who can access the network folder.<br /><br /> Use Server Message Block (SMB) signing or Internet Protocol security (IPsec) between the network location and the site server to prevent an attacker from tampering with the exported collection data. Use IPsec to encrypt the data on the network to prevent information disclosure.|  
  
### Security Issues for Collections  
 Collections have the following security issues:  
  
-   If you use collection variables, local administrators can read potentially sensitive information.  
  
     Collection variables can be used when you deploy an operating system.  
  
## See Also  
 [Collections technical reference for System Center Configuration Manager](../System Center Configuration Manager/Collections-technical-reference-for-System-Center-Configuration-Manager.md)