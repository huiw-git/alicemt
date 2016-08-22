---
title: "How to monitor compliance settings in System Center Configuration Manager"
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
ms.assetid: 92c1ccca-a748-44cd-a52e-e41d34bf981d
caps.latest.revision: 6
caps.handback.revision: 0
---
# How to monitor compliance settings in System Center Configuration Manager
After you have deployed [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] configuration baselines to computers in your hierarchy, you can use one or more of the following procedures to display the compliance status of the configuration baseline:  
  
-   [How to view compliance results in the Configuration Manager console](#BKMK_Console)  
  
-   [How to view compliance results by using reports](#BKMK_Reports)  
  
-   [How to view compliance results on a Configuration Manager Windows client](#BKMK_Client)  
  
-   [How to create collections based on configuration baseline compliance](#BKMK_Create)  
  
> [!NOTE]  
>  The validation criteria fields in compliance settings reports (the equivalent on the client-side report is **Constraints**) display the underlying Service Modeling Language (SML). This can make it difficult for administrators who have authored the configuration item in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to understand what the validation criteria is if they do not have knowledge of SML. In this case, use the **Monitoring** workspace in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to view the properties of the configuration item and its validation criteria.  
  
##  <a name="BKMK_Console"></a> How to view compliance results in the Configuration Manager console  
 Use this procedure to view details about the compliance of deployed configuration baselines in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
#### To view compliance results in the Configuration Manager console  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the **Monitoring** workspace, click **Deployments**.  
  
3.  In the **Deployments** list, select the configuration baseline deployment for which you want to review compliance information.  
  
4.  You can review summary information about the compliance of the configuration baseline deployment on the main page. To view more detailed information, select the configuration baseline deployment, and then on the **Home** tab, in the **Deployment** group, click **View Status** to open the **Deployment Status** page.  
  
     The **Deployment Status** page contains the following tabs:  
  
    -   **Compliant**: Displays the compliance of the configuration baseline based on the number of assets affected. You can click a rule to create a temporary node under the **Users** or **Devices** node that are in the **Assets and Compliance** workspace, which contains all users or devices that are compliant with this rule. The **Asset Details** pane displays the users or devices that are compliant with the configuration baseline. Double-click a user or device in the list to display additional information.  
  
        > [!IMPORTANT]  
        >  A configuration item rule is not evaluated if it is not detected or not applicable on a client computer; however, the rule is returned as compliant.  
  
    -   **Error**: Displays a list of all errors for the selected configuration baseline deployment based on number of assets affected. You can click a rule to create a temporary node under the **Users** or **Devices** node of the **Assets and Compliance** workspace, which contains all users or devices that generated errors with this rule. When you select a user or device, the **Asset Details** pane displays the users or devices that are affected by the selected issue. Double-click a user or device in the list to display additional information about the issue.  
  
    -   **Non-Compliant**: Displays a list of all noncompliant rules within the configuration baseline based on number of assets affected. You can click a rule to create a temporary node under the **Users** or **Devices** node of the **Assets and Compliance** workspace, which contains all users or devices that are not compliant with this rule. When you select a user or device, the **Asset Details** pane displays the users or devices that are affected by the selected issue. Double-click a user or device in the list to display further information about the issue.  
  
    -   **Unknown**: Displays a list of all users and devices that did not report compliance for the selected configuration baseline deployment together with the current client status of devices.  
  
5.  On the **Deployment Status** page, you can review detailed information about the compliance of the deployed configuration baseline. A temporary node is created under the **Deployments** node that helps you find this information again quickly.  
  
##  <a name="BKMK_Reports"></a> How to view compliance results by using reports  
 Compliance settings in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] includes a number of built-in reports that let you monitor information about configuration items, configuration baselines, and deployments. These reports have the report category of **Compliance and Settings Management**.  
  
> [!IMPORTANT]  
>  You must use a wildcard (**%**) character when you use the parameters **Device filter** and User filter in the compliance settings reports.  
  
 For more information about how to configure Reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md)  
  
##  <a name="BKMK_Client"></a> How to view compliance results on a Configuration Manager Windows client  
 Use this procedure to view details about the compliance of deployed configuration baselines on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
> [!NOTE]  
>  You cannot view information on the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Windows client if you are logged on with a domain Guest account.  
  
#### To view compliance results on a Configuration Manager Windows client  
  
1.  Navigate to **Configuration Manager** in Control Panel of the client computer, and double-click it to open its properties.  
  
2.  Click the **Configurations** tab, and view the list of deployed configuration baselines.  
  
3.  View the **Compliance State** for each configuration baseline:  
  
    > [!IMPORTANT]  
    >  The evaluation results are cached on the client for 15 minutes. If you initiate a re-evaluation within the 15 minute period, the compliance results are returned from this cache rather than a new evaluation. Therefore, if you make a change on the client that might affect the compliance evaluation results, wait until the 15 minutes have elapsed before initiating a re-evaluation.  
  
    -   **Compliant**: The client computer is in compliance with the evaluated configuration baseline.  
  
    -   **Non-Compliant**: The client computer is out of compliance with the evaluated configuration baseline.  
  
    -   **Unknown**: The client computer has not yet evaluated the configuration baseline. If you want to initiate evaluation outside the compliance evaluation schedule, select the configuration baselines to evaluate, and then click **Evaluate**.  
  
        > [!NOTE]  
        >  If you have local administrator credentials on the client computer, you can view details of each evaluated configuration baseline to determine which configuration item is reporting a noncompliant status. To do this, select the configuration baseline, and then click **View Report**.  
  
4.  Click **OK**.  
  
##  <a name="BKMK_Create"></a> How to create collections based on configuration baseline compliance  
 Use the following procedure to create a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collection based on devices with a specified compliance. You can create collections based on the following compliance states:  
  
-   **Compliant**  
  
-   **Error**  
  
-   **Non-compliant**  
  
-   **Unknown**  
  
#### To create a collection based on compliance state  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Configuration Baselines**.  
  
3.  In the **Configuration Baselines** list, select the configuration baseline from which you want to create a collection.  
  
4.  In the **Deployment** tab, in the **Deployment Group**, click **Create New Collection** and then, in the drop-down list, select the compliance level for which you want to create a collection.  
  
5.  The **Create User Collection Wizard** or the **Create Device Collection Wizard** opens, depending on whether the configuration item is deployed to users or devices. The wizard is automatically populated with the correct values to create the collection; however, you can edit these values.  
  
6.  After you complete the wizard, the collection displays in the **User Collections** or the **Device Collections** node in the **Assets and Compliance** workspace.  
  
## See Also  
 [Compliance settings technical reference for System Center Configuration Manager](../System Center Configuration Manager/Compliance-settings-technical-reference-for-System-Center-Configuration-Manager.md)