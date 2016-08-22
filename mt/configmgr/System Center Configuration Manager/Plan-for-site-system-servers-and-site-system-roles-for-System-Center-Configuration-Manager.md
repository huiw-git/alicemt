---
title: "Plan for site system servers and site system roles for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 0a7415ba-2c53-4433-983e-780e92aa662f
caps.latest.revision: 11
---
# Plan for site system servers and site system roles for System Center Configuration Manager
Each [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site you install includes a  a site server which is a **site system server**. The site can also include additional site system servers on computers that are remote from the site server.   Site system servers (the site server or a remote site system server) support **site system roles**.  The following subjects are included in this topic:  
  
-   [Site system servers](#bkmk_siteservers)  
  
-   [Site system roles](#bkmk_planroles)  
  
-   [Site system roles that can use a proxy server](#bkmk_proxy)  
  
##  <a name="bkmk_siteservers"></a> Site system servers  
 When you install a site system role on a  computer, that computer becomes a site system server. At each site you can install one or more additional site system servers. You can also choose to not install additional site system servers and run all site system roles directly on the site server computer.  Each site system server supports one or more site system roles and helps expand the capabilities and capacity of a site by sharing the CPU processing load that site system roles place on a server.  
  
 When considering the addition of a site system server, ensure the server meets prerequisites for the intended use, and is on a network location that has sufficient bandwidth to communicate with expected endpoints, including the site server, domain resources, cloud-based location, site system servers, and clients).  
  
 If you configure the site system server with a proxy for use by site system roles, see [Site system roles that can use a proxy server](#bkmk_proxy)  
  
##  <a name="bkmk_planroles"></a> Site system roles  
 Site system roles are installed on a computer to provide additional capabilities to the site. Examples include:  
  
-   Additional management points so that the site can support more devices, up to the sites supported capacity  
  
-   Additional distribution points to expand your content infrastructure, improving the performance of content distributions to devices and users  
  
-   One or more feature specific site system roles like a software update point, which you use to manage software updates for managed devices, or a reporting services point so you can run reports to monitor and understand or share information about your deployment  
  
 Different [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites can support a different sets of site system roles. The supported site system roles depends on the type of site (a central administration site, primary site, or secondary site). The topology of your hierarchy can limit the placement of some roles at ceratin site types. For example, the service connection point is only supported at the top-tier site of the hierarchy, which might be a central administration site or a stand-alone primary site. This role is not supported at a child primary site or at secondary sites.  
  
 After a site installs, you can move the  location of some site system roles from their default location on the site server to another server (like the management point or distribution point that install by default on a primary or secondary site server). You can also install additional instances of some site system roles to expand the capabilities of your site (provide more services to clients) and to meet your business requirements. Some roles are required, while others are optional:  
  
-   **[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server** - This role identifies the server where [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup is run to install a site, or the server on which you install a secondary site. This role cannot be moved or uninstalled until the site is uninstalled.  
  
-   **[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system** - This role is assigned to any computer where you either install a site or install a site system role.  This role cannot be moved or uninstalled until the last site system role is removed from the computer.  
  
-   **[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] component site system role** - This role identifies a site system that runs an instance of the SMS Executive service, and is required to support other roles, like management points. This role cannot be moved or uninstalled until the last applicable site system role is removed from the computer.  
  
-   **[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site database server** - This role is assigned to site system servers that hold an instance of the site database for a site.  This role can only be moved  to a new server by modifying the site to use a different SQL Server to host the site database.  
  
-   **SMS Provider** - The SMS Provider role is assigned to each computer that hosts an instance of the SMS Provider, the interface between a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console and the site database.  By default, this role installs automatically on the site server of  a central administration site and primary sites, and you can install additional instances  at each site to provide administrative access a site to additional administrative users.  
  
     Unlike most site system roles that install from within the console, to install additional providers you must run Configuration Manager Setup to [Manage the SMS Provider](../System Center Configuration Manager/Modify-your-System-Center-Configuration-Manager-infrastructure.md#BKMK_ManageSMSprovider) and then install additional providers on additional computers. You can only install one instance of the SMS Provider on a computer, and that computer  must be in the same domain as the site server.  
  
-   **Application Catalog web service poin** - A site system role that provides software information to the Application Catalog website from the Software Library. Although this role is supported only at primary sites, you can install multiple instances of this role at a site, or at multiple sites in the same hierarchy.  
  
-   **Application Catalog website point** - A site system role that provides users with a list of available software from the Application Catalog. Although this role is supported only at primary sites, you can install multiple instances of this role at a site, or at multiple sites in the same hierarchy.  
  
     When the Application Catalog supports client computers on the Internet, as a security best practice, install the Application Catalog website point in a perimeter network and the Application Catalog web service point on the intranet.  
  
-   **Asset Intelligence synchronization point** - A site system role that connects to Microsoft to download information for the Asset Intelligence catalog and to upload uncategorized titles so that they can be considered for future inclusion in the catalog.  A hierarchy supports only a single instance of this role, and that must be at the top-tier site of your hierarchy (A central administration site or the stand-alone primary site). If you expand a stand-alone primary site into a larger hierarchy, you must uninstall this role from the primary site and can then install it at the central administration site.   For more information, see [Asset Intelligence in System Center Configuration Manager](../System Center Configuration Manager/Asset-Intelligence-in-System-Center-Configuration-Manager.md).  
  
-   **Certificate registration point** - A site system role that communicates with a server that runs the Network Device Enrollment Service to manage device certificate requests that use the Simple Certificate Enrollment Protocol (SCEP).  This role is supported only at primary sites and the central administration site.   Although a single certificate registration point can provide functionality to an entire hierarchy, to help load balance certificate requests you can install multiple instances of this role at a site, and at multiple sites in the same hierarchy. When multiple instances exist in a hierarchy, clients are randomly assigned to one of the certificate registration points.  
  
     Each certificate registration point requires access to a separate instance of a Network Device Enrollment Service. You cannot configure two or more certificate registration points to use the same Network Device Enrollment Service. Additionally, the certificate registration point must not be installed on the same server that runs the Network Device Enrollment Service.  
  
-   **Distribution point** - A site system role that contains source files for clients to download, such as application content, software packages, software updates, operating system images, and boot images. By default, this role installs on the site server computer of new primary and secondary sites when the site installs, but is not supported at a central administration site.  You can install multiple instances of this role at a supported site, and at multiple sites in the same hierarchy.  For more information, see [Fundamental concepts for content management in System Center Configuration Manager](../System Center Configuration Manager/Fundamental-concepts-for-content-management-in-System-Center-Configuration-Manager.md), and [Manage content and content infrastructure for System Center Configuration Manager](../System Center Configuration Manager/Manage-content-and-content-infrastructure-for-System-Center-Configuration-Manager.md).  
  
-   **Fallback status point** - A site system role that helps you monitor client installation and identify the clients that are unmanaged because they cannot communicate with their management point.  Althgouht this role is supported only at primary sites, you can install multiple instances of this role at a site, and at multiple sites in the same hierarchy.  For more information, see [Content source location scenarios](../System Center Configuration Manager/Content-source-location-scenarios-in-System-Center-Configuration-Manager.md).

  
-   **Endpoint Protection point** - A site system role that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses to accept the Endpoint Protection license terms and to configure the default membership for Microsoft Active Protection Service. A hierarchy supports only a single instance of this role, and that must be at the top-tier site of your hierarchy (A central administration site or the stand-alone primary site). If you expand a stand-alone primary site into a larger hierarchy, you must uninstall this role from the primary site and can then install it at the central administration site. For more information, see  [Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Endpoint-Protection-in-System-Center-Configuration-Manager.md).  
  
-   **Enrollment point** - A site system role that uses PKI certificates for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to enroll mobile devices and Mac computers. Although this role is supported only at primary sites, you can install multiple instances of this role at a site, or at multiple sites in the same hierarchy.  
  
     If a user enrolls mobile devices by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and their Active Directory account is in a forest that is untrusted by the site server's forest, you must install an enrollment point in the user’s forest so that the user can be authenticated.  
  
-   **Enrollment proxy point** - A site system role that manages [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] enrollment requests from mobile devices and Mac computers. Although this role is supported only at primary sites, you can install multiple instances of this role at a site, or at multiple sites in the same hierarchy.  
  
     When you support mobile devices on the Internet, as a security best practice, install the enrollment proxy point in a perimeter network and the enrollment point on the intranet.  
  
-   **Exchange Server connector** - For information see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md)  
  
-   **Management point** - A site system role that provides policy and service location information to clients and receives configuration data from clients.  
    By default, this role installs on the site server computer of new primary and secondary sites when the site installs. Primary sites support multiple instances of this role and secondary sites support a single management point  to provide a local point of contact for clients  to obtain computer and user polices (a management point at secondary site is referred to as a proxy management point).  
  
     Management points can be configured to support HTTP or HTTPs, as well as to support mobile devices you manage with [!INCLUDE[onprem_first](../System Center Configuration Manager/itokens/onprem_first_md.md)]. You can use [Database replicas for management points for System Center Configuration Manager](../System Center Configuration Manager/Database-replicas-for-management-points-for-System-Center-Configuration-Manager.md) to help reduce the CPU load placed on the site database server by management points as they service requests from clients.  
  
-   **Reporting services point** - A site system role that integrates with SQL Server Reporting Services to create and manage reports for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. This role  is supported at primary sites and the central administration site, and you can install multiple instances of this role at a supported site. For more information, see [Planning for reporting in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-reporting-in-System-Center-Configuration-Manager.md).  
  
-   **Service connection point** - A site system role that you use to manage mobile devices with [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] and on-premises MDM. This role also uploads usage data from your site and is required  to make updates for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] available in the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)]. A hierarchy supports only a single instance of this role, and that must be at the top-tier site of your hierarchy (A central administration site or the stand-alone primary site). If you expand a stand-alone primary site into a larger hierarchy, you must uninstall this role from the primary site and can then install it at the central administration site. For more information, see [About the service connection point in System Center Configuration Manager](../System Center Configuration Manager/About-the-service-connection-point-in-System-Center-Configuration-Manager.md).  
  
-   **Software update point** - A site system role that integrates with Windows Server Update Services (WSUS) to provide software updates to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients. This role  is supported at all sites:  
  
    -   Install this site system in the central administration site to synchronize with Windows Server Update Services.  
  
    -   Configure each instance of this  role at  child primary sites to synchronize with the central administration site.  
  
    -   Consider installing a software update point in secondary sites when data transfer across the network is slow.  
  
     For more information, see [Plan for software updates in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-software-updates-in-System-Center-Configuration-Manager.md).  
  
-   **State migration point** - A site system role that stores user state data when a computer is migrated to a new operating system. This role is supported  at primary sites and at secondary sites, and you can install multiple instances of this role at a site, and at multiple sites in the same hierarchy. For more information about storing user state when you deploy an operating system, see [Manage user state in System Center Configuration Manager](../System Center Configuration Manager/Manage-user-state-in-System-Center-Configuration-Manager.md).  
  
-   **System Health Validator point** - This site system role is no longer used with [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] although it remains visible in the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)].  
  
##  <a name="bkmk_proxy"></a> Site system roles that can use a proxy server  
 Some [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site system roles require connections to the Internet and will use a proxy server when the site system server that hosts the role is configured for one. Typically, this connection is made in the **system** context of the computer where the site system role is installed and cannot use a proxy configuration for typical user accounts. When a proxy server is required to complete a connection to the Internet, you must configure the computer to use a proxy server:  
  
-   You can configure a proxy server when installing a site system role.  
  
-   You can add or modify a proxy server configuration when you use  the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)].  
  
-   All site system roles on a site system server that can use a proxy server configuration, use the same proxy server configuration. If you require different site system roles to use different proxy servers, you must install the site system roles on different site system server computers  
  
-   If you modify the proxy server configuration, or install a new site system role on a computer that already has a proxy server configuration, the original configuration is overwritten by the new configuration.  
  
 For procedures about configuring the proxy server for site system roles, see the [Add site system roles for System Center Configuration Manager](../System Center Configuration Manager/Add-site-system-roles-for-System-Center-Configuration-Manager.md) topic.  
  
 The following are site system roles that can use a proxy server:  
  
-   **Asset Intelligence synchronization point** - This site system role connects to Microsoft and will use a proxy server configuration on the computer that hosts the Asset Intelligence synchronization point.  
  
-   **Cloud-based distribution point** - When you use a cloud-based distribution point, the primary site that manages the cloud-based distribution point must be able to connect to Windows Azure to provision, monitor, and distribute content to the distribution point. If a proxy server is required for this connection, you must configure the proxy server on the primary site server. You cannot configure a proxy server on the cloud-based-distribution point in Windows Azure.  For more information see the [Configure proxy settings for primary sites that manage cloud services](../System Center Configuration Manager/Install-cloud-based-distribution-points-in-Microsoft-Azure-for-System-Center-Configuration-Manager.md#BKMK_ConfigProxyforCloud) section in the [Install cloud-based distribution points in Microsoft Azure for System Center Configuration Manager](../System Center Configuration Manager/Install-cloud-based-distribution-points-in-Microsoft-Azure-for-System-Center-Configuration-Manager.md) topic.  
  
-   **Exchange Server connector** - This site system role connects to an Exchange Server and will use a proxy server configuration on the computer that hosts the Exchange Server connector.  
  
-   **Software updates point** - This site system role can require connections to Microsoft Update to download patches and synchronize information about updates. Typically, when you configure the proxy server, each site system role on that computer that supports using the proxy server will use the proxy server with no additional configuration required. An exception to this is the software update point. By default, a software update point does not use an available proxy server unless you also enable the following options when you configure the software update point:  
  
    -   **Use a proxy server when synchronizing software updates**  
  
    -   **Use a proxy server when downloading content by using automatic deployment rules**  
  
    > [!TIP]  
    >  A proxy server must be configured on the site system server that hosts the software update point before you can select either option. The proxy server is only used for the specific options you select.  
  
     For more information about proxy servers for software update points, see the Proxy Server Settings section in the [Configure software updates in System Center Configuration Manager](../System Center Configuration Manager/Configure-software-updates-in-System-Center-Configuration-Manager.md) topic.  
  
-   **Service connection point** - When configured to be online (not offline), this site system role connects to [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] and the Microsoft cloud service.  
  
## See Also  
 [Design a hierarchy of sites for System Center Configuration Manager](../System Center Configuration Manager/Design-a-hierarchy-of-sites-for-System-Center-Configuration-Manager.md)