---
title: "Manage Office 365 ProPlus updates with Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
caps.latest.revision: 8
---
# Manage Office 365 ProPlus updates with Configuration Manager
Beginning in Configuration Manager version 1602, Configuration Manager has the ability to manage Office 365 client updates by using the software update management workflow. When Microsoft publishes a new Office 365 client update to the Office Content Delivery Network (CDN), Microsoft also publishes an update package to Windows Server Update Services (WSUS). After Configuration Manager synchronizes the Office 365 client update from the WSUS catalog to the site server, the update is available to deploy to clients. 

## To deploy Office 365 updates with Configuration Manager
Use the following steps to deploy Office 365 updates with Configuration Manager:
  
1.  [Verify the requirements](https://technet.microsoft.com/library/mt628083.aspx) for using Configuration Manager to manage Office 365 client updates in the **Requirements for using Configuration Manager to manage Office 365 client updates** section of the topic.  
  
2.  [Configure software update points](https://technet.microsoft.com/library/mt612804.aspx) to synchronize the Office 365 client updates. Set **Updates** for the classification and select **Office 365 Client** for the product. You might have to synchronize software updates at least one time before the Office 365 Client product is available for you to choose. You must synchronize software updates after you configure the software update points to use the **Updates** classification.  
  
3.  Enable Office 365 clients to receive updates from Configuration Manager. You can do this by using Configuration Manager client settings or use group policy. Use one of the following methods to enable the client:  
    - Method 1: Beginning in Configuration Manager version 1606, you can use the Configuration Manager client setting to manage the Office 365 client agent. After you configure this setting and deploy Office 365 updates, the Configuration Manager client agent communicates with the Office 365 client agent to download Office 365 updates from a distribution point and install them. Configuration Manager takes inventory of Office 365 ProPlus Client settings. 
      1.  In the Configuration Manager console, click **Administration** > **Overview** > **Client Settings**.  
      
      2.  Open the appropriate device settings to enable the client agent. For more information about default and custom client settings, see [How to configure client settings in System Center Configuration Manager](../System Center Configuration Manager/How-to-configure-client-settings-in-System-Center-Configuration-Manager.md).  
      
      3.  Click **Software Updates** and select **Yes** for the **Enable management of the Office 365 Client Agent** setting.  
      
    - Method 2: [Enable Office 365 clients to receive updates](https://technet.microsoft.com/library/mt628083.aspx) from Configuration Manager by using the Office Deployment Tool or Group Policy.  
  
4. [Deploy the Office 365 updates](https://technet.microsoft.com/library/mt613209.aspx#BKMK_SUMDeploy) to clients.  
  
  
## See Also
[Manage software updates in System Center Configuration Manager](../System Center Configuration Manager/Manage-software-updates-in-System-Center-Configuration-Manager.md)