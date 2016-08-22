---
title: "Reference for maintenance tasks for System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-29
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
caps.latest.revision: 16
caps.handback.revision: 0
---
# Reference for maintenance tasks for System Center Configuration Manager
This topic lists details for each of the System Center Configuration Manager site maintenance tasks, and at which site types the task is available. Each entry also indicates if the task is enabled by default, or not enabled by default.   For information about planning for and configuring sites to run maintenance tasks, see   [Maintenance tasks for System Center Configuration Manager](../System Center Configuration Manager/Maintenance-tasks-for-System-Center-Configuration-Manager.md)  
  
 **Backup Site Server** - Use this task to prepare for recovery of critical data by creating a backup of the critical information that you have to restore a site and the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. For more information, see [Backup and recovery for System Center Configuration Manager](../System Center Configuration Manager/Backup-and-recovery-for-System-Center-Configuration-Manager.md)  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Not enabled  
  
-   Secondary site - Not available  
  
 **Check Application Title with Inventory Information** - Use this task to maintain consistency between software titles reported in software inventory and software titles in the Asset Intelligence catalog. For more information, see [Introduction to Asset Intelligence in System Center Configuration Manager](../System Center Configuration Manager/Introduction-to-Asset-Intelligence-in-System-Center-Configuration-Manager.md).  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Clear Install Flag** - Use this task to remove the installed flag for clients that do not submit a Heartbeat Discovery record during the **Client Rediscovery** period. The installed flag prevents automatic client push installation to a computer that might have an active [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
-   Central administration site - Not available  
  
-   **Primary site** - Not enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Application Request Data** - Use this task to delete aged application requests from the database. For more information about application requests, see [Get started with application management in System Center Configuration Manager](../System Center Configuration Manager/Get-started-with-application-management-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Client Operations** - Use this task to delete all aged data for client operations from the site database. For example, this includes data for aged or expired client notifications (like download requests for machine or user policy), and for Endpoint Protection (like requests by an administrative user for clients to run a scan or download updated definitions).
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Client Presence History** - Use this task to delete history information about the online status of clients, recorded by client notification, that is older than the specified time. For more information about client notification, see [How to monitor clients in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-clients-in-System-Center-Configuration-Manager.md).  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Collected Files** -  Use this task to delete aged information about collected files from the database. This task also deletes the collected files from the site server folder structure at the selected site. By default, the five most recent copies of collected files are stored on the site server in the **Inboxes\sinv.box\FileCol** directory. For more information, see [Planning for software inventory in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-software-inventory-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Computer Association Data** - Use this task to delete aged Operating System Deployment computer association data from the database. This information is used as part of completing user state restores. For more information about computer associations, see [Manage user state in System Center Configuration Manager](../System Center Configuration Manager/Manage-user-state-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Delete Detection Data** - Use this task to delete aged data from the database that has been created by Extraction Views. By default, Extraction Views are disabled and can only be enabled by use of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] SDK. Unless Extraction Views are enabled, there is no data for this task to delete.  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Device Wipe Record** - Use this task to delete aged data about mobile device wipe actions from the database. For information about managing mobile devices, see  [Determine How to Manage Mobile Devices in Configuration Manager](../System Center Configuration Manager/Determine-How-to-Manage-Mobile-Devices-in-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Devices Managed by the Exchange Server Connector** - Use this task to delete aged data about mobile devices that are managed by using the Exchange Server connector. This data is deleted according to the interval configured for the **Ignore mobile devices that are inactive for more than (days)** option on the **Discovery** tab of the Exchange Server connector properties. For more information, see [Manage mobile devices with System Center Configuration Manager and Exchange](../System Center Configuration Manager/Manage-mobile-devices-with-System-Center-Configuration-Manager-and-Exchange.md)  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Discovery Data** - Use this task to delete aged discovery data from the database. This data can include records resulting from heartbeat discovery, network discovery, and Active Directory Domain Services discovery methods (System, User, and Group). When this task runs at a site, data associated with that site is deleted, and those changes replicate to other sites.  For information about Discovery, see [Run discovery for System Center Configuration Manager](../System Center Configuration Manager/Run-discovery-for-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Distribution Point Usage Data** - Use this task to delete from the database aged data for distribution points that has been stored longer than a specified time.  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Endpoint Protection Health Status History Data** - Use this task to delete aged status information for Endpoint Protection from the database. For more information about Endpoint Protection status information, see [How to monitor Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-Endpoint-Protection-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Enrolled Devices** - Beginning with the update for 1602, this task is disabled by default, and you can use this task to delete from the site database the aged data about mobile devices that have not reported any information to the site for a specified time.  This task applies to devices that are enrolled by [!INCLUDE[mit_first](../System Center Configuration Manager/itokens/mit_first_md.md)] (hybrid), or enrolled with [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] on-premises mobile device management.  For information about the operating systems of devices that are enrolled by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] or by [!INCLUDE[mit_next](../System Center Configuration Manager/itokens/mit_next_md.md)], see [Mobile devices enrolled by Microsoft Intune](../System Center Configuration Manager/Supported-operating-systems-for-clients-and-devices-for-System-Center-Configuration-Manager.md#bkmk_IntuneOS) section in [Supported operating systems for clients and devices for System Center Configuration Manager](../System Center Configuration Manager/Supported-operating-systems-for-clients-and-devices-for-System-Center-Configuration-Manager.md). 
  
-   Central administration site - Not available  
  
-   **Primary site** - Not enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Inventory History** - Use this task to delete inventory data that has been stored longer than a specified time from the database. For information about inventory history, see [How to use Resource Explorer to view hardware inventory in System Center Configuration Manager](../System Center Configuration Manager/How-to-use-Resource-Explorer-to-view-hardware-inventory-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Log Data** - Use this task to delete aged log data that is used for troubleshooting from the database. This data is not related to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] component operations.  
  
> [!IMPORTANT]  
>  By default, this task runs daily at each site. At a central administration site and primary sites, the task deletes data that is older than 30 days. When you use SQL Server Express at a secondary site, ensure that this task runs daily, and deletes data that has been inactive for 7 days.  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   **Secondary site** - Enabled  
  
 **Delete Aged Notification Task History** - Use this task to delete information about client notification tasks from the site database when it has not been updated for a specified time. For more information about client notification, see [Client deployment tasks for System Center Configuration Manager](../System Center Configuration Manager/Client-deployment-tasks-for-System-Center-Configuration-Manager.md)  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Replication Summary Data** - Use this task to delete aged replication summary data from the site database when it has not been updated for a specified time. For more information, see the [How to monitor database replication links and replication status](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md#BKMK_MonitorRepLinksAndStatuss) section in the [Monitor hierarchy and replication infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md) topic.  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   **Secondary site** - Enabled  
  
 **Delete Aged Passcode Records** - Use this task at the top-level site of your hierarchy to delete aged data about Passcode Resets for Android and Windows Phone devices. Passcode Reset data  is encrypted but does include the PIN for devices. By default this task is enabled and deletes data that is older than 1 day.  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Replication Tracking Data** - Use this task to delete aged data about database replication between [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] sites from the database. When you change the configuration of this maintenance task, the configuration applies to each applicable site in the hierarchy. For more information, see the  [How to monitor database replication links and replication status](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md#BKMK_MonitorRepLinksAndStatuss) section in the [Monitor hierarchy and replication infrastructure in System Center Configuration Manager](../System Center Configuration Manager/Monitor-hierarchy-and-replication-infrastructure-in-System-Center-Configuration-Manager.md) topic.  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   **Secondary site** - Enabled  
  
 **Delete Aged Software Metering Data** - Use this task to delete aged data for software metering that has been stored longer than a specified time from the database. For more information, see [Software metering in System Center Configuration Manager](../System Center Configuration Manager/Software-metering-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Software Metering Summary Data** - Use this task to delete aged summary data for software metering that has been stored longer than a specified time from the database.  For more information, see [Software metering in System Center Configuration Manager](../System Center Configuration Manager/Software-metering-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Status Messages** - Use this task to delete aged status message data as configured in status filter rules from the database. For information, see  the Monitor the status system of Configuration Manager section in the topic [Use alerts and the status system for System Center Configuration Manager](../System Center Configuration Manager/Use-alerts-and-the-status-system-for-System-Center-Configuration-Manager.md).  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Threat Data** - Use this task to delete aged Endpoint Protection threat data that has been stored longer than a specified time from the database. For information about Endpoint Protection, see [Endpoint Protection in System Center Configuration Manager](../System Center Configuration Manager/Endpoint-Protection-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged Unknown Computers** - Use this task to delete information about unknown computers from the site database when it has not been updated for a specified time. For more information, see [Prepare for unknown computer deployments in System Center Configuration Manager](../System Center Configuration Manager/Prepare-for-unknown-computer-deployments-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Aged User Device Affinity Data** - Use this task to delete aged User Device Affinity data from the database. For more information, see [Link users and devices with user device affinity in System Center Configuration Manager](../System Center Configuration Manager/Link-users-and-devices-with-user-device-affinity-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Inactive Client Discovery Data** - Use this task to delete discovery data for inactive clients from the database. Clients are marked as inactive when the client is flagged as obsolete and by configurations made for Client status. This task operates only on resources that are [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients. It is different than the **Delete Aged Discovery Data** task which deletes any aged discovery data record. When this task runs at a site, it removes the data from the database at all sites in a hierarchy. For more information, see [How to configure client status in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-status-in-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  When enabled, configure this task to run at an interval greater than the **Heartbeat Discovery** schedule. This enables active clients to send a Heartbeat Discovery record to mark their client record as active so this task does not delete them.  
  
-   Central administration site - Not available  
  
-   **Primary site** - Not enabled  
  
-   Secondary site - Not available  
  
 **Delete Obsolete Alerts** - Use this task to delete expired alerts that have been stored longer than a specified time from the database. For more information, see [Use alerts and the status system for System Center Configuration Manager](../System Center Configuration Manager/Use-alerts-and-the-status-system-for-System-Center-Configuration-Manager.md).  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Obsolete Client Discovery Data** - Use this task to delete obsolete client records from the database. A record that is marked as obsolete has usually been replaced by a newer record for the same client. The newer record becomes the client’s current record. For information about Discovery, see [Run discovery for System Center Configuration Manager](../System Center Configuration Manager/Run-discovery-for-System-Center-Configuration-Manager.md).  
  
> [!IMPORTANT]  
>  When enabled, configure this task to run at an interval greater than the Heartbeat Discovery schedule. This enables the client to send a Heartbeat Discovery record that sets the obsolete status correctly.  
  
-   Central administration site - Not available  
  
-   **Primary site** - Not enabled  
  
-   Secondary site - Not available  
  
 **Delete Obsolete Forest Discovery Sites and Subnets** - Use this task to delete data about Active Directory sites, subnets, and domains that have not been discovered by the Active Directory Forest Discovery method in the last 30 days. This removes the discovery data but does not affect boundaries created from this discovery data.  For more information, see [Run discovery for System Center Configuration Manager](../System Center Configuration Manager/Run-discovery-for-System-Center-Configuration-Manager.md).  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Delete Unused Application Revisions** - Use this task to delete application revisions that are no longer referenced. For more information, see [How to revise and supersede applications in System Center Configuration Manager](../System Center Configuration Manager/How-to-revise-and-supersede-applications-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Evaluate Collection Members** - You configure the Collection Membership Evaluation as a site component. For information about site components, see [Site components for System Center Configuration Manager](../System Center Configuration Manager/Site-components-for-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Monitor Keys** - Use this task to monitor the integrity of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database primary keys. A primary key is a column or combination of columns that uniquely identify one row and distinguish it from any other row in a Microsoft SQL Server database table.  
  
-   **Central administration site** - Enabled  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Rebuild Indexes** - Use this task to rebuild the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database indexes. An index is a database structure that is created on a database table to speed up data retrieval. For example, searching an indexed column is often much faster than searching a column that is not indexed. To improve performance, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database indexes are frequently updated to remain synchronized with the constantly changing data stored in the database. This task creates indexes on database columns that are at least 50 percent unique, drops indexes on columns that are less than 50 percent unique, and rebuilds all existing indexes that meet the data uniqueness criteria.  
  
-   **Central administration site** - Not enabled  
  
-   **Primary site** - Not enabled  
  
-   **Secondary site**- Not enabled  
  
 **Summarize Installed Software Data** - Use this task to summarize the data for installed software from multiple records into one general record. Data summarization can compress the amount of data stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. For more information, see [Planning for software inventory in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-software-inventory-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Summarize Software Metering File Usage Data** - Use this task to summarize the data from multiple records for software metering file usage into one general record. Data summarization can compress the amount of data stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. You can use this task with the **Summarize Software Metering Monthly Usage Data** task to summarize software metering data, and to conserve disk space in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. For more information, see [Software metering in System Center Configuration Manager](../System Center Configuration Manager/Software-metering-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Summarize Software Metering Monthly Usage Data** - Use this task to summarize the data from multiple records for software metering monthly usage into one general record. Data summarization can compress the amount of data stored in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. You can use this task with the **Summarize Software Metering File Usage Data** task to summarize software metering data, and to conserve space in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. For more information, see [Software metering in System Center Configuration Manager](../System Center Configuration Manager/Software-metering-in-System-Center-Configuration-Manager.md).  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Update Application Available Targeting** - Use this task to have [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] recalculate the mapping of  policy and application deployments to resources in collections.  When you deploy policy or applications to a collection, Configuration Manager creates an initial mapping between the objects you deploy and the collection members. These mappings are stored in a table for quick reference. When a collections membership changes, these stored mappings are updated to reflect those changes. However, it is possible for these mappings to fall out of sync. For example, if the site fails to properly process a notification file, that change might not be reflected in a change to the mappings. This tasks refreshes that mapping based on current collection membership  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
 **Update Application Catalog Tables** - Use this task to synchronize the Application Catalog website database cache with the latest application information.   When you change the configuration of this maintenance task, the configuration applies to all primary sites in the hierarchy.  
  
-   Central administration site - Not available  
  
-   **Primary site** - Enabled  
  
-   Secondary site - Not available  
  
## See Also  
 [Site and hierarchy infrastructure technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-and-hierarchy-infrastructure-technical-reference-for-System-Center-Configuration-Manager.md)