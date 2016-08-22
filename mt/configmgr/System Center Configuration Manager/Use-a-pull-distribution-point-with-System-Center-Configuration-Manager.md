---
title: "Use a pull-distribution point with System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 15a1a2aa-854a-45df-aeb4-35de0189ac80
caps.latest.revision: 5
---
# Use a pull-distribution point with System Center Configuration Manager
A pull-distribution point for [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] is a standard distribution point that obtains distributed content by downloading that from a source location like a client, instead of having the content pushed to it from the site server.  
  
 When you deploy content to a large number of distribution points at a site, pull-distribution points can help reduce the processing load on the site server and can help to speed the transfer of the content to each distribution point. This efficiency is achieved by offloading the process of transferring the content to each distribution point from the distribution manager process on the site server.  
  
-   You  configure individual distribution points to be pull-distribution points.  
  
-   For each pull-distribution point you must specify one or more source distribution points that it can get deployments from (a pull-distribution point can only obtain content from a distribution point that is specified as a source distribution point).  
  
-   When you distribute content to a pull-distribution point, the site server notifies the pull-distribution point which then initiates the download (transfer) of the content from a source distribution point. A pull-distribution point individually manages the transfer of content by downloading content from a distribution point that already has a copy of the content.  
  
 Pull-distribution points support the same configurations and functionality as typical [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] distribution points. For example, a distribution point that is configured as a pull-distribution point supports the use of multicast and PXE configurations, content validation, and on-demand content distribution. A pull-distribution point supports HTTP or HTTPS communications from clients, supports the same certificates options as other distribution points, and can be managed individually or as a member of a distribution point group.  
  
> [!IMPORTANT]  
>  Although a pull-distribution point supports communications over HTTP and HTTPS, when you use the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)], you can only specify source distribution points that are configured for HTTP. You can use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SDK to specify a source distribution point that is configured for HTTPS.  
  
 **The following sequence of events occurs when you distribute content to a pull-distribution point:**  
  
-   As soon as content is distributed to a pull-distribution point, the Package Transfer Manager on the site server checks the site database to confirm if the content is available on a source distribution point. If it cannot confirm that the content is on a source distribution point for the pull-distribution point, it repeats the check every 20 minutes until the content is available.  
  
-   When the Package Transfer Manager confirms that the content is available, it notifies the pull-distribution point to download the content. When the pull-distribution point receives this notification, it attempts to download the content from its source distribution points.  
  
-   After the pull-distribution point completes the download of content, it submits this status to a management point. However, if after 60 minutes, this status is not received, the Package Transfer Manager wakes up and checks with the pull-distribution point to confirm if the pull-distribution point has downloaded the content. If the content download is in progress, the Package Transfer Manager sleeps for 60 minutes before it checks with the pull-distribution point again. This cycle continues until the pull-distribution point completes the content transfer.  
  
 **You can configure a pull-distribution point** when you install the distribution point or after it is installed by editing the properties of the distribution point site system role.  
  
 Y**You can remove the configuration to be a pull-distribution point** by editing the properties of the distribution point. When you remove the pull-distribution point configuration, the distribution point returns to normal operation, and the site server manages future content transfers to the distribution point.  
  
## Limitations for pull-distribution points  
  
-   A cloud-based distribution point cannot be configured as a pull-distribution point.  
  
-   A distribution point on a site server cannot be configured as a pull-distribution point.  
  
-   **The prestage content configuration overrides the pull-distribution point configuration**. A pull-distribution point that is configured for prestaged content waits for the content. It does not pull content from source distribution point, and, like a standard distribution point that has the prestage content configuration, does not receive content from the site server.  
  
-   **A pull-distribution point does not use configurations for rate limits** when it transfers content. If you configure a previously installed distribution point to be a pull-distribution point, configurations for rate limits are saved, but not used. If, at a later time, you remove the pull-distribution point configuration, the rate limit configurations are implemented as previously configured.  
  
    > [!NOTE]  
    >  When a distribution point is configured as a pull-distribution point, the **Rate Limits** tab is not visible in the properties of the distribution point.  
  
-   A pull-distribution point does not use the **Retry settings** for content distribution. **Retry Settings** can be configured as part of the **Software Distribution Component Properties** for each site. To view or configure these properties, in the **Administration** workspace of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, expand **Site Configuration**, and then select **Sites**. Next, in the results pane, select a site, and then on the **Home** tab, select **Configure Site Components**, and then select **Software Distribution**.  
  
-   To transfer content from a source distribution point in a remote forest, the computer that hosts the pull-distribution point must have a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client installed., and a Network Access Account that can access the source distribution point must be configured for use.  
  
-   On a computer that is configured as a pull-distribution point and that runs a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, the version of the  client must be the same as the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site that installs the pull-distribution point. This is a requirement for the pull-distribution point to use the CCMFramework that is common to both the pull-distribution point and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
## About source distribution points  
 When you configure the pull-distribution point, you must specify one or more source distribution points:  
  
-   Only distribution points that qualify to be source distribution points are displayed.  
  
-   A pull-distribution point can be specified as a source distribution point for another pull-distribution point.  
  
-   Only distribution points that support HTTP can be specified as a source distribution points when you use the [!INCLUDE[cmconsole](../System Center Configuration Manager/itokens/cmconsole_md.md)].  
  
-   You can use the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SDK to specify a source distribution point that is configured for HTTPS. To use a source distribution point that is configured for HTTPS, the pull-distribution point must be co-located on a computer that runs the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
 Each distribution point on a pull-distribution points source distribution point list can be assigned a priority:  
  
-   You can assign a separate priority to each source distribution point, or assign multiple source distribution points to the same priority.  
  
-   The priority determines in which order the pull-distribution point requests content from its source distribution points.  
  
-   Pull-distribution points initially contact a source distribution point with the lowest value for priority.  If there are multiple source distribution points with the same priority, the pull-distribution point nondeterministically selects one of the source distribution points that share that priority.  
  
-   When the content is not available on a selected source, the pull-distribution point then attempts to download the content from another distribution point with that same priority.  
  
-   If none of the distribution points with a given priority has the content, the pull-distribution point attempts to download the content from a distribution point that has an assigned priority with the next larger value, until the content is either located or the pull-distribution point sleeps for 30 minutes before it begins the process again.  
  
 When a pull-distribution point downloads content from a source distribution point, that pull-distribution point is counted as a client in the **Client Accessed (Unique)** column of the **Distribution point usage summary** report.  
  
 By default, a pull-distribution point uses its **computer account** to transfer content from a source distribution point. However, when the pull-distribution point transfers content from a source distribution point that is in a remote forest, the pull-distribution point always uses the Network Access Account. This process requires that the computer has the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client installed and that a Network Access Account is configured for use and has access to the source distribution point.  
  
## About content transfers  
 To manage the transfer of content, pull-distribution points use the **CCMFramework** component of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client software.  
  
-   This framework is installed by the **Pulldp.msi** when you configure the distribution point to be a pull-distribution point and does not require that the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client be installed.  
  
-   After the pull-distribution point is installed, the CCMExec service on the distribution point computer must be operational for the pull-distribution point to function.  
  
-   When the pull-distribution point transfers content, it transfers content by using **Background Intelligent Transfer Service** (BITS) and logs its operation in the **datatransferservice.log** and the **pulldp.log** on the distribution point computer.  
  
## See Also  
 [Fundamental concepts for content management in System Center Configuration Manager](../System Center Configuration Manager/Fundamental-concepts-for-content-management-in-System-Center-Configuration-Manager.md)   
 [Plan for System Center Configuration Manager infrastructure](../System Center Configuration Manager/Plan-for-System-Center-Configuration-Manager-infrastructure.md)