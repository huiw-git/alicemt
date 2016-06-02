---
title: Bulk Insert Task Editor (Options Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
---
# Bulk Insert Task Editor (Options Page)
  Use the **Options** page of the **Bulk Insert Task Editor** dialog box to set properties for the bulk insert operation. The Bulk Insert task copies large amounts of data into a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] table or view.  
  
 To learn about working with bulk inserts, see [Bulk Insert Task](../../Topics\TopicNameNotContainA/Bulk-Insert-Task.md) and [BULK INSERT &#40;Transact-SQL&#41;](../Topic/BULK%20INSERT%20\(Transact-SQL\).md).  
  
## Options  
 **CodePage**  
 Specify the code page of the data in the data file.  
  
 **DataFileType**  
 Specify the data\-type value to use in the load operation.  
  
 **BatchSize**  
 Specify the number of rows in a batch. The default is the entire data file. If you set **BatchSize** to zero, the data is loaded in a single batch.  
  
 **LastRow**  
 Specify the last row to copy.  
  
 **FirstRow**  
 Specify the first row from which to start copying.  
  
 **Options**  
 |Term|Definition|  
|----------|----------------|  
|**Check constraints**|Select to check the table and column constraints.|  
|**Keep nulls**|Select to retain null values during the bulk insert operation, instead of inserting any default values for empty columns.|  
|**Enable identity insert**|Select to insert existing values into an identity column.|  
|**Table lock**|Select to lock the table during the bulk insert.|  
|**Fire triggers**|Select to fire any insert, update, or delete triggers on the table.|  
  
 **SortedData**  
 Specify the ORDER BY clause in the bulk insert statement. The column name that you supply must be a valid column in the destination table. The default is **false**. This means that the data is not sorted by an ORDER BY clause.  
  
 **MaxErrors**  
 Specify the maximum number of errors that can occur before the bulk insert operation is canceled. A value of 0 indicates that an infinite number of errors are allowed.  
  
> [!NOTE]  
>  Each row that cannot be imported by the bulk load operation is counted as one error.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Bulk Insert Task Editor &#40;General Page&#41;](../Topic/Bulk%20Insert%20Task%20Editor%20\(General%20Page\).md)   
 [Bulk Insert Task Editor &#40;Connection Page&#41;](../Topic/Bulk%20Insert%20Task%20Editor%20\(Connection%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  