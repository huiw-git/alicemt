---
title: Create or Edit Relationship Dialog Box (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
---
# Create or Edit Relationship Dialog Box (Analysis Services - Multidimensional Data)
  Use the **Create\/Edit Relationship** dialog box in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to define or modify a relationship in a data source view. You can display the **Create\/Edit Relationship** dialog box by:  
  
-   Clicking **New Relationship** in the **Toolbar** pane of **Data Source View Designer**.  
  
-   Right\-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Relationship**.  
  
-   Right\-clicking a relationship in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Relationship**.  
  
> [!NOTE]  
>  You can create relationships in **Data Source View Designer** that do not exist in the underlying data source, and remove relationships created by **Data Source View Designer** from existing foreign key relationships in the underlying data source.  
  
## Options  
 **Source \(foreign key\) table**  
 Select the table or named query that contains the reference to one or more columns in the destination table.  
  
 **Destination \(primary key\) table**  
 Select the table that contains one or more columns referenced by the source table. For self\-joins, select the same table selected in **Source \(foreign key\) table**.  
  
 **Source columns**  
 Select the columns that reference columns in the destination table.  
  
 **Destination columns**  
 Select the columns that are referenced by columns in the source table.  
  
 **Reverse**  
 Click to reverse the direction of the relationship.  
  
 **Description**  
 Type an optional description for the relationship.  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)   
 [Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Data%20Source%20View%20Designer%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  