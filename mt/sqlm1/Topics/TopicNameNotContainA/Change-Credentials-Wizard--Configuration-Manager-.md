---
title: Change Credentials Wizard (Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
robots: noindex,nofollow
---
# Change Credentials Wizard (Configuration Manager)
  The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager provides the Change Credentials Wizard to guide you through the steps of reconfiguring the account that the report server uses to connect to the report server database. When you change credentials, the Configuration Manager will update all permissions and database login information on the database server for the report server database that is actively used by the report server.  
  
 To start the wizard, click **Change Credentials** on the Database page in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager. For instructions on how to start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md).  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
## Options  
 **Database Server**  
 Specifies the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance that runs the report server database.  
  
 To connect to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance, you must use credentials that have permission to log on to the server and update database information. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager uses your current Windows credentials, but if you do not have a login or database permissions, you can specify a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database login.  
  
 You cannot specify different Windows credentials. If you want to connect as a different Windows user, login as that user and then start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager.  
  
 **Credentials**  
 Specifies the account by which the report server connects to the report server database. Valid values include the service account of the Report Server Web service, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database login defined on the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] instance you are using to host the report server, or a Windows account. If you are using a Windows account, you can specify a local account \(*\<computername\>\\\<username\>*\) if the report server and the database are on the same computer, or a domain user account \(*\<domain\>\\\<username\>*\) if they are on different computers in the same domain.  
  
 The report server will create a database login and assign database permissions for the account you specify.  
  
 The report server does not create the account itself. The account you specify must already exist and it must be valid for your deployment configuration. Specifically, if the database is on a remote computer and you want to use a Windows account, you must specify an account that has log on permissions on that computer.  
  
 If the computer is in a different or non\-trusted domain, consider using a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database login. For more information about choosing an account, see [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md).  
  
 **Summary**  
 Verify the settings before the wizard runs.  
  
 **Progress and Finish**  
 Monitor the progress of each task.  
  
## See Also  
 [Database  - Reporting Services Native mode &#40;Configuration Manager&#41;](../Topic/Database%20%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md)   
 [Change Database Wizard &#40;Configuration Manager&#41;](../Topic/Change%20Database%20Wizard%20\(Configuration%20Manager\).md)   
 [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Native%20Mode%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Reporting Services Configuration Manager Help Topics](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Manager-Help-Topics.md)   
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20a%20Report%20Server%20Database%20Connection%20%20\(SSRS%20Configuration%20Manager\).md)  
  
  