---
title: "Plan for the SMS Provider for System Center Configuration Manager"
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
ms.assetid: 5d5d6273-0d8a-43c7-865a-cdb1736dcae3
caps.latest.revision: 8
---
# Plan for the SMS Provider for System Center Configuration Manager
To manage [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], you use a [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)] which connects to an instance of the **SMS Provider**.   By default, an SMS Provider installs on a central administration site  or primary site, when the site installs.  
  
 This topic is divided into the following subjects:  
  
-   [About the SMS Provider](#BKMK_PlanSMSProv)  
  
-   [SMS Provider locations](#bkmk_location)  
  
-   [About SMS Provider Languages](#BKMK_SMSProvLanguages)  
  
-   [Use multiple SMS Providers](#BKMK_MultiSMSProv)  
  
-   [About the SMS Admins group](#BKMK_AboutSMSAdmins)  
  
-   [About the SMS Provider Namespace](#BKMK_SMSProvNamespace)  
  
-   [Operating System Deployment requirements for the SMS Provider](#BKMK_WAIKforSMSProv)  
  
##  <a name="BKMK_PlanSMSProv"></a> About the SMS Provider  
 The SMS Provider is a Windows Management Instrumentation (WMI) provider that assigns **read** and **write** access to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database at a site:  
  
-   The **SMS Admins**  group provides access to the SMS Provider. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically creates this security group on the site server and on each SMS Provider computer.  
  
-   Each central administration site and primary site require at least one SMS Provider.  You can install additional providers as needed.  
  
-   Secondary sites do not support the SMS Provider.  
  
 Each [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, Resource Explorer, tools, and custom scripts use an SMS Provider so that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] administrative users can access information that is stored in the database. The SMS Provider does not interact with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients. When a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console connects to a site, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console queries WMI on the site server to locate an instance of the SMS Provider to use.  
  
 The SMS Provider helps enforce [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] security. It returns only the information that the administrative user who is running the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console is authorized to view.  
  
> [!IMPORTANT]  
>  When each computer that holds an SMS Provider for a site is offline, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] consoles cannot connect to that site’s database.  
  
 For information about how to manage the SMS Provider, see [Manage the SMS Provider](../System Center Configuration Manager/Modify-your-System-Center-Configuration-Manager-infrastructure.md#BKMK_ManageSMSprovider) in [Modify your System Center Configuration Manager infrastructure](../System Center Configuration Manager/Modify-your-System-Center-Configuration-Manager-infrastructure.md).  
  
 **Prerequisites to install the SMS Provider:**  
  
 To support the SMS Provider:  
  
-   The computer must be in a domain that has a two-way trust with the site server and the site database site systems.  
  
-   The computer cannot have a site system role from a different site.  
  
-   The computer cannot have an SMS Provider from any site.  
  
-   The computer must run an operating system that is supported for a site server.  
  
-   The computer must have at least 650 MB of free disk space to support the Windows Automated Deployment Kit (Windows ADK) components that are installed with the SMS Provider. For more information about Windows ADK and the SMS Provider, see [Operating System Deployment requirements for the SMS Provider](#BKMK_WAIKforSMSProv) in this topic.  
  
##  <a name="bkmk_location"></a> SMS Provider locations  
 When you install a site, the installation automatically installs the first SMS Provider for the site. You can specify any of the following supported locations for the SMS Provider:  
  
-   The site server computer  
  
-   The site database computer  
  
-   A server-class computer that does not hold an SMS Provider, or a site system role from a different site  
  
 To view the locations of each SMS Provider that is installed at a site, view the **General** tab of the site **Properties** dialog box.  
  
 Each SMS Provider supports simultaneous connections from multiple requests. The only limitations on these connections are the number of server connections that are available on the SMS Provider computer, and the available resources on the SMS Provider computer to service the connection requests.  
  
 After a site is installed, you can run Setup on the site server again to change the location of an existing SMS Provider, or to install additional SMS Providers at that site. You can install only one SMS Provider on a computer, and a computer cannot install an SMS Provider from more than one site.  
  
 Use the following to identify the advantages and disadvantages of installing an SMS Provider on each supported location:  
  
 **[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server**  
  
-   **Advantages:**  
  
    -   The SMS Provider does not use the system resources of the site database computer.  
  
    -   This location can provide better performance than an SMS Provider located on a computer other than the site server or site database computer.  
  
-   **Disadvantages:**  
  
    -   The SMS Provider uses system and network resources that could be dedicated to site server operations.  
  
 **SQL Server that is hosting the site database**  
  
-   **Advantages:**  
  
    -   The SMS Provider does not use site system resources on the site server.  
  
    -   This location can provide the best performance of the three locations, if sufficient server resources are available.  
  
-   **Disadvantages:**  
  
    -   The SMS Provider uses system and network resources that could be dedicated to site database operations.  
  
    -   This location is not an option when the site database is hosted on a clustered instance of SQL Server.  
  
 **Computer other than the site server or site database computer**  
  
-   **Advantages:**  
  
    -   SMS Provider does not use site server or site database computer resources.  
  
    -   This type of location lets you deploy additional SMS Providers to provide high availability for connections.  
  
-   **Disadvantages:**  
  
    -   The SMS Provider performance might be reduced due to the additional network traffic that is required to coordinate with the site server and the site database computer.  
  
    -   This server must be always accessible to the site database computer and all computers with the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console installed.  
  
    -   This location can use system resources that would otherwise be dedicated to other services.  
  
##  <a name="BKMK_SMSProvLanguages"></a> About SMS Provider Languages  
 The SMS Provider operates independently of the display language of the computer where it is installed.  
  
 When an administrative user or [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] process requests data by using the SMS Provider, the SMS Provider attempts to return that data in a format that matches the operating system language of the requesting computer. The SMS Provider does not translate information from one language to another. Instead, when data is returned for display in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, the display language of the data depends on the source of the object and type of storage.  
  
 When data for an object is stored in the database, the languages that will be available depend on the following:  
  
-   Objects that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] creates are stored in the database by using support for multiple languages. The object is stored by using the languages that are configured at the site where the object is created when you run Setup. These objects are displayed in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console in the display language of the requesting computer, when that language is available for the object. If the object cannot be displayed in the display language of the requesting computer, it is displayed in the default language, which is English.  
  
-   Objects that an administrative user creates are stored in the database by using the language that was used to create the object. These objects display in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console in this same language. They cannot be translated by the SMS Provider and do not have multiple language options.  
  
##  <a name="BKMK_MultiSMSProv"></a> Use multiple SMS Providers  
 After a site completes installation, you can install additional SMS Providers for the site. To install additional SMS Providers, run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup on the site server. Consider installing additional SMS Providers when any of the following is true:  
  
-   You will have a large number of administrative users that run a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and connect to a site at the same time.  
  
-   You will use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SDK, or other products, that might introduce frequent calls to the SMS Provider.  
  
-   You want to ensure high availability for the SMS Provider.  
  
 When multiple SMS Providers are installed at a site and a connection request is made, the site non-deterministically assigns each new connection request to use an installed SMS Provider. You cannot specify the SMS Provider location to use with a specific connection session.  
  
> [!NOTE]  
>  Consider the advantages and disadvantages of each SMS Provider location and balance these considerations with the information that you cannot control which SMS Provider will be used for each new connection.  
  
 For example, when you first connect a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to a site, the connection queries WMI on the site server to non-deterministically identify an instance of the SMS Provider that the console will use. This specific instance of the SMS Provider remains in use by the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console until the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console session ends. If the session ends because the SMS Provider computer becomes unavailable on the network, when you reconnect the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console the site will non-deterministically assign an SMS Provider computer to the new connection session. It is possible to be assigned to the same SMS Provider computer that is not available. If this occurs, you can attempt to reconnect the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console until an available SMS Provider computer is assigned.  
  
##  <a name="BKMK_AboutSMSAdmins"></a> About the SMS Admins group  
 You use the SMS Admins group to provide administrative users access to the SMS Provider. The group is automatically created on the site server when the site installs, and on each computer that installs an SMS Provider. Additional information about the SMS Admins group:  
  
-   When the computer is a member server, the SMS Admins group is created as a local group.  
  
-   When the computer is a domain controller, the SMS Admins group is created as a domain local group.  
  
-   When the SMS Provider is uninstalled from a computer, the SMS Admins group is not removed from the computer.  
  
 Before a user can make a successful connection to an SMS Provider, their user account must be a member of the SMS Admins group. Each administrative user that you configure in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console is automatically added to the SMS Admins group on each site server and to each SMS Provider computer in the hierarchy. When you delete an administrative user from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, that user is removed from the SMS Admins group on each site server and on each SMS Provider computer in the hierarchy.  
  
 After a user makes a successful connection to the SMS Provider, role-based administration determines what [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] resources that user can access or manage.  
  
 You can view and configure SMS Admins group rights and permissions by using the WMI Control MMC snap-in. By default, **Everyone** has **Execute Methods**, **Provider Write**, and **Enable Account** permissions. After a user connects to the SMS Provider, that user is granted access to data in the site database based on their role-based administrative security rights as defined in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. The SMS Admins group is explicitly granted **Enable Account** and **Remote Enable** on the **Root\SMS** namespace.  
  
> [!NOTE]  
>  Each administrative user who uses a remote [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console requires Remote Activation DCOM permissions on the site server computer and on the SMS Provider computer. Although you can grant these rights to any user or group, as best practice, grant them to the SMS Admins group to simplify administration. For more information, see the [Configure DCOM permissions for remote Configuration Manager consoles](../System Center Configuration Manager/Modify-your-System-Center-Configuration-Manager-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) section in the [Modify your System Center Configuration Manager infrastructure](../System Center Configuration Manager/Modify-your-System-Center-Configuration-Manager-infrastructure.md) topic.  
  
##  <a name="BKMK_SMSProvNamespace"></a> About the SMS Provider Namespace  
 The structure of the SMS Provider is defined by the WMI schema. Schema namespaces describe the location of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] data within the SMS Provider schema. The following table contains some of the common namespaces that are used by the SMS Provider.  
  
|Namespace|Description|  
|---------------|-----------------|  
|Root\SMS\site_*<site code\>*|The SMS Provider, which is extensively used by the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, Resource Explorer, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] tools, and scripts.|  
|Root\SMS\SMS_ProviderLocation|Provides the location of the SMS Provider computers for a site.|  
|Root\CIMv2|Location inventoried for WMI namespace information during hardware and software inventory.|  
|Root\CCM|[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client configuration policies and client data.|  
|root\CIMv2\SMS|Location of inventory reporting classes that are collected by the inventory client agent. These settings are compiled by clients during computer policy evaluation and are based on the client settings configuration for the computer.|  
  
##  <a name="BKMK_WAIKforSMSProv"></a> Operating System Deployment requirements for the SMS Provider  
 The SMS Provider requires the following external dependency be installed on the computer that runs the SMS Provider to enable you to use operating system deployment task functions by using the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console:  
  
-   Windows Assessment and Deployment Kit 8.1  
  
 When you manage operating system deployments, the  Windows ADK allows the SMS Provider to complete various tasks, which include the following:  
  
-   View WIM file details  
  
-   Add driver files to existing boot images  
  
-   Create boot .ISO files  
  
 The Windows ADK installation can require up to 650 MB of free disk space on each computer that installs the SMS Provider. This high disk space requirement is necessary for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to install the Windows PE boot images.  
  
## See Also  
 [Design a hierarchy of sites for System Center Configuration Manager](../System Center Configuration Manager/Design-a-hierarchy-of-sites-for-System-Center-Configuration-Manager.md)