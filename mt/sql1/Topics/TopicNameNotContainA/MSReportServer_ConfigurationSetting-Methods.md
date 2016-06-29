---
title: MSReportServer_ConfigurationSetting Methods
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
  - MSReportServer_ConfigurationSetting Methods
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: a08c2476-5b8e-4792-94da-1360fe231c6e
---
# MSReportServer_ConfigurationSetting Methods
  The MSReportServer_ConfigurationSetting class of the Report Server WMI Provider provides the following public methods.  
  
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
|[ListInstalledSharePointVersions Method &#40;WMI&#41;](../../Topics/TopicNameNotContainA/ListInstalledSharePointVersions-Method--WMI-.md)|Returns a set of tokens that represent the versions of Microsoft [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/includes/winSPServ_md.md)] [!INCLUDE[offSPServ](../../Topics/TopicNameContainA/includes/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Topics/TopicNameContainA/includes/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Topics/TopicNameContainA/includes/SPS2010_md.md)] that are installed on the same computer as the report server.|  
|[ListIPAddresses Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListIPAddresses-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists IP addresses for the computer.|  
|[ListReportServersInDatabase](../../Topics/TopicNameNotContainA/ListReportServersInDatabase-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Returns a list of report server installations that are present in the report server database, regardless of whether those installations have access to secure information.|  
|[ListReservedURLs Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListReservedURLs-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists URLs reserved for all applications on the report server.|  
|[ListSSLCertificateBindings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListSSLCertificateBindings-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists SSL certificate bindings that exist in HTTP.SYS and those expected from RSReportServer.config.|  
|[ListSSLCertificates Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ListSSLCertificates-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Lists installed SSL certificates on the computer.|  
|[ReencryptSecureInformation](../../Topics/TopicNameNotContainA/ReencryptSecureInformation-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Generates a new encryption key and re-encrypts all secure information in the report server database using this new key.|  
|[RemoveSSLCertificateBindings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/RemoveSSLCertificateBindings-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Remove an SSL Certificate binding.|  
|[RemoveUnattendedExecutionAccount](../../Topics/TopicNameNotContainA/RemoveUnattendedExecutionAccount-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Deletes the unattended execution account entry from the report server configuration.|  
|[RemoveURL Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/RemoveURL-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Removes a URL reserved for the report server.|  
|[ReserveURL Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/ReserveURL-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Adds a URL reservation for a given application.|  
|[RestoreEncryptionKey](../../Topics/TopicNameNotContainA/RestoreEncryptionKey-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Reapplies the specified encryption key to the report server database.|  
|[SetDatabaseConnection](../../Topics/TopicNameNotContainA/SetDatabaseConnection-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Sets the report server database connection to a particular report server database.|  
|[SetDatabaseLogonTimeout](../../Topics/TopicNameNotContainA/SetDatabaseLogonTimeout-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the default time-out value for report server database logon attempts.|  
|[SetDatabaseQueryTimeout](../../Topics/TopicNameNotContainA/SetDatabaseQueryTimeout-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the default time-out value for report server database queries.|  
|[SetEmailConfiguration](../../Topics/TopicNameNotContainA/SetEmailConfiguration-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Configures the e-mail delivery extension used by the report server to send e-mail.|  
|[SetSecureConnectionLevel](../../Topics/TopicNameNotContainA/SetSecureConnectionLevel-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Sets the secure connection level of the report server.|  
|[SetServiceState](../../Topics/TopicNameNotContainA/SetServiceState-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Turns the Report Server service on and off.|  
|[SetUnattendedExecutionAccount](../../Topics/TopicNameNotContainA/SetUnattendedExecutionAccount-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Specifies the account used to run reports unattended.|  
|[SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../Topics/TopicNameNotContainA/SetVirtualDirectory-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Sets the virtual directory for an application.|  
|[SetWindowsServiceIdentity](../../Topics/TopicNameNotContainA/SetWindowsServiceIdentity-Method--WMI-MSReportServer_ConfigurationSetting-.md)|Makes the Report Server service run as the specified Windows user, and grants this account sufficient file system permissions to allow the report server to operate.|  
  
## See Also  
 [MSReportServer_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
  