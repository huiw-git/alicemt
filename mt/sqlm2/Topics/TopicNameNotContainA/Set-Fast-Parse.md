---
title: Set Fast Parse
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
---
# Set Fast Parse
  The fast parse property must be set for each column of the source or transformation that uses fast parse. To set the property, use the Advanced editor of the Flat File source and Data Conversion transformation.  
  
### To set fast parse  
  
1.  Right\-click the Flat File source or Data Conversion transformation, and then click **Show Advanced Editor**.  
  
2.  In the **Advanced Editor** dialog box, click the **Input and Output Properties** tab.  
  
3.  In the **Inputs and Outputs** pane, click the column for which you want to enable fast parse.  
  
4.  In the Properties window, expand the **Custom Properties** node, and then set the **FastParse** property to **True**.  
  
5.  Click **OK**.  
  
  