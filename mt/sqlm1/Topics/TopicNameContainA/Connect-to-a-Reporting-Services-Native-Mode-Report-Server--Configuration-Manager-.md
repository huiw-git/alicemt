---
title: Connect to a Reporting Services Native Mode Report Server (Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
robots: noindex,nofollow
---
# Connect to a Reporting Services Native Mode Report Server (Configuration Manager)
  Use this dialog box to connect to a local or remote [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] or later [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server instance. You cannot use this tool to connect to earlier versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report servers. You can only connect to one instance at a time.  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
> [!NOTE]  
>  The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager is not used to configure and administer [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode. You Use SharePoint Central Administration and PowerShell scripts to configure a report server in SharePoint mode. For more information, see [Install Reporting Services SharePoint Mode for SharePoint 2010](assetId:///47efa72e-1735-4387-8485-f8994fb08c8c)  
  
> [!TIP]  
>  The[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager \(RSConfigTool.exe\) is installed with a privilege level of “highestAvailable”. This behavior is by design. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager requires communication with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] WMI APIs. Some of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] WMI communication requires a higher level or administrative of privileges.  
  
-   To connect to a local report server instance, use the default values and click **Connect**. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager provides the local server name and detects the default instance. In most cases, you can click **Connect** without having to change the values. If you installed more than one instance, you must select the one that you want to use.  
  
-   To connect to a remote report server instance, type the server name, click **Find**, select the instance, and then click **Connect**.  
  
 To open this dialog box, start the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager. This dialog box appears immediately when you start the tool. For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md).  
  
## Options  
 **Server Name**  
 Enter the network name of the computer on which [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] or later [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is installed. Type just the computer name; do not include a prefix or slashes.  
  
 **Find**  
 Find the computer specified in **Server Name**.  
  
 **Report Server Instance**  
 Select which instance to connect to if multiple report server instances are installed. Only valid instances are available for selection. If you are running older versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] side\-by\-side a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance, those instances will not appear in the list.  
  
 **Connect**  
 Connect to the server and instance you specified.  
  
## See Also  
 [Reporting Services Configuration Manager &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md)  
  
  