---
title: "Reporting Services Security and Protection"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
caps.latest.revision: 22
manager: mblythe
---
# Reporting Services Security and Protection
You can use information in this section to learn about the security features of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)][!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]. This section also explains the authorization models and authentication providers supported in [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)].  
  
## Extended Protection for Authentication  
 Beginning with [!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)], support for Extended Protection for Authentication is available. The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication. The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] features need to be used with an operating system that supports Extended Protection. For more information, see [Extended Protection for Authentication with Reporting Services](../../Topics/TopicNameNotContainA/Extended-Protection-for-Authentication-with-Reporting-Services.md).  
  
## Authentication and Authorization  
 [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] provides different authentication types for users and client applications to authenticate with the report server. Using the right authentication type for your report server enables your organization to achieve the appropriate level of security required by your organization. For more information, see [Authentication with the Report Server](../../Topics/TopicNameNotContainA/Authentication-with-the-Report-Server.md).  
  
 [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] also employs roles and permissions to control user access to content in the report server catalog (in other words, who can access what, and how s/he can access it). For more information, see [Roles and Permissions (Reporting Services)](../../Topics/TopicNameNotContainA/Roles-and-Permissions--Reporting-Services-.md).  
  
## Related Tasks  
  
|Task Descriptions|Links|  
|-----------------------|-----------|  
|Configure the Secure Socket Layer (SSL) to secure client connections to the report server.|[Configure SSL Connections on a Native Mode Report Server](../../Topics/TopicNameContainA/Configure-SSL-Connections-on-a-Native-Mode-Report-Server.md)|