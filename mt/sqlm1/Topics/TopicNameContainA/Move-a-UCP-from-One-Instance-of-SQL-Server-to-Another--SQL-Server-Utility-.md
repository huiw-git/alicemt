---
title: Move a UCP from One Instance of SQL Server to Another (SQL Server Utility)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
---
# Move a UCP from One Instance of SQL Server to Another (SQL Server Utility)
  This topic describes how to move a utility control point \(UCP\) from one instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to another in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
  
#### Move a UCP from one instance of SQL Server to another.  
  
1.  Create a new UCP on the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] that will be the new host instance of the UCP. For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](../Topic/Create%20a%20SQL%20Server%20Utility%20Control%20Point%20\(SQL%20Server%20Utility\).md).  
  
2.  If non\-default policy settings have been set for any instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility, make note of the policy thresholds so that you can re\-establish them on the new UCP. Default policies are applied when instances are added to the new UCP. If default policies are in effect, the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility list view displays **Global** in the **Policy Type** column.  
  
3.  Remove all managed instances from the old UCP. For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](../../Topics\TopicNameNotContainA/Remove-an-Instance-of-SQL-Server-from-the-SQL-Server-Utility.md).  
  
4.  Back up the utility management data warehouse \(UMDW\) from the old UCP. The filename is Sysutility\_mdw\_\<GUID\>\_DATA, and the database default location is \<System drive\>:\\Program Files\\Microsoft SQL Server\\MSSQL10\_50.\<UCP\_Name\>\\MSSQL\\Data\\, where \<System drive\> is normally the C:\\ drive. For more information, see [Copy Databases with Backup and Restore](../../Topics\TopicNameNotContainA/Copy-Databases-with-Backup-and-Restore.md).  
  
5.  Restore the backup of the UMDW to the new UCP. For more information, see [Copy Databases with Backup and Restore](../../Topics\TopicNameNotContainA/Copy-Databases-with-Backup-and-Restore.md).  
  
6.  Enroll instances into the new UCP to make them managed by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Utility. For more information, see [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../Topic/Enroll%20an%20Instance%20of%20SQL%20Server%20\(SQL%20Server%20Utility\).md).  
  
7.  Implement custom policy definitions for the managed instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], as necessary.  
  
8.  Wait approximately 1 hour for data collection and aggregation operations to complete.  
  
9. To refresh data, right\-click the **Managed Instances** node in **Utility Explorer**, then select **Refresh**. List view data are displayed in the **Utility Explorer** content pane. For more information, see [View Resource Health Policy Results &#40;SQL Server Utility&#41;](../Topic/View%20Resource%20Health%20Policy%20Results%20\(SQL%20Server%20Utility\).md).  
  
## See Also  
 [SQL Server Utility Features and Tasks](../../Topics\TopicNameNotContainA/SQL-Server-Utility-Features-and-Tasks.md)   
 [Enroll an Instance of SQL Server &#40;SQL Server Utility&#41;](../Topic/Enroll%20an%20Instance%20of%20SQL%20Server%20\(SQL%20Server%20Utility\).md)  
  
  