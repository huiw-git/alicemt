---
title: Reporting Services WMI Provider Library Reference (SSRS)
ms.custom: na
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
---
# Reporting Services WMI Provider Library Reference (SSRS)
  The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Windows Management Instrumentation \(WMI\) provider supports WMI operations that enable you to write scripts and code to modify settings of the report server and Report Manager.  
  
 For example, if you want to change whether integrated security is used when the report server connects to the report server database, create an instance of the MSReportServer\_ConfigurationSetting class and use the DatabaseIntegratedSecurity property of the of the report server instance. The classes shown in the following table represent [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components. The classes are defined in either the [!INCLUDE[ssRSWMInmspc](../../Token\Other/ssRSWMInmspc_md.md)] or the [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)] namespaces. Each of the classes support read and write operations. Create operations are not supported.  
  
## Classes  
 [MSReportServer_Instance Class](../../Topics\TopicNameNotContainA/MSReportServer_Instance-Class.md)  
 Provides basic information required for a client to connect to an installed report server.  
  
 [MSReportServer_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
 Represents the installation and run\-time parameters of a report server instance. These parameters are stored in the configuration file for the report server.  
  
 For more information about WMI operations, see the WMI SDK documentation included with the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] SDK.  
  
## See Also  
 [Access the Reporting Services WMI Provider](../../Topics\TopicNameNotContainA/Access-the-Reporting-Services-WMI-Provider.md)   
 [Technical Reference &#40;SSRS&#41;](../Topic/Technical%20Reference%20\(SSRS\).md)  
  
  