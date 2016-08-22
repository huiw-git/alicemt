---
title: "How to assign clients to a site in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-04-21
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: ba9b623f-6e86-4006-93f2-83d563de0cd0
caps.latest.revision: 10
---
# How to assign clients to a site in System Center Configuration Manager
After a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] client is installed, it must join a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] primary site before it can be managed. The site that a client joins is referred to as its assigned site. Clients cannot be assigned to a central administration site or to a secondary site.  
  
 The assignment process occurs after the client is successfully installed and determines which site manages the client computer. When you install the mobile device client during [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] enrollment, this process always automatically assigns the mobile device to a site. When you install the client on a computer, you can also assign the client to a site or you can just install the client without assigning it to a site. However, when the client is installed but not assigned, the client is unmanaged until site assignment is successful.  
  
 To assign a client computer, you can either directly assign the client to a site, or you can use automatic site assignment where the client automatically finds an appropriate site based on its current network location or a fallback site that has been configured for the hierarchy.  
  
> [!NOTE]  
>  Always assign clients to sites from the same version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. Avoid assigning a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client from a newer release to a site from an older release.   If necessary, update the primary site to same [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] version you are using for the clients.  
  
 After the client is assigned to a site, it remains assigned to that site, even if the client changes its IP address and roams to another site. Only an administrator can later manually assign the client to another site or remove the client assignment.  
  
> [!WARNING]  
>  An exception to a client remaining assigned to a site is if you assign the client on a Windows Embedded device when the write filters are enabled. If you do not first disable write filters before you assign the client, the site assignment status of the client reverts to its original state when the device next restarts.  
>   
>  For example, if the client is configured for automatic site assignment, it will reassign on startup and might be assigned to a different site. If the client is not configured for automatic site assignment but requires manual site assignment, you must manually reassign the client after startup before you can manage this client again by using [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
>   
>  To avoid this behavior, disable the write filters before you assign the client on embedded devices, and then enable the write filters after you have verified that site assignment was successful.  
  
 If the client fails to assign to a site, the client software remains installed, but will be unmanaged. A client is considered unmanaged when it is installed but not assigned to a site, or is assigned to a site but cannot communicate with a management point.  
  
 Use the following sections for more information about client site assignment:  
  
-   [Using Manual Site Assignment for Computers](#BKMK_ManualAssignment)  
  
-   [Using Automatic Site Assignment for Computers](#BKMK_AutomaticAssignment)  
  
-   [Completing Site Assignment by Checking Site Compatibility](#BKMK_SiteCompatibility)  
  
-   [Locating Management Points](#BKMK_LocatingMPs)  
  
-   [Downloading Site Settings](#BKMK_DownloadSiteSettings)  
  
-   [Verifying Site Assignment](#BKMK_VerifyAssignment)  
  
-   [Roaming to Other Sites](#BKMK_Roaming)  
  
##  <a name="BKMK_ManualAssignment"></a> Using Manual Site Assignment for Computers  
 You can manually assign client computers to a site by using the following two methods:  
  
-   Use a client installation property that specifies the site code.  
  
-   In Control Panel, in **Configuration Manager**, specify the site code.  
  
> [!NOTE]  
>  If you manually assign a client computer to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site code that does not exist, the site assignment fails. The client remains installed but unmanaged until it is assigned to a valid [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site.  
  
##  <a name="BKMK_AutomaticAssignment"></a> Using Automatic Site Assignment for Computers  
 Automatic site assignment can occur during client deployment, or when you click **Find Site** in the **Advanced** tab of the **Configuration Manager Properties** in the Control Panel. The Configuration Manager client compares its own network location with the boundaries that are configured in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. When the network location of the client falls within a boundary group that is enabled for site assignment, or the hierarchy is configured for a fallback site, the client is automatically assigned to that site without your having to specify a site code.  
  
 You can configure boundaries by using one or more of the following:  
  
-   IP subnet  
  
-   Active Directory site  
  
-   IP v6 prefix  
  
-   IP address range  
  
> [!NOTE]  
>  If a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client has multiple network adapters (possibly a LAN network adapter and a dial-up modem), and therefore has multiple IP addresses, the IP address used to an evaluate client site assignment is nondeterministic.  
  
 For information about how to configure boundary groups for site assignment and how to configure a fallback site for automatic site assignment, see [Define site boundaries and boundary groups for System Center Configuration Manager](../System Center Configuration Manager/Define-site-boundaries-and-boundary-groups-for-System-Center-Configuration-Manager.md).  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients that use automatic site assignment attempt to find site boundary groups that are published to Active Directory Domain Services. If this method fails (for example, the Active Directory schema is not extended for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], or clients are workgroup computers), clients can find boundary group information from a management point.  
  
 You can specify a management point for client computers to use when they are installed, or clients can locate a management point by using DNS publishing or WINS.  
  
 If the client cannot find a site that is associated with a boundary group that contains its network location, and the hierarchy does not have a fallback site, the client retries every 10 minutes until it can be assigned to a site.  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client computers cannot be automatically assigned to a site if any of the following scenarios apply, and instead, they must be manually assigned:  
  
-   They are currently assigned to a site.  
  
-   They are on the Internet or configured as Internet-only clients.  
  
-   Their network location does not fall within one of the configured boundary groups in the Configuration Manager hierarchy, and there is no fallback site for the hierarchy.  
  
##  <a name="BKMK_SiteCompatibility"></a> Completing Site Assignment by Checking Site Compatibility  
 After a client has found its assigned site, the version and operating system of the client is checked to ensure that a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site can manage it. For example, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot manage [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] clients, [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] clients, or clients that are running Windows 2000.  
  
 Whereas site assignment fails if you assign a client that runs Windows 2000 to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site, when you assign a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] client or a[!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] client  to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) site, site assignment succeeds to support automatic client upgrade. However, until the older generation clients are upgraded to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch)  client, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot manage this client by using client settings, applications, or software updates.  
  
> [!NOTE]  
>  To support the site assignment of a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] or a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] client to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) site, you must configure automatic client upgrade for the hierarchy. For more information, see the [How to upgrade clients for Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-upgrade-clients-for-Windows-computers-in-System-Center-Configuration-Manager.md).  
  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] also checks that you have assigned the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) client to a site that supports it. The following scenarios might occur during a migration period when you migrate from previous versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
-   Scenario: You have used automatic site assignment and your boundaries overlap with boundaries defined in a previous version of[!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
     In this case, the client automatically tries to find a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) site.  
  
     The client first checks Active Directory Domain Services and if it finds a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) site published, site assignment succeeds. If this is not successful (for example, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) site is not published or the computer is a workgroup client), the client then checks for site information from its assigned management point.  
  
    > [!NOTE]  
    >  You can assign a management point to the client during client installation by using the Client.msi property **SMSMP=<server_name>**.  
  
     If both these methods fail, site assignment fails and you must manually assign the client.  
  
-   Scenario: You have assigned the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) client by using a specific site code rather than automatic site assignment, and mistakenly specified a site code for a version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] earlier than [!INCLUDE[sccm2012r2_1](../System Center Configuration Manager/itokens/sccm2012r2_1_md.md)].  
  
     In this case, site assignment fails and you must manually reassign the client to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] (current branch) site.  
  
 The site compatibility check requires one of the following conditions:  
  
-   The client can access site information published to Active Directory Domain Services.  
  
-   The client can communicate with a management point in the site.  
  
 If the site compatibility check fails to finish successfully, the site assignment fails, and the client remains unmanaged until the site compatibility check finishes successfully when it is run again.  
  
 The exception to performing the site compatibility check occurs when a client is configured for an Internet-based management point. In this scenario, no site compatibility check is made. If you are assigning clients to a site that contains Internet-based site systems, and you specify an Internet-based management point, ensure that you are assigning the client to the correct site. If you mistakenly assign the client to a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] site,  a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] site, or to a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that does not have Internet-based site system roles, the client will be unmanaged.  
  
##  <a name="BKMK_LocatingMPs"></a> Locating Management Points  
 After a client is successfully assigned to a site, it locates a management point in the site.  
  
 Client computers download a list of management points in the site that they can connect to. This process happens whenever the client restarts, every 25 hours, and if the client detects a network change, such as the computer disconnects and reconnects on the network or it receives a new IP address. The list includes management points on the intranet and whether they accept client connections over HTTP or HTTPS. When the client computer is on the Internet and the client doesn’t yet have a list of management points, it connects to the specified Internet-based management point to obtain a list of management points. When the client has a list of management points for its assigned site, it then selects one to connect to:  
  
-   When the client is on the intranet and it has a valid PKI certificate that it can use, the client chooses HTTPS management points before HTTP management points. It then locates the closest management point, based on its forest membership.  
  
-   When the client is on the Internet, it non-deterministically chooses one of the Internet-based management points.  
  
 Mobile device clients that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] only connect to one management point in their assigned site and never connect to management points in secondary sites. These clients always connect over HTTPS and the management point must be configured to accept client connections over the Internet. When there is more than one management point for mobile device clients in the primary site, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] non-deterministically chooses one of these management points during assignment and the mobile device client continues to use the same management point.  
  
 When the client has downloaded client policy from a management point in the site, the client is then a managed client.  
  
##  <a name="BKMK_DownloadSiteSettings"></a> Downloading Site Settings  
 After site assignment succeeds, and the client has found a management point, a client computer that uses Active Directory Domain Services for its site compatibility check downloads client-related site settings for its assigned site. These settings include the client certificate selection criteria, whether to use a certificate revocation list, and the client request port numbers. The client continues to check these settings on a periodic basis.  
  
 When client computers cannot obtain site settings from Active Directory Domain Services, they download them from their management point. Client computers can also obtain the site settings when they are installed by using client push, or you specify them manually by using CCMSetup.exe and client installation properties. For more information about the client installation properties, see [About client installation properties in System Center Configuration Manager](../System Center Configuration Manager/About-client-installation-properties-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_DownloadClientSettings"></a> Downloading Client Settings  
 All clients download the default client settings policy and any applicable custom client settings policy. Software Center relies on these client configuration policies for Windows computers and will notify users that Software Center cannot run successfully until this configuration information is downloaded. Depending on the client settings that are configured, the initial download of client settings might take a while, and some client management tasks might not run until this process is complete.  
  
##  <a name="BKMK_VerifyAssignment"></a> Verifying Site Assignment  
 You can verify that site assignment is successful by using any of the following methods:  
  
-   For clients on Windows computers, use [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] in the Control Panel and verify that the site code is correctly displayed on the **Site** tab.  
  
-   For client computers, in the **Assets and Compliance** workspace, use the **Devices** node to verify that the computer displays **Yes** for the **Client** column and the correct primary site code for the **Site Code** column.  
  
-   For mobile device clients, in the **Assets and Compliance** workspace, use the **All Mobile Devices** collection to verify that the mobile device displays **Yes** for the **Client** column and the correct primary site code for the **Site Code** column.  
  
-   Use the reports for client assignment and mobile device enrollment.  
  
-   For client computers, use the LocationServices.log file on the client.  
  
##  <a name="BKMK_Roaming"></a> Roaming to Other Sites  
 When client computers on the intranet are assigned to a primary site but change their network location so that it falls within a boundary group that is configured for another site, they have roamed to another site. When this site is a secondary site for their assigned site, clients can use a management point in the secondary to download client policy and upload client data, which avoids sending this data over a potentially slow network. However, if these clients roam into the boundaries for another primary site or a secondary that is not a child site of their assigned site, these clients always use a management point in their assigned site to download client policy and to upload data to their site.  
  
 These client computers that roam to other sites (all primary sites and all secondary sites) can always use management points in other sites for content location requests. Management points in the current site can give clients a list of distribution points that have the content that clients request.  
  
 For client computers that are configured for Internet-only client management, and for Mac computers and mobile devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], these clients only communicate with management points in their assigned site. These clients never communicate with management points in secondary sites or with management points in other primary sites.  
  
## See Also  
 [Client deployment tasks for System Center Configuration Manager](../System Center Configuration Manager/Client-deployment-tasks-for-System-Center-Configuration-Manager.md)