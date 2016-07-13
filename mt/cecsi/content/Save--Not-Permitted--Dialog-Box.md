---
title: Save (Not Permitted) Dialog Box
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Save (Not Permitted) Dialog Box
The **Save** (Not Permitted) dialog box warns you that saving changes is not permitted because the changes you have made require the listed tables to be dropped and re\-created.  
  
The following actions might require a table to be re\-created:  
  
-   Adding a new column to the middle of the table  
  
-   Dropping a column  
  
-   Changing column nullability  
  
-   Changing the order of the columns  
  
-   Changing the data type of a column  
  
To change this option, on the **Tools** menu, click **Options**, expand **Designers**, and then click **Table and Database Designers**. Select or clear the **Prevent saving changes that require the table to be re\-created** check box.  
  
