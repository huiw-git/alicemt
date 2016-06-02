---
title: Table Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
---
# Table Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)
  Use the **Table Binding** option in the **Partition Source** dialog box to specify the fact table that provides the data for the partition. You can display this pane by selecting **Table Binding** from the **Binding type** option in the **Partition Source** dialog box.  
  
## Options  
 **Measure group**  
 Displays the measure group for this partition.  
  
 **Look in**  
 Select the data source or data source view that contains the source tables for this partition. The data source view used by the selected measure group is selected by default.  
  
 **Filter tables**  
 Type the string used to restrict, by table name, the tables displayed in **Available tables**.  
  
 **Find tables**  
 Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.  
  
 **Available tables**  
 Click to select the table to use as a source table for the partition.  
  
 If no filter is specified in **Filter tables**, all tables in the data source or data source view specified in **Look in** that are similar in structure to the fact table used by the measure group specified in **Measure group** are listed.  
  
 If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the above criteria. Only those tables that contain the string specified in **Filter tables** are displayed.  
  
## See Also  
 [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Partition%20Source%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  