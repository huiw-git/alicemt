---
title: Deployment Checklist: Install Reporting Services into an Existing SharePoint Farm
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 436b4c3d-3f2f-464a-be7e-5c051d9ffb8f
robots: noindex,nofollow
---
# Deployment Checklist: Install Reporting Services into an Existing SharePoint Farm
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint report servers can be installed into a new SharePoint Farm or into an existing SharePoint farm. This topic describes the possible scenarios and best practices for installing [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] into and existing SharePoint farm.  
  
## Prerequisites  
 Before you run Setup, review the following information:  
  
|Step|Link|  
|----------|----------|  
|Create or identify the accounts used in a report server deployment. You must have a service account for the Report Server service, and credentials for connecting to the report server database||  
|Decide on an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to host the report server database. You can use a local or remote instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. You should choose an instance that is on a computer that has the storage capacity to accommodate your reports.||  
|\(Optional\) Find the name of the SMTP server or gateway that provides e\-mail service to your organization if you want to use report server e\-mail in subscriptions|[Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83)|  
  
## Installation Scenarios  
 The following table describes the possible scenarios when you are installing [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] into and existing SharePoint Farm. Local mode allows reports to be rendered locally from the SharePoint document library, without integration with a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint products is required but a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server is not. For more information on local mode, see [Local Mode vs. Connected Mode Reports in the Report Viewer &#40;Reporting Services in SharePoint Mode&#41;](../Topic/Local%20Mode%20vs.%20Connected%20Mode%20Reports%20in%20the%20Report%20Viewer%20\(Reporting%20Services%20in%20SharePoint%20Mode\).md) and [Where to find the Reporting Services add-in for SharePoint Products](../../Topics\TopicNameNotContainA/Where-to-find-the-Reporting-Services-add-in-for-SharePoint-Products.md).  
  
|Starting Configuration|Workflow|Ending Configuration|  
|----------------------------|--------------|--------------------------|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] in Local mode|Installation|Connected mode [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|  
|Connected Mode [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] or [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]|In place upgrade|Connected mode [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|  
|Connected Mode [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] or [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]|Migration|Connected mode [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|  
  
## Installation and in place Upgrade Checklist  
 The following table summarizes the steps, tools, and information you should review and use for the installation:  
  
|Step|Link|  
|----------|----------|  
|**Installation and initial configuration**||  
|Install the SharePoint add\-in on all Web front\-end \(WFE\) computers.|[Add an Additional Reporting Services Web Front-end to a Farm](../../Topics\TopicNameContainA/Add-an-Additional-Reporting-Services-Web-Front-end-to-a-Farm.md)|  
|Install [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Reporting Services and the Database engine.|[Install Reporting Services SharePoint Mode for SharePoint 2010](assetId:///47efa72e-1735-4387-8485-f8994fb08c8c)|  
|Create at least one SSRS service application and configure service app association.|See the ‘Service Application’ section in [Install Reporting Services SharePoint Mode for SharePoint 2010](assetId:///47efa72e-1735-4387-8485-f8994fb08c8c)|  
|**Additional Configuration**||  
|Add SSRS content types to your document library.|[Add Reporting Services Content Types to a SharePoint Library](../../Topics\TopicNameContainA/Add-Reporting-Services-Content-Types-to-a-SharePoint-Library.md)|  
|Provision SQL Server Agent|[Provision Subscriptions and Alerts for SSRS Service Applications](../../Topics\TopicNameNotContainA/Provision-Subscriptions-and-Alerts-for-SSRS-Service-Applications.md)|  
|Configure e\-mail settings for your Service application|[Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../Topic/Configure%20E-mail%20for%20a%20Reporting%20Services%20Service%20Application%20\(SharePoint%202010%20and%20SharePoint%202013\).md)|  
|Configure Claims to Windows Token Service \(c2WTS\)|[Claims to Windows Token Service &#40;c2WTS&#41; and Reporting Services](../Topic/Claims%20to%20Windows%20Token%20Service%20\(c2WTS\)%20and%20Reporting%20Services.md)|  
  
## Migration Checklist  
 The following is a list of the basic steps for a migration from an existing installation to a new installation.  
  
|Step|Link|  
|----------|----------|  
|Install and configure your new server. This includes the following:<br /><br /> SharePoint Products Preparation Tool<br /><br /> SharePoint 2010 Product<br /><br /> SharePoint 2010 SP1<br /><br /> [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint Mode<br /><br /> [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint 2010 products|[Install Reporting Services SharePoint Mode for SharePoint 2010](assetId:///47efa72e-1735-4387-8485-f8994fb08c8c)|  
|Create at least one [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service application||  
|Backup [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Databases||  
|Backup [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Encryption keys||  
|Restore [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] database and Encryption keys||  
|Map all web applications to new [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]service application\(s\)|The new installation **is now functional**|  
|Remove the Integration URL on the old server.|From SharePoint Central Administration, on the **General Application Settings** Page, click **Reporting Services Integration**.|  
|Uninstall [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] from the old installation, if desired.||  
  
## Next Steps  
  
## See Also  
 [Install Reporting Services SharePoint Mode](../../Topics\TopicNameNotContainA/Install-Reporting-Services-SharePoint-Mode.md)   
 [Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm](assetId:///5f9a94c4-854b-4577-a8b1-7142f19904e3)   
 [Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2016&#41;](../Topic/Supported%20Combinations%20of%20SharePoint%20and%20Reporting%20Services%20Server%20and%20Add-in%20\(SQL%20Server%202016\).md)  
  
  