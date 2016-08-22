---
title: "How to use maintenance windows in System Center Configuration Manager"
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
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
caps.latest.revision: 6
caps.handback.revision: 0
author: barlanmsft
---
# How to use maintenance windows in System Center Configuration Manager
Maintenance windows in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] provide a means by which administrative users can define a time period when various [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operations can be carried out on members of a device collection. You can use maintenance windows to help ensure that client configuration changes occur during periods that do not affect the productivity of the organization.  
  
 The following [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] operations support maintenance windows:  
  
-   Software deployments  
  
-   Software update deployments  
  
-   Compliance settings deployment and evaluation  
  
-   Operating system deployments  
  
-   Task sequence deployments  
  
 Maintenance windows are configured for a collection with a start date, a start and finish time, and a recurrence pattern. Each maintenance window must have a duration of less than 24 hours. By default, computer restarts caused by a deployment are not allowed outside of a maintenance window, but you can override the default in the settings for each deployment. Maintenance windows affect only the time when the deployment program runs; applications configured to download and run locally can download content outside of the maintenance window.  
  
 When a client computer is a member of a device collection that has a maintenance window configured, a deployment program runs only if the maximum allowed run time does not exceed the duration configured for the maintenance window. If the program fails to run, an alert is generated and the deployment is rerun during the next scheduled maintenance window that has available time.  
  
## Using multiple maintenance windows  
 When a client computer is a member of multiple device collections that have configured maintenance windows, the following rules apply:  
  
-   If the maintenance windows do not overlap, they are treated as two independent maintenance windows.  
  
-   If the maintenance windows overlap, they are treated as a single maintenance window encompassing the time period covered by both maintenance windows. For example, if two maintenance windows, each an hour in duration overlap by 30 minutes, the effective duration of the maintenance window would be 90 minutes.  
  
 When a user initiates an application installation from Software Center, the application is installed immediately, regardless of any configured maintenance windows.  
  
 If an application deployment with a purpose of **Required** reaches its installation deadline during the nonbusiness hours configured by a user in Software Center, the application will be installed.  
  
### How to configure maintenance windows  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, click **Device Collections**.  
  
3.  In the **Device Collections** list, select the collection for which you want to configure a maintenance window.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  In the **Maintenance Windows** tab of the *<collection name\>***Properties** dialog box, click the **New** icon.  
  
    > [!NOTE]  
    >  You cannot create maintenance windows for the **All Systems** collection.  
  
6.  In the **<new\> Schedule** dialog box, specify a name, a schedule, and a recurrence pattern for the maintenance window. You can also enable the option to apply the schedule to only task sequences.  
  
7.  From the **Apply this schedule to** drop-down list, select whether this maintenance window applies to all deployments, only software updates, or only task sequences.  
  
8.  Click **OK** to close the **<new\> Schedule** dialog box and create the new maintenance window.  
  
9. Close the *<collection name\>***Properties** dialog box.  
  
## See Also  
 [Operations and maintenance for collections in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-collections-in-System-Center-Configuration-Manager.md)