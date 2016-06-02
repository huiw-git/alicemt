---
title: DQS Administration
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9940ef5d-f6f6-4dec-9414-1077a4d7f12b
---
# DQS Administration
  [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) allows you to administer and manage various DQS activities performed on [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)], configure server\-level properties related to DQS activities, configure the Reference Data Service settings, and configure DQS log settings. These things are done through the **Administration** feature in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]. Depending upon your security access \(role\) in DQS, you are granted\/denied access to certain functionalities in this area.  
  
 Apart from these administration activities, this topic also provides information about an administration activity, backing up and restoring DQS databases, which is not performed using [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)].  
  
 The administration feature in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] has the following benefits:  
  
-   Enables data stewards to monitor various DQS activities on a [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] from a [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)].  
  
-   Enables DQS administrators to monitor the DQS activities on a [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] from a [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)], and *terminate* a running activity or *stop* a running process within an activity, if required.  
  
-   Configure reference data service settings such as setting up connectivity with Windows Azure Marketplace and managing direct third\-party reference data service providers.  
  
-   Configure threshold values for the cleansing and matching activities.  
  
-   Enable\/disable notifications in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)].  
  
-   Configure logging based on the severity level of the events.  
  
##  <a name="AdminUsingClent"></a> Administration Activities by Using Data Quality Client  
 These activities are performed by using the **Administration** feature in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)].  
  
### Activity Monitoring  
 The **Activity Monitoring** screen in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] displays detailed information about each activity performed on a [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)]. This screen will be primarily used by the data steward to perform a high\-level monitoring of all the activities performed on the [!INCLUDE[ssDQSServer](../../Token\Other/ssDQSServer_md.md)] that the [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] application is connected to. This screen does not provide any system\-level monitoring. Additionally, this screen also enables the DQS administrators to control an activity or a process within an activity by terminating a running activity or stopping a running process within an activity, if required. The data is displayed for knowledge discovery, domain management, matching policy, cleansing, matching, and SQL Server Integration Services \(SSIS\)\-based cleansing.  
  
### Configuration  
 The **Configuration** screen in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)] enables the DQS administrator to do the following things:  
  
-   **Reference Data**: Configure reference data service providers: Windows Azure Marketplace or direct reference data service providers. After you set up the reference data service providers, you can map a domain\/composite domain with the reference data during domain management activity in a knowledge base, and then use the same knowledge base for the cleansing activity in a data quality project. It also enables you to specify the proxy settings for connecting to the Internet to use Windows Azure Marketplace.  
  
-   **General Settings**: Specify the threshold values for data cleansing and data matching, and whether to enable notifications for profiling in [!INCLUDE[ssDQSClient](../../Token\Other/ssDQSClient_md.md)]. These threshold values are used by DQS during the computer\-assisted cleansing and matching activities in a data quality project.  
  
-   **Log Settings**: The log files in DQS record the activities performed in DQS, and are useful for tracking operational issues during maintenance and troubleshooting. You can filter the messages that you want to be logged for various DQS features \(domain management, knowledge discovery, cleansing, matching, and reference data services\) and DQS modules based on the severity level of the events.  
  
> [!NOTE]  
>  The **Configuration** screen is available only for those users who have the dqs\_administrator role on the DQS\_MAIN database.  
  
##  <a name="AdminOutsideClient"></a> Administration Activities Outside of Data Quality Client  
 There activities are performed outside of Data Quality Client:  
  
-   **Backup and Restore DQS Databases**: The backup and restore of DQS databases is same as backing up and restoring any SQL Server database with some considerations that are specific to DQS.  
  
-   **Detach and Attach DQS Databases**: The steps to detach and attach DQS databases is same as detaching and attaching any SQL Server database with some considerations that are specific to DQS.  
  
 For more information, see [Manage DQS Databases](../../Topics\TopicNameNotContainA/Manage-DQS-Databases.md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how to monitor activities in DQS.|[Monitor DQS Activities](../../Topics\TopicNameNotContainA/Monitor-DQS-Activities.md)|  
|Describes how to configure reference data settings in DQS.|[Configure DQS to Use Reference Data](../../Topics\TopicNameNotContainA/Configure-DQS-to-Use-Reference-Data.md)|  
|Describes how to configure threshold values for the cleansing and matching activities.|[Configure Threshold Values for Cleansing and Matching](../../Topics\TopicNameNotContainA/Configure-Threshold-Values-for-Cleansing-and-Matching.md)|  
|Describes how to enable or disable notifications in DQS.|[Enable or Disable Profiling Notifications in DQS](../../Topics\TopicNameNotContainA/Enable-or-Disable-Profiling-Notifications-in-DQS.md)|  
|Describes how to configure DQS logging based on the severity level of the events.|[Configure Severity Levels for DQS Log Files](../../Topics\TopicNameNotContainA/Configure-Severity-Levels-for-DQS-Log-Files.md)|  
|Describes how to configure advanced settings for DQS logging.|[Configure Advanced Settings for DQS Log Files](../../Topics\TopicNameNotContainA/Configure-Advanced-Settings-for-DQS-Log-Files.md)|  
|Describes how to back up and restore DQS databases.|[Backing Up and Restoring DQS Databases](../../Topics\TopicNameNotContainA/Backing-Up-and-Restoring-DQS-Databases.md)|  
|Describes how to detach and attach DQS databases.|[Detaching and Attaching DQS Databases](../../Topics\TopicNameNotContainA/Detaching-and-Attaching-DQS-Databases.md)|  
  
## See Also  
 [Reference Data Services in DQS](../../Topics\TopicNameNotContainA/Reference-Data-Services-in-DQS.md)   
 [Manage DQS Log Files](../../Topics\TopicNameNotContainA/Manage-DQS-Log-Files.md)   
 [Manage DQS Databases](../../Topics\TopicNameNotContainA/Manage-DQS-Databases.md)  
  
  