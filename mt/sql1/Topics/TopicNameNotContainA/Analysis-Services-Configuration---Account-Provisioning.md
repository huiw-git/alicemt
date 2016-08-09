---
title: "Analysis Services Configuration - Account Provisioning"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 169b1af2-6fe2-467f-8ca4-919f24c620ce
caps.latest.revision: 30
caps.handback.revision: 0
manager: mblythe
---
# Analysis Services Configuration - Account Provisioning
Use this page to set the server mode, and to grant administrative permissions to users or services requiring unrestricted access to [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]. Setup does not automatically add the local Windows Group BUILTIN\Administrators to the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] server administrator role of the instance you are installing. If you want to add the local Administrators group to the server administrator role, you must explicitly specify that group.  
  
 If you are installing [!INCLUDE[ssGeminiShort](../../Topics/TopicNameNotContainA/tokens/ssGeminiShort_md.md)], be sure to grant administrative permissions to SharePoint farm administrators or service administrators who are responsible for a [!INCLUDE[ssGemini](../../Topics/TopicNameContainA/tokens/ssGemini_md.md)] server deployment in a [!INCLUDE[SPS2010](../../Topics/TopicNameContainA/tokens/SPS2010_md.md)] farm. For more information about [!INCLUDE[ssGeminiMTS](../../Topics/TopicNameNotContainA/tokens/ssGeminiMTS_md.md)] installation and service account requirements, see [Install SQL Server BI Features with SharePoint (Power Pivot and Reporting Services)](../../Topics/TopicNameNotContainA/Install-SQL-Server-BI-Features-with-SharePoint--Power-Pivot-and-Reporting-Services-.md).  
  
## Options  
 **Server Mode** - The server mode specifies the type of Analysis Services databases that can be deployed to the server. Server modes are determined during Setup and cannot be modified later. Each mode is mutually exclusive, which means that you will need two instances of Analysis Services, each configured for a different mode, to support both classic OLAP and tabular model solutions.  
  
 **Specify Administrators** - You must specify at least one server administrator for the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The users or groups that you specify will become members of the server administrator role of the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance you are installing. These must be Windows domain user accounts in the same domain as the computer on which you are installing the software.  
  
> [!NOTE]  
>  User Account Control (UAC) is a Windows security feature that requires an administrator to specifically approve administrative actions or applications before they are allowed to run. Because UAC is on by default, you will be prompted to allow specific operations that require elevated privileges. You can configure UAC to change the default behavior or customize UAC for specific programs. For more information about UAC and UAC configuration, see [User Account Control Step by Step Guide](http://go.microsoft.com/fwlink/?linkid=196350) and [User Account Control (Wikipedia)](http://go.microsoft.com/fwlink/?linkid=196351).  
  
## See Also  
 [Configure Service Accounts (Analysis Services)](../../Topics/TopicNameNotContainA/Configure-Service-Accounts--Analysis-Services-.md)   
 [Configure Windows Service Accounts and Permissions](../../Topics/TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md)