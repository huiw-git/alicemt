---
title: "How to import configuration data with System Center Configuration Manager"
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
ms.assetid: 309b9a09-a611-4ba2-90ab-dde51582cf87
caps.latest.revision: 6
caps.handback.revision: 0
---
# How to import configuration data with System Center Configuration Manager
In addition to creating configuration baselines and configuration items in the [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] console, you can import configuration data if it is contained in a cabinet (.cab) file format and adheres to the supported SML schema. You can import configuration data from the following sources:  
  
-   Best practice configuration data (Configuration Packs) that has been downloaded from Microsoft or from other software vendor sites.  
  
-   Configuration data that has been exported from System Center 2012 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and later.  
  
-   Configuration data that was externally authored and that conforms to the Service Modeling Language (SML) schema.  
  
 For an example Configuration Pack that helps you manage compliance for System Center 2012 Configuration Manager site server roles, see [System Center 2012 Configuration Manager Configuration Pack](http://www.microsoft.com/en-us/download/details.aspx?id=30710&WT.mc_id=rss_alldownloads_all).  
  
## How to import configuration data  
 When you import a configuration baseline, some or all of the configuration items that are referenced in the configuration baseline might also be included in the cabinet file. During the import process, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] verifies that all of the configuration items that are referenced in the configuration baseline are either also included in the cabinet file or already exist in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. The import process fails if you attempt to import a configuration baseline that references configuration data that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot locate.  
  
 Other scenarios where the import process might fail include the following:  
  
-   The configuration data references configuration data that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] cannot locate, either in its database or in the cabinet file itself.  
  
-   The configuration data is already present in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database with the same name and configuration data version, but the content version differs.  
  
-   The configuration data is already present in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database with the same content version, but the hash calculation identifies it as being different.  
  
-   A newer version of the configuration data with same name is already present or has recently been deleted in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database.  
  
-   In a multi-site [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy, the configuration data was originally imported from a parent site. You must update it from the same site and not a child site.  
  
#### To import configuration data  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, expand **Configuration Items** or **Configuration Baselines**, and then in the **Home** tab, in the **Create** group, click **Import Configuration Data**.  
  
3.  On the **Select Files** page of the **Import Configuration Data Wizard**, click **Add**, and then in the **Open** dialog box, select the .cab files you want to import.  
  
4.  Select the **Create a new copy of the imported configuration baselines and configuration items** check box if you want the imported configuration data to be editable in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
5.  On the **Summary** page of the wizard, review the actions that will be taken, and then complete the wizard.  
  
 The imported configuration data displays in the **Compliance Settings** node in the **Assets and Compliance** workspace.  
  
## See Also  
 [Compliance settings technical reference for System Center Configuration Manager](../System Center Configuration Manager/Compliance-settings-technical-reference-for-System-Center-Configuration-Manager.md)