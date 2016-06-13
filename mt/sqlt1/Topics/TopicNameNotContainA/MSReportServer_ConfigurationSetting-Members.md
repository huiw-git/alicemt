---
title: MSReportServer_ConfigurationSetting Members
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
  - MSReportServer_ConfigurationSetting Members
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 5e21a53a-a2f8-4b35-a8d9-5483519e3857
---
# MSReportServer_ConfigurationSetting Members
  The MSReportServer\_ConfigurationSetting class contains the following properties and methods.  
  
## Public Properties  
  
|||  
|-|-|  
|[ConnectionPoolSize](../../Topics/TopicNameNotContainA/ConnectionPoolSize-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the connection pool size used by the report server to communicate with the [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token/Other/ssDE_md.md)] instance that hosts the report server database. Read\-only.|  
|[DatabaseLogonAccount](../../Topics/TopicNameNotContainA/DatabaseLogonAccount-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the login account used by the report server to connect to the [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Token/Other/ssDE_md.md)] instance that hosts the report server database. Read\-only.|  
|[DatabaseLogonTimeout](../../Topics/TopicNameNotContainA/DatabaseLogonTimeout-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the number of seconds to wait before an attempt to log on to the report server database fails. Read\-only.|  
|[DatabaseLogonType](../../Topics/TopicNameNotContainA/DatabaseLogonType-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies whether the report server uses a Windows service account, a Windows user account, or a [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] login to access the report server database. Read\-only.|  
|[DatabaseName](../../Topics/TopicNameNotContainA/DatabaseName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the name of the [!INCLUDE[ssNoVersion](../../Token/Other/ssNoVersion_md.md)] instance that hosts the report server database.|  
|[DatabaseQueryTimeout](../../Topics/TopicNameNotContainA/DatabaseQueryTimeout-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the number of seconds that must elapse before the command fails or times out. The report server is timing the process against the report server database, not a data source for the report.|  
|[DatabaseServerName](../../Topics/TopicNameNotContainA/DatabaseServerName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the name of the server on which the report server database is installed.|  
|[InstallationID Property](../../Topics/TopicNameNotContainA/InstallationID-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns a unique identifier for a specific report server instance.|  
|[InstanceName](../../Topics/TopicNameNotContainA/InstanceName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the name of a report server instance on a specific computer.|  
|[IsInitialized](../../Topics/TopicNameNotContainA/IsInitialized-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Indicates whether the report server instance is initialized. Read\-only.|  
|[IsSharePointIntegrated](../../Topics/TopicNameNotContainA/IsSharePointIntegrated-Property--WMI-.md)|Indicates whether the report server is configured for SharePoint integrated mode.|  
|[IsWebServiceEnabled](../../Topics/TopicNameNotContainA/IsWebServiceEnabled-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Indicates whether the Report Server Web service is enabled. Read\-only.|  
|[IsWindowsServiceEnabled](../../Topics/TopicNameNotContainA/IsWindowsServiceEnabled-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Indicates whether the Report Server Windows service is enabled. Read\-only.|  
|[MachineAccountIdentity Property &#40;WMI&#41;](../../Topics/TopicNameNotContainA/MachineAccountIdentity-Property--WMI-.md)|Gets the machine account identity of the computer that the report server is installed on.|  
|[PathName](../../Topics/TopicNameNotContainA/PathName-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the installation path to a report server instance.|  
|[SecureConnectionLevel](../../Topics/TopicNameNotContainA/SecureConnectionLevel-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the secure connection level specified in the RSReportServer.config file.|  
|[SenderEmailAddress](../../Topics/TopicNameNotContainA/SenderEmailAddress-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Gets the address used to send e\-mail from the report server. Read\-only.|  
|[SendUsingSMTPServer](../../Topics/TopicNameNotContainA/SendUsingSMTPServer-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies whether the SendUsing property in the e\-mail configuration is set to TRUE.|  
|[SMTPServer](../../Topics/TopicNameNotContainA/SMTPServer-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Gets the SMTP server property from the RSReportServer.config file. Read\-only.|  
|[UnattendedExecutionAccount](../../Topics/TopicNameNotContainA/UnattendedExecutionAccount-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the login user account that the report server impersonates when running reports unattended. Read\-only.|  
|[Version](../../Topics/TopicNameNotContainA/Version-Property---WMI-MSReportServer_ConfigurationSetting-.md)|Returns the version of the report server.|  
|[VirtualDirectoryReportManager Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/VirtualDirectoryReportManager-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the virtual directory for the report manager application|  
|[VirtualDirectoryReportServer Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/VirtualDirectoryReportServer-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the Virtual directory for the report server web service application.|  
|[WindowsServiceIdentityActual](../../Topics/TopicNameNotContainA/WindowsServiceIdentityActual-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the identity that the Report Server Windows service is actually running under. Read\-only.|  
|[WindowsServiceIdentityConfigured](../../Topics/TopicNameNotContainA/WindowsServiceIdentityConfigured-Property--WMI-MSReportServer_ConfigurationSetting-.md)|Returns the identity that the Report Server Windows service was last configured to run under. Read\-only.|  
  
## Public Methods  
  
|||  
|-|-|  
|[BackupEncryptionKey](../../Topics/TopicNameNotContainA/BackupEncryptionKey-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Backs up the encryption key for the instance. The encryption key is stored encrypted with a password.|  
|[CreateSSLCertificateBinding Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/CreateSSLCertificateBinding-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Creates an SSL Certificate binding.|  
|[DeleteEncryptedInformation](../../Topics/TopicNameNotContainA/DeleteEncryptedInformation-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Deletes the encrypted information from the report server database.|  
|[DeleteEncryptionKey](../../Topics/TopicNameNotContainA/DeleteEncryptionKey-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Deletes the encryption keys from the report server database.|  
|[GenerateDatabaseCreationScript](../../Topics/TopicNameNotContainA/GenerateDatabaseCreationScript-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Generates an SQL script that can be used to create the report server database.|  
|[GenerateDatabaseRightsScript](../../Topics/TopicNameNotContainA/GenerateDatabaseRightsScript-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Generates an SQL script that can be used to grant a user permissions to the report server database.|  
|[GenerateDatabaseUpgradeScript](../../Topics/TopicNameNotContainA/GenerateDatabaseUpgradeScript-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Generates an SQL script that can be used to upgrade a report server database.|  
|[GetAdminSiteUrl Method &#40;WMI&#41;](../../Topics/TopicNameNotContainA/GetAdminSiteUrl-Method--WMI-.md)|Gets the absolute URL to the Central Administration Web site.|  
|[GetDatabaseVersionDisplayName](../../Topics/TopicNameNotContainA/GetDatabaseVersionDisplayName-Method--WMI-.md)|Gets the display name for a given report server database version string.|  
|[InitializeReportServer](../../Topics/TopicNameNotContainA/InitializeReportServer-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Initializes the specified report server instance.|  
|[ListInstalledSharePointVersions Method &#40;WMI&#41;](../../Topics/TopicNameNotContainA/ListInstalledSharePointVersions-Method--WMI-.md)|Returns a set of tokens that represent the versions of [!INCLUDE[winSPServ](../../Token/Other/winSPServ_md.md)] [!INCLUDE[offSPServ](../../Token/Other/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Token/Other/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Token/Other/SPS2010_md.md)] that are installed on the same computer as the report server.|  
|[ListIPAddresses Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListIPAddresses-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists IP addresses for the computer.|  
|[ListReportServersInDatabase](../../Topics/TopicNameNotContainA/ListReportServersInDatabase-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Returns a list of report server installations that are present in the report server database, regardless of whether those installations have access to secure information.|  
|[ListReservedURLs Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListReservedURLs-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists URLs reserved for all applications on the report server.|  
|[ListSSLCertificateBindings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListSSLCertificateBindings-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists SSL certificate bindings that exist in HTTP.SYS and those expected from rsreportserver.config.|  
|[ListSSLCertificates Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListSSLCertificates-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists installed SSL certificates on the computer.|  
|[ReencryptSecureInformation](../../Topics/TopicNameNotContainA/ReencryptSecureInformation-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Generates a new encryption key and re\-encrypts all secure information in the report server database using this new key.|  
|[RemoveSSLCertificateBindings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/RemoveSSLCertificateBindings-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Remove an SSL Certificate binding.|  
|[RemoveUnattendedExecutionAccount](../../Topics/TopicNameNotContainA/RemoveUnattendedExecutionAccount-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Deletes the unattended execution account entry from the report server configuration.|  
|[RemoveURL Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/RemoveURL-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Removes a URL reserved for the report server.|  
|[ReserveURL Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ReserveURL-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Adds a URL reservation for a given application.|  
|[RestoreEncryptionKey](../../Topics/TopicNameNotContainA/RestoreEncryptionKey-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Reapplies the specified encryption key to the report server database.|  
|[SetDatabaseConnection](../../Topics/TopicNameNotContainA/SetDatabaseConnection-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Sets the report server database connection to a particular report server database.|  
|[SetDatabaseLogonTimeout](../../Topics/TopicNameNotContainA/SetDatabaseLogonTimeout-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the default time\-out value for report server database logon attempts.|  
|[SetDatabaseQueryTimeout](../../Topics/TopicNameNotContainA/SetDatabaseQueryTimeout-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the default time\-out value for report server database connections.|  
|[SetEmailConfiguration](../../Topics/TopicNameNotContainA/SetEmailConfiguration-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Configures the e\-mail delivery extension used by the report server to send e\-mail.|  
|[SetSecureConnectionLevel](../../Topics/TopicNameNotContainA/SetSecureConnectionLevel-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Sets the secure connection level of the report server.|  
|[SetServiceState](../../Topics/TopicNameNotContainA/SetServiceState-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Turns the Report Server Windows and Web services on and off.|  
|[SetUnattendedExecutionAccount](../../Topics/TopicNameNotContainA/SetUnattendedExecutionAccount-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the account used to run reports unattended.|  
|[SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/SetVirtualDirectory-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Sets the virtual directory for an application.|  
|[SetWindowsServiceIdentity](../../Topics/TopicNameNotContainA/SetWindowsServiceIdentity-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Makes the Report Server Windows service run as the specified Windows user, and grants this account sufficient file system permissions to allow the report server to operate.|  
  
## See Also  
 [MSReportServer\_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
  