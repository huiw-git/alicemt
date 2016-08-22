---
title: "How to test client upgrades in a preproduction collection in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 49ef2ed2-2e15-4637-8b63-1d5b7f9c17e1
caps.latest.revision: 10
caps.handback.revision: 0
---
# How to test client upgrades in a preproduction collection in System Center Configuration Manager
For upgrading the Configuration Manager client on Windows PCs and devices, you can test a new client version in a preproduction collection before upgrading the rest of the site with it.  When you do this, only devices that are part of the preproduction collection upgraded to the new client. Once you've had a chance to test the client in this preproduction collection, you can promote the client, which makes the new version of the client software available to the rest of the site.  
  
 There are 3 basic steps to testing clients in preproduction  
  
1.  [To configure automatic client upgrades to use a preproduction collection](#BKMK_config) to use a preproduction collection.  
  
2.  [To install a Configuration Manager update that includes a new version of the client](#BKMK_install) that includes a new version of the client. During the install, you specify to use a preproduction collection for the new client software.  
  
3.  [To promote the new client to production](#BKMK_promote) after you've tested it sufficiently in preproduction.  
  
> [!TIP]  
>  [!INCLUDE[cm-client-upgrade-tip](../System Center Configuration Manager/itokens/cm-client-upgrade-tip_md.md)]  
  
##  <a name="BKMK_config"></a> To configure automatic client upgrades to use a preproduction collection  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console open **Administration** > **Site Configuration** > **Sites**, and click **Hierarchy Settings**.  
  
     On the **Client Upgrade** tab of the **Hierarchy Settings Properties**:  
  
    -   Select **Upgrade all clients in the pre-production collection automatically using pre-production client**  
  
    -   Enter the name of a collection to use as a pre-production collection  
  
2.  Click **OK** to save the Client Upgrade settings.  
  
##  <a name="BKMK_install"></a> To install a Configuration Manager update that includes a new version of the client  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console,  open **Administration** > **Cloud Services** > **Updates and Services**, select an **Available** update, and then click **Install Update Pack**  
  
     For more information on installing updates, see [Updates for System Center Configuration Manager](../System Center Configuration Manager/Updates-for-System-Center-Configuration-Manager.md)  
  
2.  During installation of the update, on the **Client Options** page of the wizard, select **Test in pre-production collection**, click **Next**.  
  
3.  Complete the rest of the wizard and install the update pack.  
  
     After the wizard complete, clients in the pre-production collection will begin to deploy the updated client. You can monitor the deployment of upgraded clients by going to **Monitoring** > **Client Status** > **Pre-production Client Deployment**. For more information, see [How to monitor client deployment status in System Center Configuration Manager](../System Center Configuration Manager/How-to-monitor-client-deployment-status-in-System-Center-Configuration-Manager.md).
     
    > [!NOTE]
    > The deployment status on computers hosting site system roles in a pre-production collection may be reported as **Not Started** even when the client was successfully deployed. When you promote the client to production, the deployment status is reported correctly.
  
##  <a name="BKMK_promote"></a> To promote the new client to production  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, open **Administration** > **Cloud Services** > **Updates and Servicing**, and click  **Promote Pre-production Client**.

    > [!TIP]
    > The **Promote Pre-production Client** button is also available when you're monitoring client deployments in the console at **Monitoring** > **Client Status** > **Pre-production Client Deployment**.
  
2.  In the dialog box, review the client versions in production and pre-production, make sure the correct the pre-production collection is specified, and then  click **Promote**. In the confirmation box, click **Yes**.  
  
3.  After dialog box closes, the updated client version will replace the current client version in use in your hierarchy. You can then upgrade the clients for your whole site. See [How to upgrade clients for Windows computers in System Center Configuration Manager](../System Center Configuration Manager/How-to-upgrade-clients-for-Windows-computers-in-System-Center-Configuration-Manager.md) for more information.  
  
## See Also  
 [Upgrade clients in System Center Configuration Manager](../System Center Configuration Manager/Upgrade-clients-in-System-Center-Configuration-Manager.md)