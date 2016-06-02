---
title: Manage the Size of the Transaction Log File
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-transaction-log
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
---
# Manage the Size of the Transaction Log File
  In some cases, it can be useful to physically shrink or expand the physical log file of the transaction log of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database. This topic contains information about how to monitor the size of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] transaction log, shrink the transaction log, add or enlarge a transaction log file, optimize the **tempdb** transaction log growth rate, and control the growth of a transaction log file.  
  
 **In This Topic:**  
  
-   [Monitor Log Space Use](#MonitorSpaceUse)  
  
-   [Shrink the Size of the Log File](#ShrinkSize)  
  
-   [Add or Enlarge a Log File](#AddOrEnlarge)  
  
-   [Optimizing the Size of the tempdb Transaction Log](#tempdbOptimize)  
  
-   [Control the Growth of a Transaction Log File](#ControlGrowth)  
  
##  <a name="MonitorSpaceUse"></a> Monitor Log Space Use  
 You can monitor log space use by using DBCC SQLPERF \(LOGSPACE\). This command returns information about the amount of log space currently used and indicates when the transaction log is in need of truncation. For more information, see [DBCC SQLPERF &#40;Transact-SQL&#41;](../Topic/DBCC%20SQLPERF%20\(Transact-SQL\).md). For information about the current size of a log file, its maximum size, and the autogrow option for the file, you can also use the **size**, **max\_size**, and **growth** columns for that log file in **sys.database\_files**. For more information, see [sys.database_files &#40;Transact-SQL&#41;](../Topic/sys.database_files%20\(Transact-SQL\).md).  
  
> [!IMPORTANT]  
>  We recommend that you avoid overloading the log disk.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="ShrinkSize"></a> Shrink the Size of the Log File  
 To reduce the physical size of a physical log file, you must shrink the log file. This is useful if you know that a transaction log file contains unused space that you will not be needing. Shrinking a log file can occur only while the database is online and, also, at least one virtual log file is free. In some cases, shrinking the log may not be possible until after the next log truncation.  
  
> [!NOTE]  
>  Factors, such as a long\-running transaction, that keep virtual log files active for an extended period can restrict log shrinkage or even prevent the log from shrinking at all. For information about factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](../Topic/The%20Transaction%20Log%20\(SQL%20Server\).md).  
  
 Shrinking a log file removes one or more virtual log files that do not hold any part of the logical log \(that is, *inactive virtual log files*\). When a transaction log file is shrunk, enough inactive virtual log files are removed from the end of the log file to reduce the log to approximately the target size.  
  
 **To shrink a log file \(without shrinking database files\)**  
  
-   [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../Topic/DBCC%20SHRINKFILE%20\(Transact-SQL\).md)  
  
-   [Shrink a File](../../Topics\TopicNameContainA/Shrink-a-File.md)  
  
 **To monitor log\-file shrink events**  
  
-   [Log File Auto Shrink Event Class](../../Topics\TopicNameNotContainA/Log-File-Auto-Shrink-Event-Class.md).  
  
 **To monitor log space**  
  
-   [DBCC SQLPERF &#40;Transact-SQL&#41;](../Topic/DBCC%20SQLPERF%20\(Transact-SQL\).md)  
  
-   [sys.database_files &#40;Transact-SQL&#41;](../Topic/sys.database_files%20\(Transact-SQL\).md) \(See the **size**, **max\_size**, and **growth** columns for the log file or files.\)  
  
> [!NOTE]  
>  Shrinking database and log files can be set to occur automatically. However, we recommend against automatic shrinking, and the **autoshrink** database property is set to FALSE by default. If **autoshrink** is set to TRUE, automatic shrinking reduces the size of a file only when more than 25 percent of its space is unused. The file is shrunk either to the size at which only 25 percent of the file is unused space or to the original size of the file, whichever is larger. For information about changing the setting of the **autoshrink** property, see [View or Change the Properties of a Database](../../Topics\TopicNameContainA/View-or-Change-the-Properties-of-a-Database.md)—use the **Auto Shrink** property on the **Options** page—or [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)—use the AUTO\_SHRINK option.  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="AddOrEnlarge"></a> Add or Enlarge a Log File  
 Alternatively, you can gain space by enlarging the existing log file \(if disk space permits\) or by adding a log file to the database, typically on a different disk.  
  
-   To add a log file to the database, use the ADD LOG FILE clause of the ALTER DATABASE statement. Adding a log file allows the log to grow.  
  
-   To enlarge the log file, use the MODIFY FILE clause of the ALTER DATABASE statement, specifying the SIZE and MAXSIZE syntax. For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="tempdbOptimize"></a> Optimize the Size of the tempdb Transaction Log  
 Restarting a server instance resizes the transaction log of the **tempdb** database to its original, pre\-autogrow size. This can reduce the performance of the **tempdb** transaction log. You can avoid this overhead by increasing the size of the **tempdb** transaction log after starting or restarting the server instance. For more information, see [tempdb Database](../../Topics\TopicNameNotContainA/tempdb-Database.md).  
  
 [&#91;Top&#93;](#Top)  
  
##  <a name="ControlGrowth"></a> Control the Growth of a Transaction Log File  
 You can use the [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md) statement to manage the growth of a transaction log file. Note the following:  
  
-   To change the current file size in KB, MB, GB, and TB units, use the SIZE option.  
  
-   To change the growth increment, use the FILEGROWTH option. A value of 0 indicates that automatic growth is set to off and no additional space is permitted. A small autogrowth increment on a log file can reduce performance. The file growth increment on a log file should be sufficiently large to avoid frequent expansion. The default growth increment of 10 percent is generally suitable.  
  
     For information on changing the file\-growth property on a log file, see [ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20\(Transact-SQL\).md).  
  
-   To control the maximum the size of a log file in KB, MB, GB, and TB units or to set growth to UNLIMITED, use the MAXSIZE option.  
  
 [&#91;Top&#93;](#Top)  
  
## See Also  
 [BACKUP &#40;Transact-SQL&#41;](../Topic/BACKUP%20\(Transact-SQL\).md)   
 [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../Topic/Troubleshoot%20a%20Full%20Transaction%20Log%20\(SQL%20Server%20Error%209002\).md)  
  
  