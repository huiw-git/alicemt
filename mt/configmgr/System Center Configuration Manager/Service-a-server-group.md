---
title: "Service a server group"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 304a83ea-0f72-437d-9688-2e6e0c7526dd
caps.latest.revision: 4
---
# Service a server group
Starting in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] version 1606, you can configure server group settings for a collection to define how many, what percentage, or in what order computers in the collection will install software updates. You can also configure pre-deployment and post-deployment PowerShell scripts to run custom actions. 

When you deploy software updates to a collection that has server group settings configured, [!INCLUDE[cmshort_md](../System Center Configuration Manager/itokens/cmshort_md.md)] determines how many computers in the collection can install the software updates at any given time and makes the same number of deployment locks available. Only computers that get a deployment lock will start software update installation. When a deployment lock is available, a computer gets the deployment lock, installs the software updates, and then releases the deployment lock when software updates installation successfully completes. Then, the deployment lock becomes available for other computers. If a computer is unable to release a deployment lock, you can manually release all server group deployment locks for the collection.

>[!IMPORTANT]
>All of the computers in the collection must be assigned to the same site. 

### Create a collection for a server group  
The server group settings are configured in the properties for a device collection. To service a server group, all members in the collection must be assigned to the same site. Use the following steps to create a collection and configure the server group settings: 
1.  [Create a device collection](https://technet.microsoft.com/library/gg712295.aspx) that contains the computers in the server group.  
  
2.  In the **Assets and Compliance** workspace, click **Device Collections**, right-click the collection that contains the computers in the server group, and then click **Properties**.  
  
3.  On the **General** tab, select **All devices are part of the same server group**, and then click **Settings**.  
  
4.  On the **Server Group Settings** page, specify one of the following settings:  
  
    -   **Allow a percentage of machines to be updated at the same time**: Specifies that only a certain percentage of clients are updated at any one time. If, for example, the collection has 10 clients, and the collection is configured to update 30% of clients at the same time, then only 3 clients will install software updates at any given time.  
  
    -   **Allow a number of machines to be updated at the same time**: Specifies that only a certain number of clients are updated at any one time.  
  
    -   **Specify the maintenance sequence**: Specifies that the clients in the collection will be updated one at a time in the sequence that you configure. A client will only install software updates after the client that is ahead of it in the list has finished installing its software updates.  
  
5.  Specify whether to use a pre-deployment (node drain) script or post-deployment (node resume) script.  
  
    > [!TIP]  
    >The following are examples that you can use in testing for pre-deployment and post-deployment scripts that write the current time to a text file:  
    >   
    >  **Pre-deployment**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Post-deployment**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  
  
### Deploy software updates to the server group and monitor status  
You deploy software updates to the server group collection by using the typical deployment process. After you deploy the software updates, you can monitor the software update deployment in the [!INCLUDE[cmshort_md](../System Center Configuration Manager/itokens/cmshort_md.md)] console.
1.  [Deploy software updates](https://technet.microsoft.com/library/gg712304.aspx) to the server group collection.   
  
2.  [Monitor the software update deployment](https://technet.microsoft.com/library/gg712304.aspx). In addition to the standard monitoring views for software updates deployment, the **Waiting for lock** state is displayed when a client is waiting for its turn to install the software updates. You can review the UpdatesDeployment.log file for more information.
  
  
### Clear the deployment locks for computers in a server group  
When a computer fails to release a deployment lock, you can manually release all server group deployment locks for the collection. Clear locks only when a deployment is stuck updating computers in the collection and there are computers that are still not compliant.  
1.  In the **Assets and Compliance** workspace, click **Device Collections**, and click the collection to clear deployment locks.  
  
2.  On the **Home** tab, in the **Deployment** group, click **Clear Server Group Deployment Locks**. When clients have failed to install the software updates and are preventing other clients from installing their software updates, the deployment locks can be manually cleared.  