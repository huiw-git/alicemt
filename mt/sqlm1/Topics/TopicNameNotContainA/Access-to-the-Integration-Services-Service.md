---
title: Access to the Integration Services Service
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
---
# Access to the Integration Services Service
  Package protection levels can limit who is allowed to edit and execute a package. Additional protection is needed to limit who can view the list of packages currently running on a server and who can stop currently executing packages in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] uses the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service to list running packages. Members of the Windows Administrators group can view and stop all currently running packages. Users who are not members of the Administrators group can view and stop only packages that they started.  
  
 It is important to restrict access to computers that run an [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service, especially an [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service that can enumerate remote folders. Any authenticated user can request the enumeration of packages. Even if the service does not find the service, the service enumerates folders. These folder names may be useful to a malicious user. If an administrator has configured the service to enumerate folders on a remote machine, users may also be able to see folder names that they would normally not be able to see.  
  
  