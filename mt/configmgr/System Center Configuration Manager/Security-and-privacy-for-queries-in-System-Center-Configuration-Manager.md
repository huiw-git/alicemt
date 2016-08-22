---
title: "Security and privacy for queries in System Center Configuration Manager"
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
ms.assetid: 30080620-20d3-4c38-b8dd-db5516e1acae
caps.latest.revision: 5
caps.handback.revision: 0
---
# Security and privacy for queries in System Center Configuration Manager
Queries in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] let you retrieve information from the site database based on the criteria that you specify. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collects the site database information during standard operation. For example, by using information that has been collected from discovery or inventory, you can configure a query to identify devices that meet specified criteria.  
  
 For more information about queries, see [Introduction to queries in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-queries-in-System-Center-Configuration-Manager.md). For more information about any security best practices and privacy information for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operations that collect the information that you can retrieve by using queries, see [Security and privacy for System Center Configuration Manager](../System Center Configuration Manager/Security-and-privacy-for-System-Center-Configuration-Manager.md).  
  
## Security Best Practices for Queries  
 Use the following security best practice for queries.  
  
|Security best practice|More information|  
|----------------------------|----------------------|  
|When you export or import a query that is saved to a network location, secure the location and secure the network channel.|Restrict who can access the network folder.<br /><br /> Use server message block (SMB) signing or Internet Protocol Security (IPsec) between the network location and the site server to prevent an attacker from tampering with the query data before it is imported.|  
  
## See Also  
 [Queries technical reference for System Center Configuration Manager](../System Center Configuration Manager/Queries-technical-reference-for-System-Center-Configuration-Manager.md)