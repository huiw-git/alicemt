---
title: Reporting Services Security and Protection
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
---
# Reporting Services Security and Protection
  You can use information in this section to learn about the security features of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. This section also explains the authorization models and authentication providers supported in [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
## Extended Protection for Authentication  
 Beginning with [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], support for Extended Protection for Authentication is available. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features need to be used with an operating system that supports Extended Protection. For more information, see [Extended Protection for Authentication with Reporting Services](../../Topics\TopicNameNotContainA/Extended-Protection-for-Authentication-with-Reporting-Services.md).  
  
## Authentication and Authorization  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] provides different authentication types for users and client applications to authenticate with the report server. Using the right authentication type for your report server enables your organization to achieve the appropriate level of security required by your organization. For more information, see [Authentication with the Report Server](../../Topics\TopicNameNotContainA/Authentication-with-the-Report-Server.md).  
  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] also employs roles and permissions to control user access to content in the report server catalog \(in other words, who can access what, and how s\/he can access it\). For more information, see [Roles and Permissions &#40;Reporting Services&#41;](../Topic/Roles%20and%20Permissions%20\(Reporting%20Services\).md).  
  
## Related Tasks  
  
|Task Descriptions|Links|  
|-----------------------|-----------|  
|Configure the Secure Socket Layer \(SSL\) to secure client connections to the report server.|[Configure SSL Connections on a Native Mode Report Server](../../Topics\TopicNameContainA/Configure-SSL-Connections-on-a-Native-Mode-Report-Server.md)|  
  
  