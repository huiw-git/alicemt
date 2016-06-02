---
title: Delete Catalog Items (Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0599e01-6dc3-4484-80d4-022a412e0ebd
---
# Delete Catalog Items (Management Studio)
  Use this page to delete shared schedules and role definitions.  
  
 If you delete a shared schedule that is used by multiple reports and subscriptions, the report server will create individual schedules for each report and subscription that previously used the shared schedule. Each new individual schedule will contain the date, time, and recurrence pattern that was specified in the shared schedule. Note that [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] does not provide central management of individual schedules. If you delete a shared schedule, you will now need to maintain the schedule information for each individual item. Before deleting a shared schedule, use the [Reports page](../Topic/Schedule%20Properties%20\(Reports%20Page\).md) to determine which reports are currently using the shared schedule.  
  
 For role definitions, you can only delete those that are not actively used in a role assignment. If you try to delete a role that is currently in use, the report server will not delete the role and you will see an error message to that effect. If this page contains a single role definition that is not currently in use, it will be deleted when you click **OK**. If this page contains multiple roles, you cannot select which roles to keep or remove. All unused role definitions will be deleted when you click **OK**.  
  
 You cannot undo a delete operation. If you want to recover an item that you deleted, you must either recreate it or restore a backup copy of the report server database.  
  
## Options  
 **Name**  
 Specifies the name of the item you are deleting.  
  
 **Type**  
 Shows the type of item you are deleting.  
  
 **Owner**  
 Shows the name of the owner. In most cases, this is System.  
  
 **Status**  
 Shows progress information for a delete operation.  
  
 **Error**  
 Displays an error code if an error occurs while deleting an item.  
  
## See Also  
 [Delete an Item &#40;Management Studio&#41;](../Topic/Delete%20an%20Item%20\(Management%20Studio\).md)   
 [Report Server in Management Studio F1 Help](../../Topics\TopicNameNotContainA/Report-Server-in-Management-Studio-F1-Help.md)   
 [Create, Modify, and Delete Schedules](../../Topics\TopicNameNotContainA/Create,-Modify,-and-Delete-Schedules.md)  
  
  