---
title: View Data Conflicts for Transactional Publications (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
---
# View Data Conflicts for Transactional Publications (SQL Server Management Studio)
  You can view conflicts for peer\-to\-peer transactional replication and transactional replication with queued updating subscriptions in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Replication Conflict Viewer. For information about how conflicts are detected and resolved, see [Conflict Detection in Peer-to-Peer Replication](../../Topics\TopicNameNotContainA/Conflict-Detection-in-Peer-to-Peer-Replication.md) and [Set Queued Updating Conflict Resolution Options &#40;SQL Server Management Studio&#41;](../Topic/Set%20Queued%20Updating%20Conflict%20Resolution%20Options%20\(SQL%20Server%20Management%20Studio\).md).  
  
 The availability of conflict data depends on the type of replication and the conflict retention period:  
  
-   For peer\-to\-peer replication, by default, the Distribution Agent fails when it detects a conflict. A conflict error is logged into the error log, but no conflict data is logged into the conflict table; therefore it is not available for viewing. If the Distribution Agent is allowed to continue, a conflict is logged locally on each node where it was detected. For more information, see "Handling Conflicts" in [Conflict Detection in Peer-to-Peer Replication](../../Topics\TopicNameNotContainA/Conflict-Detection-in-Peer-to-Peer-Replication.md).  
  
-   For queued updating subscriptions, data is available for every conflict. Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period, with a default of 14 days. To set the conflict retention period, perform either of the following:  
  
    -   Specify a retention value for the @conflict\_retention parameter of [sp\_addpublication](../Topic/sp_addpublication%20\(Transact-SQL\).md).  
  
    -   Specify a value of **'conflict\_retention'** for the @property parameter and a retention value for the @value parameter of [sp\_changepublication](../Topic/sp_changepublication%20\(Transact-SQL\).md).  
  
### To view conflicts  
  
1.  Connect to the appropriate server in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node:  
  
    -   For peer\-to\-peer replication, this is the node at which the conflict occurred.  
  
    -   For queued updating subscriptions, this is the Publisher.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Right\-click the publication for which you want to view conflicts, and then click **View Conflicts**.  
  
4.  In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.  
  
5.  In the Replication Conflict Viewer, you can:  
  
    -   Filter rows with the buttons to the right of the upper grid.  
  
    -   Select a row in the upper grid to display information on that row in the lower grid.  
  
    -   Select one or more rows in the upper grid, and then click **Remove**, which removes the row from the conflicts metadata table.  
  
    -   Click the properties button \(**…**\) to view more information on a column involved in a conflict.  
  
    -   Select **Log the details of this conflict** to log conflict data to a file. To specify a location for the file, point to the **View** menu, and then click **Options**. Enter a value, or click the browse button \(**...**\), and then navigate to the appropriate file. Click **OK** to close the **Options** dialog box.  
  
6.  Close the Replication Conflict Viewer.  
  
## See Also  
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)   
 [Queued Updating Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Queued-Updating-Conflict-Detection-and-Resolution.md)  
  
  