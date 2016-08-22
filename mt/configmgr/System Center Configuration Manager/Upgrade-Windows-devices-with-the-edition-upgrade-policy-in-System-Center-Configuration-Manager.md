---
title: "Upgrade Windows devices with the edition upgrade policy in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-19
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 45f20c53-2571-4dea-826d-d1d12d3b5aa0
caps.latest.revision: 11
caps.handback.revision: 0
---
# Upgrade Windows devices with the edition upgrade policy in System Center Configuration Manager
The [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]**Edition Upgrade Policy** lets you automatically upgrade devices that run one of the following Windows 10 versions to a newer edition:  
  
-   Windows 10 Desktop  
  
-   Windows 10 Mobile  
  
-   Windows 10 Holographic  
  
 The devices must be enrolled in Microsoft Intune. This feature is not currently compatible with PCs that run the Configuration Manager client software, or PCs that are managed by on-premises MDM. 
  
## Before you start  
 Before you begin to upgrade devices to the latest version, you will need one of the following:  
  
-   A product key which is valid to install the new version of Windows on all devices you target with the policy (for desktop operating systems)  
  
-   A licence file from Microsoft which contains the licensing information to install the new version of Windows on all devices you target with the policy (for Windows 10 Mobile and Windows 10 Holographic).

- To create and deploy this policy type, you must have been assigned the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] **Full Administrator** security role.
  
## Configure the edition upgrade policy  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Windows 10 Edition Upgrade**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Edition Upgrade Policy**.  
  
4.  Click **Create Policy**.  
  
5.  On the **General** page of the **Create Edition Upgrade Policy Wizard**, specify the following information:  
  
    -   **Name** - Enter a name for the edition upgrade policy.  
  
    -   **Description** (optional) - Optionally, enter a description for the policy that helps you identify it in the Intune console.  
  
    -   **SKU to upgrade device to** - From the drop-down list, select the version of Windows 10 Desktop, Windows 10 Holographic, or Windows 10 Mobile that you want to upgrade targeted devices to.  
  
    -   **License information** - Select one of:  
  
        -   **Product Key** - Enter a valid Windows 10 product key that will be used to upgrade devices you target that run Windows 10 Desktop operating systems.  
  
            > [!NOTE]  
            >  After you create a policy containing a product key, you cannot edit the product key later. This is because the key is obscured for security reasons. To change the product key, you must re-enter the entire key.  
  
        -   **License File** - Click **Browse** to select a valid license file in XML format that will be used to upgrade devices you target that run Windows 10 Holographic and Windows 10 Mobile operating systems.  
  
6.  Complete the wizard.  
  
 The new policy is displayed in the **Windows 10 Edition Upgrade** node of the **Assets and Compliance** workspace.  
  
## Deploy the edition upgrade policy  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Windows 10 Edition Upgrade**.  
  
3.  Select the Windows 10 edition upgrade policy you want to deploy and then, on the **Home** tab, in the **Deployment** group, click **Deploy**.  
  
4.  In the **Deploy Windows 10 Edition Upgrade** dialog box, choose the user or device collection to which you want to deploy the policy and the schedule by which the policy will be evaluated, and then click **OK**.  
  
 You can monitor the deployment you just created from the **Deployments** node of the **Monitoring** workspace.  
  
 Once the policy reaches a targeted Windows PC, the PC will be restarted within two hours to apply the upgrade. Ensure you inform any users to which you deploy the policy, or schedule the policy to run outside of the users working hours. 
  
## See Also  
 [Ensure device compliance with System Center Configuration Manager](../System Center Configuration Manager/Ensure-device-compliance-with-System-Center-Configuration-Manager.md)