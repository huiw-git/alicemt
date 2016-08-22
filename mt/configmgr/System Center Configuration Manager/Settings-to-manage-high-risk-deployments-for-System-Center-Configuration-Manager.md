---
title: "Settings to manage high-risk deployments for System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
caps.latest.revision: 6
---
# Settings to manage high-risk deployments for System Center Configuration Manager
With [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] you can configure settings at a site that will warn administrative users if they create a high-risk task sequence deployment. A high-risk deployment is:  
  
-   A deployment that is automatically installed  
  
-   Has the potential to cause unwanted results  
  
 For example, a task sequence that has a purpose of **Required** that deploys an operating system is considered a high-risk deployment.  
  
 To reduce the risk of an unwanted high-risk deployment, you can configure the following deployment verification settings:  
  
-   **Collection size limits**: Hide collections that contain more clients than a configured number when you create a deployment.  
  
    -   **Default size**: This setting hides collections, by default, with more clients than the configured number when you create a deployment. You can still view these collections when creating the deployment, but they are hidden by default. The default value is 100. Enter a value of 0 to ignore this setting.  
  
    -   **Maximum size**: This setting always hides collections with more clients than the configured number when you create a deployment. The default value is 0, which ignores this setting. The **Maximum size** value must be greater than the **Default size** value.  
  
     For example, let’s say you set **Default size** to 100 and the **Maximum size** to 1000. When you create a high risk deployment, the **Select Collection** window will only display collections that contain less than 100 clients. If you clear the **Hide collections with a member count greater than the site’s minimum size configuration** setting, the window will display collections that contain less than 1000 clients.  
  
-   **Collections with site system servers**: Block deployments, or require verification before creating the deployment, when the target collection contains a computer with a site system role. When a deployment is blocked, you must select a different collection that meets the deployment verification criteria.  
  
> [!NOTE]  
>  High-risk deployments are always limited to custom collections, collections that you create, and the built-in **Unknown Computers** collection. When you create a high-risk deployment, you cannot select a built-in collection such as **All Systems**.  
  
### To configure deployment verification for a site  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration** >**Site Configuration** > **Sites**, and then click the primary site to configure.  
  
2.  On the **Home** tab, in the **Properties** group, click **Properties**, and then click the **Deployment Verification** tab.  
  
3.  After setting configurations you want to use, click  **OK**  to save the configuration.  
  
## See Also  
 [Configure sites and hierarchies for System Center Configuration Manager](../System Center Configuration Manager/Configure-sites-and-hierarchies-for-System-Center-Configuration-Manager.md)