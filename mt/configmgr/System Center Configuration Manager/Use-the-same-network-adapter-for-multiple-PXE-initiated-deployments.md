---
title: "Use the same network adapter for multiple PXE initiated deployments"
ms.custom: na
ms.date: 08/22/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 39bc6d7f-7b14-4049-ae3c-2ab1d9845ef0
caps.latest.revision: 2
---
# Use the same network adapter for multiple PXE initiated deployments


### Use the same network adapter for multiple PXE initiated deployments
In Configuration Manager Technical Preview 1607, when you use an ethernet adapter to image multiple devices (such as a USB ethernet adapter on a Surface Pro), you can enable a new setting that allows you to enter hardware identifiers for the ethernet adapters. Configuration Manager ignores the hardware identifiers in the list when performing a PXE installation and for client registration. 

For more information about this issue, see the [Configuration Manager OSD Support Team Blog](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/)  

#### Enable the feature to manage duplicate hardware identifiers  
1. In the Configuration Manager console, go to **Administration** > **Overview** > **Cloud Services** > **Updates and Servicing** > **Features**.
2. In the display pane, select **Manage duplicate hardware identifiers**. 
3. On the **Home** tab, in the **Features** group, click **Turn on**. 

#### Add hardware identifiers for Configuration Manager to ignore  
1. In the Configuration Manager console, go to **Administration** > **Overview** > **Site Configuration** > **Sites**. 
2. On the **Home** tab, in the **Sites** group, click **Hierarchy Settings**. 
3. Go to the **Client Approval and Conflicting Records** tab. 
4. Click **Add** in the **Duplicate hardware identifiers** section to add new hardware identifiers.