---
title: "Monitor software updates in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 9afd7b0f-5c8e-48bc-9a65-1f7d74103688
caps.latest.revision: 5
caps.handback.revision: 0
---
# Monitor software updates in System Center Configuration Manager
To help you to monitor software updates objects, processes, and compliance information, the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console provides the following:  
  
-   [Alerts for software updates](#BKMK_SUAlerts)  
  
-   [Software updates synchronization status](#BKMK_SUSyncStatus)  
  
-   [Software update deployment status](#BKMK_SUDeployStatus)  
  
-   [Software updates reports](#BKMK_SUReports)  
  
-   [Monitor content](#BKMK_MonitorContent)  
  
    -   [Content status monitoring](#BKMK_ContentStatus)  
  
    -   [Distribution point group status](#BKMK_DPGroupStatus)  
  
    -   [Distribution point configuration status](#BKMK_DPConfigStatus)  
  
##  <a name="BKMK_SUAlerts"></a> Alerts for software updates  
 You can configure alerts for software updates to notify administrative users when compliance levels for software update deployments are below the configured percentage. You can configure alerts for software update deployments in the following locations:  
  
-   ADR setting: You can configure the alerts settings in the Automatic Deployment Rule Wizard and in the properties for the ADR.  
  
-   Deployment setting: You can configure the alerts settings in the Deploy Software Updates Wizard and in deployment properties.  
  
 After you configure the alert settings, if the specified conditions occur, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] generates an alert. You can review software update alerts at the following locations:  
  
1.  Review recent alerts in the **Software Updates** node in the **Software Library** workspace.  
  
2.  Manage the configured alerts in the **Alerts** node in the **Monitoring** workspace.  
  
##  <a name="BKMK_SUSyncStatus"></a> Software updates synchronization status  
 After you initiate the synchronization process, you can monitor the synchronization process from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console for all software update points in your hierarchy. Use the following procedure to monitor the software update synchronization process.  
  
#### To monitor the software updates synchronization process  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the Monitoring workspace, click **Software Update Point Synchronization Status**.  
  
     The software update points in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy are displayed in the results pane. From this view, you can monitor the synchronization status for all software update points. To see more detailed information about the synchronization process, you can review the wsyncmgr.log file, which is located in <*ConfigMgrInstallationPath*>\Logs on each site server.  
  
##  <a name="BKMK_SUDeployStatus"></a> Software update deployment status  
 After you deploy the software updates in a software update group or deploy an individual software update, you can monitor the deployment status. Use the following procedure to monitor the deployment status for a software update group or software update.  
  
#### To monitor deployment status  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the Monitoring workspace, click **Deployments**.  
  
3.  Click the software update group or software update for which you want to monitor the deployment status.  
  
4.  On the **Home** tab, in the **Deployment** group, click **View Status**.  
  
##  <a name="BKMK_SUReports"></a> Software updates reports  
 The state messages for software updates provide information about the compliance of software updates and about the evaluation and enforcement state of software update deployments. You can run software update reports to display these state messages. There are more than 30 predefined software update reports available. They are organized in several categories and can be used to report on specific information about software updates and deployments. In addition to using the preconfigured reports, you can also create custom software update reports according to the needs of your enterprise. For more information, see [Operations and maintenance for reporting in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-reporting-in-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_MonitorContent"></a> Monitor content  
 You can monitor content in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to review the status for all package types in relation to the associated distribution points. This can include the content validation status for the content in the package, the status of content assigned to a specific distribution point group, the state of content assigned to a distribution point, and the status of optional features for each distribution point (content validation, PXE, and multicast).  
  
###  <a name="BKMK_ContentStatus"></a> Content status monitoring  
 The **Content Status** node in the **Monitoring** workspace provides information about content packages. You can review general information about the package, distribution status for the package, and detailed status information about the package. Use the following procedure to view content status.  
  
##### To monitor content status  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the Monitoring workspace, expand **Distribution Status**, and then click **Content Status**. The packages are displayed.  
  
3.  Select the package for which to view detailed status information.  
  
4.  On the **Home** tab, click **View Status**. Detailed status information for the package is displayed.  
  
###  <a name="BKMK_DPGroupStatus"></a> Distribution point group status  
 The **Distribution Point Group Status** node in the **Monitoring** workspace provides information about distribution point groups. You can review general information about the distribution point group, such as distribution point group status and compliance rate, as well as detailed status information for the distribution point group. Use the following procedure to view distribution point group status.  
  
##### To monitor distribution point group status  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the monitoring workspace, expand **Distribution Status**, and then click **Distribution Point Group Status**. The distribution point groups are displayed.  
  
3.  Select the distribution point group for which to view detailed status information.  
  
4.  On the **Home** tab, click **View Status**. Detailed status information for the distribution point group is displayed.  
  
###  <a name="BKMK_DPConfigStatus"></a> Distribution point configuration status  
 The **Distribution Point Configuration Status** node in the **Monitoring** workspace provides information about the distribution point. You can review which attributes are enabled for the distribution point, such as the PXE, Multicast, and content validation. You can also view detailed status information for the distribution point. Use the following procedure to view distribution point configuration status.  
  
##### To monitor distribution point configuration status  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the monitoring workspace, expand **Distribution Status**, and then click **Distribution Point Configuration Status**. The distribution points are displayed.  
  
3.  Select the distribution point for which to view distribution point status information.  
  
4.  In the results pane, click the **Details** tab. Status information for the distribution point is displayed.  
  
## See Also  
 [Deploy and manage software updates in System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-software-updates-in-System-Center-Configuration-Manager.md)