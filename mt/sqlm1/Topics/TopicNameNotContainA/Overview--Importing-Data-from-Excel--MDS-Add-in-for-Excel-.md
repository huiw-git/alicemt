---
title: Overview: Importing Data from Excel (MDS Add-in for Excel)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
---
# Overview: Importing Data from Excel (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], publish data to the MDS repository when you want to share it with other users. As soon as data is published, it is available for other users of the Add\-in to download.  
  
 When you publish data, any data you’ve added or updated is published to the MDS repository. Data you’ve deleted is not published—you must delete data separately. For more information, see [Delete a Row &#40;MDS Add-in for Excel&#41;](../Topic/Delete%20a%20Row%20\(MDS%20Add-in%20for%20Excel\).md).  
  
> [!NOTE]  
>  Publishing cannot be used to create a new entity. For more information about creating entities, see [Create an Entity &#40;MDS Add-in for Excel&#41;](../Topic/Create%20an%20Entity%20\(MDS%20Add-in%20for%20Excel\).md).  
  
## When Multiple Users Publish at the Same Time  
 Multiple users can publish updates to the same data. As each user publishes, the update is saved to the database. This means that a user who was not working with the most recently\-updated data can still change the value when he or she publishes.  
  
 Only the updates you make are published to the database. Any out\-of\-date data in the worksheet is not published.  
  
## Transactions and Annotations  
 Each published change is saved as a transaction. If you choose, you can add annotations \(comments\) to a transaction, to explain why you made the change.  
  
-   You cannot annotate deletions, although deletions are saved as transactions that can be reversed by an administrator.  
  
-   If you change the **Code** value for a member, all previous transactions for the member will be unavailable. By returning the **Code** value to the original value, you can access the previous transactions.  
  
-   You can view transactions made to a member by other users. You can also view all transactions you’ve made to a member, even if you no longer have permission to specific attributes. You cannot view transactions involving attributes where your permission is set to deny.  
  
 You can view all transactions made to a member. For more information, see [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](../Topic/View%20All%20Annotations%20or%20Transactions%20for%20a%20Member%20\(MDS%20Add-in%20for%20Excel\).md).  
  
> [!IMPORTANT]  
>  If you enter an annotation of more than 500 characters, the annotation is automatically truncated.  
  
## Business Rule and Other Validation  
 When you publish data, validation is performed to ensure data is accurate before it’s added to the MDS repository. If the data does not meet specified criteria, it will not be published to the repository. For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](../Topic/Validating%20Data%20\(MDS%20Add-in%20for%20Excel\).md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Publish data from the active worksheet back to the MDS repository.|[Import Data from Excel to Master Data Services &#40;MDS Add-in for Excel&#41;](../Topic/Import%20Data%20from%20Excel%20to%20Master%20Data%20Services%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Delete a row from the MDS repository and from the worksheet at the same time.|[Delete a Row &#40;MDS Add-in for Excel&#41;](../Topic/Delete%20a%20Row%20\(MDS%20Add-in%20for%20Excel\).md)|  
|View annotations \(comments\) and transactions for rows of data \(members\) when you want to view updates to the data over time.|[View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](../Topic/View%20All%20Annotations%20or%20Transactions%20for%20a%20Member%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Combine data from two worksheets when you want to compare data before publishing.|[Combine Data &#40;MDS Add-in for Excel&#41;](../Topic/Combine%20Data%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Perform merge conflicts so that you can publish your changes.|[Merge Conflicts &#40;MDS Add-in for Excel&#41;](../Topic/Merge%20Conflicts%20\(MDS%20Add-in%20for%20Excel\).md)|  
  
## Related Content  
  
-   [Refreshing Data &#40;MDS Add-in for Excel&#41;](../Topic/Refreshing%20Data%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Master Data Services Add-in for Microsoft Excel](../../Topics\TopicNameNotContainA/Master-Data-Services-Add-in-for-Microsoft-Excel.md)  
  
  