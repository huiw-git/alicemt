---
title: "Annotate a Transaction (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Annotate a Transaction (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], annotate a transaction when you want to provide supporting details about the transaction for historical purposes.  
  
> [!NOTE]  
>  You cannot delete annotations.  
  
## Prerequisites  
  
-   To annotate transactions that you created, you must have permission to access the **Explorer** functional area, and have a minimum of **Update** permission to the model object you want to annotate.  
  
-   To annotate transactions for all users, you must have permission to access the **Version Management** functional area and be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To annotate a transaction in Explorer  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] home page, from the **Model** list, select a model.  
  
2.  From the **Version** list, select a version.  
  
3.  Click **Explorer**.  
  
4.  From the menu bar, point to **Entities** and click the entity that contains the member with a transaction you want to annotate.  
  
5.  In the grid, click the row of the member.  
  
6.  Click **View Transactions**.  
  
7.  In the **View Transactions** dialog box, click the transaction you want to annotate.  
  
8.  In the box at the bottom of the dialog box, type your annotation.  
  
9. Click **Add Annotation**. The annotation is displayed in the **Annotations** pane.  
  
### To annotate a transaction in Version Management (administrators only)  
  
1.  On the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] home page, click **Version Management**.  
  
2.  On the menu bar, click **Transactions**.  
  
3.  In the **Transactions** pane, click the row in the grid for the transaction you want to annotate.  
  
4.  In the **Transaction Annotations** pane, in the **Annotation** box, type your annotation.  
  
5.  Click **OK**.  
  
## See Also  
 [Annotations (Master Data Services)](../../Topics/TopicNameNotContainA/Annotations--Master-Data-Services-.md)   
 [Transactions (Master Data Services)](../../Topics/TopicNameNotContainA/Transactions--Master-Data-Services-.md)