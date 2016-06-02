---
title: View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
---
# View and Resolve Data Conflicts for Merge Publications (SQL Server Management Studio)
  Conflicts in merge replication are resolved based on the resolver specified for each article. By default, conflicts are resolved without the need for user intervention. But conflicts can be viewed, and the outcome of the resolution can be changed, in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Replication Conflict Viewer.  
  
 Conflict data is available in the Replication Conflict Viewer for the amount of time specified for the conflict retention period \(with a default of 14 days\). To set the conflict retention period, either:  
  
-   Specify a retention value for the **@conflict\_retention** parameter of [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md).  
  
-   Specify a value of **conflict\_retention** for the **@property** parameter and a retention value for the **@value** parameter of [sp_changemergepublication &#40;Transact-SQL&#41;](../Topic/sp_changemergepublication%20\(Transact-SQL\).md).  
  
 By default, conflict information is stored:  
  
-   At the Publisher and Subscriber if the publication compatibility level is 90RTM or higher.  
  
-   At the Publisher if the publication compatibility level is lower than 80RTM.  
  
-   At the Publisher if Subscribers are running [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)]. Conflict data cannot be stored on [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] Subscribers.  
  
 Storage of conflict information is controlled by the **conflict\_logging** publication property. For more information, see [sp_addmergepublication &#40;Transact-SQL&#41;](../Topic/sp_addmergepublication%20\(Transact-SQL\).md) and [sp_changemergepublication &#40;Transact-SQL&#41;](../Topic/sp_changemergepublication%20\(Transact-SQL\).md).  
  
 Conflicts can also be resolved interactively during synchronization using the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Interactive Resolver. The Interactive Resolver is available through the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Synchronization Manager. For more information, see [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../Topic/Synchronize%20a%20Subscription%20Using%20Windows%20Synchronization%20Manager%20\(Windows%20Synchronization%20Manager\).md).  
  
### To view and resolve conflicts for merge publications  
  
1.  Connect to the Publisher \(or Subscriber if appropriate\) in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], and then expand the server node.  
  
2.  Expand the **Replication** folder, and then expand the **Local Publications** folder.  
  
3.  Right\-click the publication for which you want to view conflicts, and then click **View Conflicts**.  
  
    > [!NOTE]  
    >  If you specified a value of **'subscriber'** for the **conflict\_logging** property, the **View Conflicts** menu option is not available. To view conflicts, start ConflictViewer.exe from the command prompt. By default, ConflictViewer.exe is located in the following directory: Microsoft SQL Server\\100\\Tools\\Binn\\VSShell\\Common7\\IDE. For a list of valid startup parameters, run ConflictViewer.exe \-?.  
  
4.  In the **Select Conflict Table** dialog box, select a database, publication, and table for which to view conflicts.  
  
5.  In the Replication Conflict Viewer, you can:  
  
    -   Filter rows with the buttons to the right of the upper grid.  
  
    -   Select a row in the upper grid to display information on that row in the lower grid.  
  
    -   Select one or more rows in the upper grid, and then click **Remove**, which is equivalent to clicking the **Submit Winner** button \(without making any changes to the data\).  
  
    -   Click the properties button \(**…**\) to view more information on a column involved in a conflict.  
  
    -   Edit data in the **Conflict winner** or **Conflict loser** column before submitting the data \(data is read\-only if the column is gray\).  
  
    -   Click **Submit Winner** to accept the row designated as the winner of the conflict.  
  
    -   Click **Submit Loser** to override the resolution and to propagate the value designated as the loser of the conflict to all nodes in the topology.  
  
    -   Select **Log the details of this conflict** to log conflict data to a file. To specify a location for the file, point to the **View** menu, and then click **Options**. Enter a value, or click the browse button \(**...**\), and then navigate to the appropriate file. Click **OK** to exit the **Options** dialog box.  
  
6.  Close the Replication Conflict Viewer.  
  
## See Also  
 [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md)   
 [Specify a Merge Article Resolver](../../Topics\TopicNameContainA/Specify-a-Merge-Article-Resolver.md)  
  
  