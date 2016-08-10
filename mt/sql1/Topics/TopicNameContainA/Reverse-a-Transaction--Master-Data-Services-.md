---
title: "Reverse a Transaction (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
caps.latest.revision: 9
caps.handback.revision: 0
manager: jhubbard
---
# Reverse a Transaction (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], administrators can reverse a transaction when an action needs to be undone. Examples of transactions are attribute value changes, hierarchy moves, or member deletions.  
  
## Prerequisites  
  
-   You must have permission to access the **Version Management** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To reverse a transaction  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] home page, click **Version Management**.  
  
2.  On the menu bar, click **Transactions**.  
  
3.  On the **Transactions** page, from the **Model** list, select a model.  
  
4.  From the **Version** list, select a version.  
  
5.  Click the row in the grid for the transaction you want to reverse.  
  
6.  Click **Reverse Transaction**.  
  
7.  In the confirmation dialog box, click **OK**. Another transaction is added to the grid to record the reversed transaction.  
  
## See Also  
 [Transactions (Master Data Services)](../../Topics/TopicNameNotContainA/Transactions--Master-Data-Services-.md)   
 [Reactivate a Member or Collection (Master Data Services)](../../Topics/TopicNameContainA/Reactivate-a-Member-or-Collection--Master-Data-Services-.md)