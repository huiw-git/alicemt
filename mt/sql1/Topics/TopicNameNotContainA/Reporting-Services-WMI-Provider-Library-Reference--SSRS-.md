---
title: "Reporting Services WMI Provider Library Reference (SSRS)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - Reporting Services WMI Provider Library
apilocation: 
  - reportingservices.mof
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
caps.latest.revision: 43
manager: mblythe
---
# Reporting Services WMI Provider Library Reference (SSRS)
The [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Windows Management Instrumentation (WMI) provider supports WMI operations that enable you to write scripts and code to modify settings of the report server and Report Manager.  
  
 For example, if you want to change whether integrated security is used when the report server connects to the report server database, create an instance of the **MSReportServer_ConfigurationSetting** class and use the **DatabaseIntegratedSecurity** property of the of the report server instance. The classes shown in the following table represent [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] components. The classes are defined in either the [!INCLUDE[ssRSWMInmspc](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspc_md.md)] or the [!INCLUDE[ssRSWMInmspcA](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspcA_md.md)] namespaces. Each of the classes support read and write operations. Create operations are not supported.  
  
## Classes  
 [MSReportServer_Instance Class](../../Topics/TopicNameNotContainA/MSReportServer_Instance-Class.md)  
 Provides basic information required for a client to connect to an installed report server.  
  
 [MSReportServer_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
 Represents the installation and run-time parameters of a report server instance. These parameters are stored in the configuration file for the report server.  
  
 For more information about WMI operations, see the WMI SDK documentation included with the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] SDK.  
  
## See Also  
 [Access the Reporting Services WMI Provider](../../Topics/TopicNameNotContainA/Access-the-Reporting-Services-WMI-Provider.md)   
 [Technical Reference (SSRS)](../../Topics/TopicNameNotContainA/Technical-Reference--SSRS-.md)