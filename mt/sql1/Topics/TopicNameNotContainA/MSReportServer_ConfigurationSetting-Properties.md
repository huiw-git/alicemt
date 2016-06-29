---
title: MSReportServer_ConfigurationSetting Properties
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
  - MSReportServer_ConfigurationSetting Properties
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: e75fe1e5-197b-4c65-859b-370821cad003
---
# MSReportServer_ConfigurationSetting Properties
  The MSReportServer_ConfigurationSetting class represents the installation and runtime parameters of a report server instance. These settings are stored in the RSReportServer.config configuration file.  
  
## Public Properties  
  
|||  
|-|-|  
|[ConnectionPoolSize](../../Topics/TopicNameNotContainA/ConnectionPoolSize-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the connection pool size used by the report server to communicate with the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)] instance that hosts the report server database. Read-only.|  
|[DatabaseLogonAccount](../../Topics/TopicNameNotContainA/DatabaseLogonAccount-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the logon account used by the report server to connect to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/includes/ssDE_md.md)] instance that hosts the report server database. Read-only.|  
|[DatabaseLogonTimeout](../../Topics/TopicNameNotContainA/DatabaseLogonTimeout-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the number of seconds to wait before an attempt to log on to the report server database fails. Read-only.|  
|[DatabaseLogonType](../../Topics/TopicNameNotContainA/DatabaseLogonType-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies whether the report server uses a Windows service account, a Windows user account, or a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] login to access the report server database. Read-only.|  
|[DatabaseName](../../Topics/TopicNameNotContainA/DatabaseName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the name of the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] instance that hosts the report server database.|  
|[DatabaseQueryTimeout](../../Topics/TopicNameNotContainA/DatabaseQueryTimeout-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the number of seconds that must elapse before the command fails or times out. The report server is timing the process against the SQL Server catalog, not a data source for the report.|  
|[DatabaseServerName](../../Topics/TopicNameNotContainA/DatabaseServerName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the name of the server on which the report server database is installed.|  
|[InstallationID Property](../../Topics/TopicNameNotContainA/InstallationID-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns a unique identifier for a specific report server instance.|  
|[InstanceName](../../Topics/TopicNameNotContainA/InstanceName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the name of a report server instance on a specific computer.|  
|[IsInitialized](../../Topics/TopicNameNotContainA/IsInitialized-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Indicates whether the report server instance is initialized.  Read-only.|  
|[IsSharePointIntegrated](../../Topics/TopicNameNotContainA/IsSharePointIntegrated-Property--WMI-.md)|Indicates whether the report server is configured for SharePoint integrated mode.|  
|[IsWebServiceEnabled](../../Topics/TopicNameNotContainA/IsWebServiceEnabled-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Indicates whether the Report Server Web service is enabled. Read-only.|  
|[IsWindowsServiceEnabled](../../Topics/TopicNameNotContainA/IsWindowsServiceEnabled-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Indicates whether the Report Server Windows service is enabled. Read-only.|  
|[MachineAccountIdentity Property &#40;WMI&#41;](../../Topics/TopicNameNotContainA/MachineAccountIdentity-Property--WMI-.md)|Gets the machine account identity of the computer that the report server is installed on.|  
|[PathName](../../Topics/TopicNameNotContainA/PathName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the installation path to a report server instance.|  
|[SecureConnectionLevel](../../Topics/TopicNameNotContainA/SecureConnectionLevel-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the secure connection level specified in the RSReportServer.config file.|  
|[SenderEmailAddress](../../Topics/TopicNameNotContainA/SenderEmailAddress-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Gets the address used to send e-mail from the report server. Read-only.|  
|[SendUsingSMTPServer](../../Topics/TopicNameNotContainA/SendUsingSMTPServer-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies whether the SendUsing property in the e-mail configuration is set to TRUE.|  
|[SMTPServer](../../Topics/TopicNameNotContainA/SMTPServer-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Gets the SMTP server property from the RSReportServer.config file. Read-only.|  
|[UnattendedExecutionAccount](../../Topics/TopicNameNotContainA/UnattendedExecutionAccount-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the login user account that the report server impersonates when running reports unattended. Read-only.|  
|[Version](../../Topics/TopicNameNotContainA/Version-Property---WMI-MSReportServer_ConfigurationSetting-.md)|Returns the version of the report server.|  
|[VirtualDirectoryReportManager Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/VirtualDirectoryReportManager-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the virtual directory for the report manager application|  
|[VirtualDirectoryReportServer Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/VirtualDirectoryReportServer-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the Virtual directory for the report server web service application.|  
|[WindowsServiceIdentityActual](../../Topics/TopicNameNotContainA/WindowsServiceIdentityActual-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the identity that the Report Server Windows service is actually running under. Read-only.|  
|[WindowsServiceIdentityConfigured](../../Topics/TopicNameNotContainA/WindowsServiceIdentityConfigured-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the identity that the Report Server Windows service was last configured to run under. Read-only.|  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  