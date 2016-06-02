---
title: Create, Modify, and Delete Snapshots in Report History
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
---
# Create, Modify, and Delete Snapshots in Report History
  Report history is a collection of report snapshots. You can maintain report history by adding and deleting snapshots, or by modifying properties that affect report history storage. You can create report history manually or on a schedule.  
  
 To create report history, your role assignment must include the "Manage report history" task. To view report history, your role assignment must include the "View reports" task. Report history is available to all users who have access to the report. You cannot selectively enable or disable report history for a subset of users.  
  
 Snapshots in report history are identified by the date and time that they were created. The date and time is based on when the query executed.  
  
## Creating Snapshots in Report History  
 Snapshots can be created manually or at scheduled intervals for any report that can run unattended. To run unattended, the report must use stored credentials or no credentials at all. Furthermore, if the report uses parameters, you must specify default values to use when the report runs. You can specify stored credentials and parameter values in the property pages for the report. For more information, see [Parameters Properties Page &#40;Report Manager&#41;](../Topic/Parameters%20Properties%20Page%20\(Report%20Manager\).md).  
  
 When you create a report snapshot, the following elements are stored along with the report snapshot in the report server database:  
  
-   The result set \(that is, the data in the report, retrieved through the credentials specified in the Data Sources properties page of the report\).  
  
-   The underlying report definition, as it exists at the time the snapshot was created. If the report definition is subsequently modified after the snapshot is generated, those changes are not reflected in the snapshot.  
  
-   Parameter values that are used to obtain or filter the result set.  
  
-   Embedded resources, such as images. External resources that are linked to a report are not stored with the report snapshot.  
  
 The ways in which report history can be created and the number of report snapshots that can be stored are determined by settings.  
  
 If a report produces an error, a snapshot is not created. Reports that produce warnings, yet still run, can be used to generate snapshots.  
  
## Modifying Properties and Deleting Report History  
 Once a report snapshot exists, you cannot modify it. However, you can modify properties in a way that deletes report history.  
  
 Report history can be deleted in the following ways:  
  
-   Manually delete snapshots singly or in groups.  
  
     You can delete snapshots from the History page in Report Manager. Navigate to the report, click History, select the check box next to the snapshots that you want to delete, and then click **Delete**.  
  
-   Lower the report history limit to reduce the number of snapshots that are stored. The report history limit can be set for the report server or for specific reports. When the limit is lowered, the oldest snapshots are deleted from history.  
  
 You cannot delete all report history stored on a report server in a bulk operation.  
  
 Report history is also deleted when you delete a report. For example, if you delete a monthly sales report because you are replacing it with a newer version, all report history that is associated with the report is also deleted. However, if you move a report, all report history moves with it.  
  
## See Also  
 [Create Report History &#40;Reporting Services in SharePoint Integrated Mode&#41;](../Topic/Create%20Report%20History%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)   
 [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Report Server Content Management &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Content%20Management%20\(SSRS%20Native%20Mode\).md)   
 [Add a Snapshot to Report History &#40;Report Manager&#41;](../Topic/Add%20a%20Snapshot%20to%20Report%20History%20\(Report%20Manager\).md)   
 [Limit Report History &#40;Report Manager&#41;](../Topic/Limit%20Report%20History%20\(Report%20Manager\).md)  
  
  