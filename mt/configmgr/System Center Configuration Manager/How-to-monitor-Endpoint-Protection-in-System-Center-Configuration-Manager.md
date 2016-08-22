---
title: "How to monitor Endpoint Protection in System Center Configuration Manager"
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
ms.assetid: f4a1335c-bb3d-493e-a124-83a32a107dc8
caps.latest.revision: 8
---
# How to monitor Endpoint Protection in System Center Configuration Manager
You can monitor [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in your [!INCLUDE[cm5long](../System Center Configuration Manager/itokens/cm5long_md.md)] hierarchy by using the **[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] Status** node in the **Monitoring** workspace, the **[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)]** node in the **Assets and Compliance** workspace, and by using reports.  
  
##  <a name="BKMK_1"></a> How to Monitor [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] by Using the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] Status Node  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Monitoring**.  
  
2.  In the **Monitoring** workspace, click **[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] Status**.  
  
3.  In the **Collection** list, select the collection for which you want to view status information.  
  
    > [!IMPORTANT]  
    >  Collections are available for selection in the following cases:  
    >   
    >  -   When you select **View this collection in the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] dashboard** on the **Alerts** tab of the *<collection name\>***Properties** dialog box.  
    > -   When you deploy an [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] antimalware policy to the collection.  
    > -   When you enable and deploy [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] client settings to the collection.  
  
4.  Review the information that is displayed in the **Security State** and **Operational State** sections. You can click any status link to create a temporary collection in the **Devices** node in the **Assets and Compliance** workspace. The temporary collection contains the computers with the selected status.  
  
    > [!IMPORTANT]  
    >  Information that is displayed in the **[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] Status** node is based on the last data that was summarized from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database and might not be current. If you want to retrieve the latest data, on the **Home** tab, click **Run Summarization**, or click **Schedule Summarization** to adjust the summarization interval.  
  
##  <a name="BKMK_2"></a> How to Monitor [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in the Assets and Compliance Workspace  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Assets and Compliance**.  
  
2.  In the **Assets and Compliance** workspace, perform one of the following actions:  
  
    -   Click **Devices**. In the **Devices** list, select a computer, and then click the **Malware Detail** tab.  
  
    -   Click **Device Collections**. In the **Device Collections** list, select the collection that contains the computer you want to monitor and then, on the **Home** tab, in the **Collection** group, click **Show Members**.  
  
3.  In the *<collection name\>* list, select a computer, and then click the **Malware Detail** tab.  
  
##  <a name="BKMK_3"></a> How to Monitor [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] by Using Reports  
 Use the following reports to help you view information about [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] in your hierarchy. You can also use these reports to help troubleshoot any [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] problems. For more information about how to configure reporting in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md) and [Log files in System Center Configuration Manager](../System Center Configuration Manager/Log-files-in-System-Center-Configuration-Manager.md). The [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] reports are in the [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] folder.  
  
|Report name|Description|  
|-----------------|-----------------|  
|**Antimalware Activity Report**|Displays an overview of antimalware activity for a specified collection.|  
|**Infected Computers**|Displays a list of computers on which a specified threat is detected.|  
|**Top Users By Threats**|Displays a list of users with the most number of detected threats.|  
|**User Threat List**|Displays a list of threats that were found for a specified user account.|  
  
## Malware Alert Levels  
 Use the following table to identify the different [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] alert levels that might be displayed in reports, or in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
|Alert level|Description|  
|-----------------|-----------------|  
|**Failed**|[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] failed to remediate the malware. Check your logs for details of the error.<br /><br /> **Note:** For a list of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and [!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] log files, see the "Endpoint Protection" section in the [Log files in System Center Configuration Manager](../System Center Configuration Manager/Log-files-in-System-Center-Configuration-Manager.md) topic.|  
|**Removed**|[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] successfully removed the malware.|  
|**Quarantined**|[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] moved the malware to a secure location and prevented it from running until you remove it or allow it to run.|  
|**Cleaned**|The malware was cleaned from the infected file.|  
|**Allowed**|An administrative user selected to allow the software that contains the malware to run.|  
|**No Action**|[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] took no action on the malware. This might occur if the computer is restarted after malware is detected and the malware is no longer detected; for instance, if a mapped network drive on which malware is detected is not reconnected when the computer restarts.|  
|**Blocked**|[!INCLUDE[epshort](../System Center Configuration Manager/itokens/epshort_md.md)] blocked the malware from running. This might occur if a process on the computer is found to contain malware.|