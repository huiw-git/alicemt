---
title: "How to create configuration baselines in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-08-11
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 678c9622-c61b-47d1-ba25-690616e431c7
caps.latest.revision: 5
caps.handback.revision: 0
---
# How to create configuration baselines in System Center Configuration Manager
Configuration baselines in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] contain predefined configuration items and optionally, other configuration baselines. After a configuration baseline is created, you can deploy it to a collection so that devices in that collection download the configuration baseline and assess their compliance with it.  
  
 Configuration baselines in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] can contain specific revisions of configuration items or can be configured to always use the latest version of a configuration item. For more information about configuration item revisions, see [Management tasks for configuration data in System Center Configuration Manager](../System Center Configuration Manager/Management-tasks-for-configuration-data-in-System-Center-Configuration-Manager.md).  
  
 There are two methods that you can use to create configuration baselines in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]:  
  
-   Import configuration data from a file. To start the **Import Configuration Data Wizard**, in the **Configuration Items** or **Configuration Baselines** node in the **Assets and Compliance** workspace, click **Import Configuration Data**.  
  
-   Use the **Create Configuration Baseline** dialog box to create a new configuration baseline.  
  
 Use the following procedure to create a configuration baseline by using the **Create Configuration Baseline** dialog box.  
  
### To create a configuration baseline  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Compliance Settings**, and then click **Configuration Baselines**.  
  
3.  On the **Home** tab, in the **Create** group, click **Create Configuration Baseline**.  
  
4.  In the **Create Configuration Baseline** dialog box, enter a unique name and a description for the configuration baseline. You can use a maximum of 255 characters for the name and 512 characters for the description.  
  
5.  The **Configuration data** list displays all configuration items or configuration baselines that are included in this configuration baseline. Click **Add** to add a new configuration item or configuration baseline to the list. You can choose from the following:  
  
    -   **Configuration Items**  
  
    -   **Software Updates**  
  
    -   **Configuration Baselines**  
      > [!IMPORTANT]
      > You must limit each configuration baseline to no more than 1000 software updates.
6.  Use the **Change Purpose** list to specify the behavior of a configuration item that you have selected in the **Configuration data** list. You can select from the following:  
  
    -   **Required** The configuration baseline is evaluated as noncompliant if the configuration item is not detected on a client device. If it is detected, it is evaluated for compliance  
  
    -   **Optional** The configuration item is only evaluated for compliance if the application it references is found on client computers. If the application is not found, the configuration baseline is not marked as noncompliant (only applicable to application configuration items).  
  
    -   **Prohibited** The configuration baseline is evaluated as noncompliant if the configuration item is detected on client computers (only applicable to application configuration items).  
  
    > [!NOTE]
    >  The **Change Purpose** list is available only if you clicked the option **This configuration item contains application settings** on the **General** page of the **Create Configuration Item Wizard**.  
  
7.  Use the **Change Revision** list to select a specific or the latest revision of the configuration item to assess for compliance on client devices or select **Always Use Latest** to always use the latest revision. For more information about configuration item revisions, see [Management tasks for configuration data in System Center Configuration Manager](../System Center Configuration Manager/Management-tasks-for-configuration-data-in-System-Center-Configuration-Manager.md).  
  
8.  If you want to remove a configuration item from the configuration baseline, select a configuration item, and then click **Remove**.  
  
9. Click **OK** to close the **Create Configuration Baseline** dialog box and to create the configuration baseline.  
  
## See Also  
 [Compliance settings technical reference for System Center Configuration Manager](../System Center Configuration Manager/Compliance-settings-technical-reference-for-System-Center-Configuration-Manager.md)