---
title: "Monitor operating system deployments in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 08085d94-295c-432f-b5e3-9736bce0193b
caps.latest.revision: 6
caps.handback.revision: 0
---
# Monitor operating system deployments in System Center Configuration Manager
To help you to monitor operating system deployment objects, the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console provides the following:  
  
-   [Alerts for operating system deployments](#BKMK_OSDAlerts)  
  
-   [Task sequence deployment status](#BKMK_TSDeployStatus)  
  
-   [Operating system deployment reports](#BKMK_TSReports)  
  
-   [Monitor content](#BKMK_MonitorContent)  
  
    -   [Content status monitoring](#BKMK_ContentStatus)  
  
    -   [Distribution point group status](#BKMK_DPGroupStatus)  
  
    -   [Distribution point configuration status](#BKMK_DPConfigStatus)  
  
##  <a name="BKMK_OSDAlerts"></a> Alerts for operating system deployments  
 You can configure an alert in the task sequence  deployment settings to notify administrative users when compliance levels for the  deployment is below the configured percentage.  
  
 After you configure the alert settings, if the specified conditions occur, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] generates an alert. You can review task sequence deployment alerts at the following locations:  
  
1.  Review recent alerts in the **Operating Systems** node in the **Software Library** workspace.  
  
2.  Manage the configured alerts in the **Alerts** node in the **Monitoring** workspace.  
  
##  <a name="BKMK_TSDeployStatus"></a> Task sequence deployment status  
 After you deploy a task sequence, you can monitor the deployment status. Use the following procedure to monitor the deployment status for a task sequence.  
  
#### To monitor deployment status  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the Monitoring workspace, click **Deployments**.  
  
3.  Click the task sequence  for which you want to monitor the deployment status.  
  
4.  On the **Home** tab, in the **Deployment** group, click **View Status**.  
  
##  <a name="BKMK_TSReports"></a> Operating system deployment reports  
 There are many predefined operating system deployment reports available. They are organized in several categories and can be used to report on specific information about state migration and task sequence deployments. In addition to using the preconfigured reports, you can also create custom software update reports according to the needs of your enterprise. For more information, see [Operations and maintenance for reporting in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-reporting-in-System-Center-Configuration-Manager.md).  
  
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
 [Manage enterprise operating systems with System Center Configuration Manager](../System Center Configuration Manager/Manage-enterprise-operating-systems-with-System-Center-Configuration-Manager.md)