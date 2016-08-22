---
title: "Planning for Endpoint Protection in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 7610bbd3-a67f-4a09-8115-e35d40d43b42
caps.latest.revision: 16
---
# Planning for Endpoint Protection in System Center Configuration Manager
Use the following topics in this section to help you plan to use [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)].  
  
## Administrator Workflow for Endpoint Protection in Configuration Manager  
 Use the following workflow as a reference to help you enable, configure, and manage and monitor Endpoint Protection in System Center 2012 Configuration Manager.  
  
|Step|More information|  
|----------|----------------------|  
|Review the prerequisites information for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)].|[Planning for Endpoint Protection in Configuration Manager](../System Center Configuration Manager/Planning-for-Endpoint-Protection-in-System-Center-Configuration-Manager.md).|  
|Create an [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] point site system role.|[Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md).|  
|Configure alerts for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)].|[Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md)|  
|Configure definition update methods to update client computers.|See "How to Configure Definition Updates for Endpoint Protection in Configuration Manager" in [Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md)|  
|Configure antimalware settings for collections of computers.|[How to create and deploy antimalware policies for Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-and-deploy-antimalware-policies-for-Endpoint-Protection-in-System-Center-Configuration-Manager.md)|  
|Configure client settings for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)].|[Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md)|  
|Create and deploy firewall policies to collections of computers.|[How to create and deploy Windows Firewall policies for Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-create-and-deploy-Windows-Firewall-policies-for-Endpoint-Protection-in-System-Center-Configuration-Manager.md).|  
|Monitor [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] activity.|[How to monitor Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-Endpoint-Protection-in-System-Center-Configuration-Manager.md) .|  
  
## Prerequisites for Endpoint Protection in Configuration Manager  
 Endpoint Protection in System Center 2012 Configuration Manager has external dependencies and dependencies in the product.  
  
### Dependencies External to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
 The following table lists the external dependencies for running [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
 **Dependencies**  
  
-   Windows Server Update Services (WSUS) must be installed and configured for software updates synchronization if you want to use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] software updates to deliver definition and engine updates. See [Prerequisites for software updates in System Center Configuration Manager](../System Center Configuration Manager/Prerequisites-for-software-updates-in-System-Center-Configuration-Manager.md)  
  
-   Some definition update methods require that client computers have Internet access. If you use any of the following methods to update definitions on client computers, the client computer must be able to access the Internet:  
  
    -   Updates distributed from Microsoft Update  
  
    -   Updates distributed from Microsoft Malware Protection Center  
  
    > [!IMPORTANT]  
    >  Clients download definition updates by using the built-in System account. You must configure a proxy server for this account to enable these clients to connect to the Internet. You can use Windows Group Policy to configure a proxy server on multiple computers.  
  
-   An SMTP server if you want to send email alerts. See Step 1 (Optional): Configure Email Settings for Alerts in the [Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md) topic.  
  
-   Hotfix requirement to deploy Windows Firewall policies. If you want to deploy Windows Firewall policies to computers running Windows Server 2008 and Windows Vista Service Pack 1, you must first install [Hotfix KB971800](http://go.microsoft.com/fwlink/p/?LinkId=231239) on these computers.  
  
### Configuration Manager Dependencies  
 The following table lists the dependencies within [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] for running [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)].  
  
 **Dependencies**  
  
-   Your standalone primary or central administration site must be running [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] and have the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] point site system role installed and configured. For more information about the requirements for the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] point site system role, see the Site System Requirements section of the [Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md). For more information about to install this site system role, see [Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md).  
  
    > [!IMPORTANT]  
    >  The Endpoint Protection point site system role must be installed before you can use Endpoint Protection. It must be installed on one site system server only, and it must be installed at the top of the hierarchy on a central administration site or a stand-alone primary site.  
  
-   A software update point site system role must be installed and configured to deliver definition updates if you want to use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] software updates to deliver definition and engine updates. For more information about the requirements for the software update point site system role, sesee the Site System Requirements section of the [Supported configurations for System Center Configuration Manager](../System Center Configuration Manager/Supported-configurations-for-System-Center-Configuration-Manager.md). For more information about how to install this site system role and configure it for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)], see [Configure software updates in System Center Configuration Manager](../System Center Configuration Manager/Configure-software-updates-in-System-Center-Configuration-Manager.md) and [Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md).  
  
-   Client settings that install the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] client and configure Endpoint Protection. For more information about how to configure the client settings for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)], see "Configure Custom Client Settings" in [Configuring Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Configuring-Endpoint-Protection-in-System-Center-Configuration-Manager.md).  
  
-   The reporting services point site system role must be installed before [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] reports can be displayed. See [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md)  
  
-   Security permissions to manage [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)]. You must have the following security permissions to manage [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)]:  
  
    -   To create and manage subscriptions to [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] alerts: **Create**, **Delete**, **Modify**, **Read**, **Set Security Scope** for the **Alert Subscription** object.  
  
    -   To create and modify alerts for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)]: **Create**, **Delete**, **Modify**, **Modify Report**, **Read**, **Run Report** for the **Alerts** object.  
  
    -   To create and modify antimalware policies: **Create**, **Delete**, **Modify**, **Modify Default**, **Modify Report**, **Read**, **Read Default**, **Run Report** for the **Antimalware Policy** object.  
  
    -   To deploy antimalware and Windows Firewall policies to computers: **Audit Security**, **Delete**, **Deploy Antimalware Policies**, **Deploy Firewall Policies**, **Enforce Security**, **Read**, **Read Resource** for the  **Collection** object.  
  
    -   To view and manage [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console: **Read** permissions for the **Site** object.  
  
    -   To create and modify Windows Firewall policies: **Create Policy**, **Delete Policy**, **Modify Policy**, **Read Policy**, **Read Settings** for the **Windows Firewall Policy** object.  
  
     The **[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] Manager** security role includes these permissions that are required to manage [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
    > [!NOTE]  
    >  To perform the following actions, you must be a member of the **Full Administrator** security role.  
    >   
    >  -   Configure the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] point site system role.  
    > -   Configure email notification for Endpoint Protection alerts.  
  
## Best Practices for Endpoint Protection in Configuration Manager  
 Use the following best practices for Endpoint Protection in System Center 2012 Configuration Manager.  
  
### Configure custom client settings for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)]  
 When you configure client settings for [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)], do not use the default client settings because they apply settings to all computers in your hierarchy. Instead, configure custom client settings and assign these settings to collections of computers in your hierarchy.  
  
 When you configure custom client settings, you can do the following:  
  
-   Customize antimalware and security settings for different parts of your organization.  
  
-   Test the effects of running [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] on a small group of computers before you deploy it to the entire hierarchy.  
  
-   Add more clients to the collection over time to phase your deployment of the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] client.  
  
### Distributing definition updates by using software updates  
 If you are using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] software updates to distribute definition updates, consider placing definition updates in a package that does not contain other software updates. This keeps the size of the definition update package smaller which allows it to replicate to distribution points more quickly.