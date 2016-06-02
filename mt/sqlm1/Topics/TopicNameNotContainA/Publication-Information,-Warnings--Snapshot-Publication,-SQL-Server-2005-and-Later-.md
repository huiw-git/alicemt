---
title: Publication Information, Warnings (Snapshot Publication, SQL Server 2005 and Later)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
---
# Publication Information, Warnings (Snapshot Publication, SQL Server 2005 and Later)
  The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. The **Warnings** tab allows you to perform the following tasks for the selected publication:  
  
-   Enable warnings.  
  
-   Specify thresholds associated with warnings.  
  
-   Define alerts associated with warnings.  
  
## Warnings, Thresholds, and Alerts  
 By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information. For snapshot publications, you can also specify that imminent subscription expiration results in a warning by setting the option **Warn if a subscription will expire within the threshold**. If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon\/Expired** \(unless an issue with a higher priority needs to be displayed\).  
  
 In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert. Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.  
  
## Options  
 **Enabled**  
 Select to enable a warning and specify a threshold.  
  
 **Warning**  
 A description of the warning associated with a threshold.  
  
 **Threshold**  
 Specify a value for the threshold.  
  
 **Configure Alerts**  
 Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box. The dialog box allows you to define an alert, which is associated with the selected threshold and warning.  
  
 **Discard Changes**  
 Click to discard any changes to warnings and thresholds.  
  
> [!NOTE]  
>  Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.  
  
 **Save Changes**  
 Click to save any changes to warnings and thresholds.  
  
## See Also  
 [Start the Replication Monitor](../../Topics\TopicNameNotContainA/Start-the-Replication-Monitor.md)   
 [View Information and Perform Tasks for a Publication &#40;Replication Monitor&#41;](../Topic/View%20Information%20and%20Perform%20Tasks%20for%20a%20Publication%20\(Replication%20Monitor\).md)   
 [Monitoring Replication](../../Topics\TopicNameNotContainA/Monitoring-Replication.md)  
  
  