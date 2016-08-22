---
title: "How to simulate application deployments with System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 28b240a4-d358-40ce-8006-c697b1622ece
caps.latest.revision: 6
caps.handback.revision: 0
author: barlanmsft
---
# How to simulate application deployments with System Center Configuration Manager
Use simulated deployments if you want to test the applicability of an application deployment to computers without installing or uninstalling the application. A simulated deployment evaluates the detection method, requirements and dependencies for a deployment type, and reports the results in the **Deployments** node of the **Monitoring** workspace. Use the procedure in this topic to simulate an application deployment in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)].  
  
> [!NOTE]  
>  You cannot use simulated deployments for collections of mobile devices.  
>   
>  You cannot deploy an application with a deployment purpose of **Uninstall** if a simulated deployment of the same application is active.  
  
## How to simulate an application deployment  
  
#### To simulate an application deployment  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, select one of the following:  
  
    -   A collection of users.  
  
    -   A collection of devices.  
  
    -   A [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] application.  
  
2.  In the **Home** tab, in the **Deployment** group, click **Simulate Deployment**.  
  
3.  In the **Simulate Application Deployment Wizard**, specify the following information:  
  
    -   **Application** - Click **Browse** and then select the application for which you want to create a simulated deployment.  
  
    -   **Collection** - Click **Browse** and then select the collection that you want to use for the simulated deployment.  
  
    -   **Action** - From the drop-down list, select whether you want to simulate the installation, or the uninstallation of the selected application.  
  
    -   **Deploy automatically with or without user login** - If this option is checked, the clients will evaluate the simulated deployment whether or not the clients are logged in.  
  
4.  Click **Next**, review the information on the **Summary** page, and then complete the wizard to create the simulated application deployment.  
  
5.  Simulated applications appear in the **Deployments** node of the **Monitoring** workspace with a purpose of **Simulate**. For more information about how to monitor application deployments, see [Monitor applications from the System Center Configuration Manager console](../System Center Configuration Manager/Monitor-applications-from-the-System-Center-Configuration-Manager-console.md).  
  
## See Also  
 [Application management technical reference for System Center Configuration Manager](../System Center Configuration Manager/Application-management-technical-reference-for-System-Center-Configuration-Manager.md)