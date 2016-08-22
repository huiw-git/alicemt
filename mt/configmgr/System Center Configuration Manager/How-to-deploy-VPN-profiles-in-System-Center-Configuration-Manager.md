---
title: "How to deploy VPN profiles in System Center Configuration Manager"
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
ms.assetid: bebe9d4b-66f0-41a6-9924-c42e18298690
caps.latest.revision: 5
caps.handback.revision: 0
---
# How to deploy VPN profiles in System Center Configuration Manager
VPN profiles in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] must be deployed to one or more collections before they can be used.  
  
 Use the **Deploy VPN Profile** dialog box to configure the deployment of VPN profiles. As part of the configuration, you define the collection to which the VPN profile is to be deployed and specify how often the VPN profile is evaluated for compliance.  
  
> [!NOTE]  
>  If you deploy multiple company resource access profiles to the same user, the following behavior occurs:  
>   
>  -   If a conflicting setting contains an optional value, it will not be sent to the device.  
> -   If a conflicting setting contains a mandatory value, the default value will be sent to the device. If there is no default value, the entire company resource access profile will fail.  
  
> [!NOTE]  
>  When a VPN profile deployment is removed, the VPN profile is not removed from client devices. If you want to remove the profile from devices, you must manually remove it.  
  
## VPN profile deployment  
 Follow these steps to deploy a VPN profile.  
  
#### To deploy a VPN profile  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, expand **Company Resource Access**, and then click **VPN Profiles**.  
  
3.  In the **VPN Profiles** list, select the VPN profile that you want to deploy, and then in the **Home** tab, in the **Deployment** group, click **Deploy**.  
  
4.  In the **Deploy VPN Profile** dialog box, specify the following information:  
  
    -   **Collection** - Click **Browse** to select the collection where you want to deploy the VPN profile.  
  
    -   **Generate an alert** - Enable this option to configure an alert that is generated if the VPN profile compliance is less than a specified percentage by a specified date and time. You can also specify whether you want an alert to be sent to System Center Operations Manager.  
  
    -   **Specify the compliance evaluation schedule for this VPN profile** - Specify the schedule by which the deployed VPN profile is evaluated on client computers. The schedule can be either a simple or a custom schedule.  
  
        > [!NOTE]  
        >  The profile is evaluated by client computers when the user logs on.  
  
5.  Click **OK** to close the **Deploy VPN Profile** dialog box and to create the deployment. For more information about how to monitor the deployment, see [How to monitor VPN profiles in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-VPN-profiles-in-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Operations and maintenance for VPN profiles in System Center Configuration Manager](../System Center Configuration Manager/Operations-and-maintenance-for-VPN-profiles-in-System-Center-Configuration-Manager.md)