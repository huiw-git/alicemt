---
title: "Site components for System Center Configuration Manager"
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
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
caps.latest.revision: 9
---
# Site components for System Center Configuration Manager
At each [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] site you can configure site components to modify the behavior of site system roles and site status reporting. Site component configurations apply to a site, and to each instance of an applicable site system role at the  site.  
  
## About site components  
 Most options for the various site components are self-explanatory when viewed in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. However, the following details can help explain some of the more complex configurations or direct you to additional content that does explain them:  
  
 **Software Distribution:**  
  
-   **Content distribution settings:**  You can configure settings that modify how the site server transfers content to its distribution points. When you increase the values you use for concurrent distribution settings, content distribution can use more network bandwidth.  
  
-   **Network Access Account:**  For information about configuring and using the Network Access Account, see [Network Access Account](../System Center Configuration Manager/Manage-accounts-to-access-content-in-System-Center-Configuration-Manager.md#bkmk_NAA)  
  
 **Software Update Point:**  
  
-   For information about  configuration options for the software update point component, see [Configure software updates in System Center Configuration Manager](../System Center Configuration Manager/Configure-software-updates-in-System-Center-Configuration-Manager.md).  
  
 **Management  Point:**  
  
-   **Management points:** You can configure the site to publish information about its management points to Active Directory Domain Services.  
  
     [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients use management points for service location,  to find site information such as boundary group membership and PKI certificate selection options, and to find other management points in the site and distribution points from which to download software. Clients also use management points to complete site assignment and download client policy and upload their client information.  
  
     Because the most secure method for clients to find management points is to publish them in Active Directory Domain Services, you will typically always select all functioning management points to publish to Active Directory Domain Services. However, this service location method requires that the schema is extended for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], there is a **System Management** container with appropriate security permissions for the site server to publish to this container, that the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site is configured to publish to Active Directory Domain Services, and that clients belong to the same Active Directory forest as the site server’s forest.  
  
     When clients on the intranet cannot use Active Directory Domain Services to find management points, use [DNS](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md#bkmk_dns) publishing.  
  
     For general information about service location, see [Understand how clients find site resources and services for System Center Configuration Manager](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md).  
  
-   **Publish selected intranet management points in DNS:** Specify this option when clients on the intranet cannot find management points from Active Directory Domain Services, but they can use a DNS service location resource record (SRV RR) to find a management point in their assigned site.  
  
     For [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to publish intranet management points to DNS, all the following conditions must be met:  
  
    -   Your DNS servers have a version of BIND that is 8.1.2 or later.  
  
    -   Your DNS servers are configured for automatic updates and support service location resource records.  
  
    -   The specified FQDNs for the management points in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] have host entries (A or AAA records) in DNS.  
  
    > [!WARNING]  
    >  For clients to find management points that are published in DNS, you must assign the clients to a specific site (rather than use automatic-site assignment) and configure these clients to use the site code with the domain suffix of their management point. For more information, see  [Locating Management Points](../System Center Configuration Manager/How-to-assign-clients-to-a-site-in-System-Center-Configuration-Manager.md#BKMK_LocatingMPs) in [How to assign clients to a site in System Center Configuration Manager](../System Center Configuration Manager/How-to-assign-clients-to-a-site-in-System-Center-Configuration-Manager.md).  
  
     If [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients cannot use Active Directory Domain Services or DNS to find management points on the intranet, they fall back to using [WINS](../System Center Configuration Manager/Understand-how-clients-find-site-resources-and-services-for-System-Center-Configuration-Manager.md#bkmk_wins). The first management point that is installed for the site is automatically published to WINS when it is configured to accept HTTP client connections on the intranet.  
  
 **Status Reporting:**  
  
-   These settings directly configure the level of detail that is included in status reports from sites and clients.  
  
 **Email Notification:**  
  
-   Specify account and email server details to enable [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] to send email notifications for alerts.  
  
 **Collection Membership Evaluation:**  
  
-   Use this task to set how often collection membership is incrementally evaluated. Incremental evaluation updates a collection membership with only new or changed resources.  
  
#### To edit the site components at a site  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration** > **Site Configuration** > **Sites**, and then select the site that has site components you will configure.  
  
2.  On the **Home** tab, in the **Settings** group, click **Configure Site Components** and then select the site component you want to configure.  
  
##  <a name="BKMK_ServiceMgr"></a> Use the Configuration Manager Service Manager to manage site components  
 You can use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Service Manager to control [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] services and to view the status of any [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] service or working  thread (referred to collectively as [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] components):  
  
-   [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] components can run on any site system.  
  
-   Components are managed the same way that you manage services in Windows; you can start, stop, pause, resume, or query [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] components.  
  
 A [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] service runs when there is something for it to do (typically, when a configuration file is written to a component's inbox). If you have to identify the component involved in an operation, you can use the **[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Service Manager** to manipulate various [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] services and threads and then view the resulting change in the behavior of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. For example, you can stop [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] services one at a time until a particular response is eliminated. Doing so enables you to determine which service causes the behavior.  
  
> [!TIP]  
>  The following procedure can be used to manipulate [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] component operation.  
  
#### To use the Configuration Manager Service Manager  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring** >  **System Status**, and then click **Component Status**.  
  
2.  On the **Home** tab, in the **Component** group, click **Start**, and then select **Configuration Manager Service Manager**.  
  
3.  When the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Service Manager opens, connect to the site that you want to manage.  
  
     If you do not see the site that you want to manage, click **Site**, click **Connect**, and then enter the name of the site server of the correct site.  
  
4.  Expand the site and navigate to **Components** or **Servers** depending on where the components that you want to manage are located.  
  
5.  In the right pane, select one or more components and then on the **Component** menu, click **Query** to update the status of your selection.  
  
6.  After the status of the component is updated, use one of the four action-based options on the **Component** menu to modify the components operation. After you request an action, you must query the component to display the new status of the component.  
  
7.  Close the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Service Manager when you are finished modifying the operational status of components.  
  
## See Also  
 [Configure sites and hierarchies for System Center Configuration Manager](../System Center Configuration Manager/Configure-sites-and-hierarchies-for-System-Center-Configuration-Manager.md)