---
title: Select Tables and Views (Data Source View Wizard) (Analysis Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
---
# Select Tables and Views (Data Source View Wizard) (Analysis Services)
  Use the **Select Tables and Views** page to select the tables or views from the data source that you want to include in the data source view.  
  
## Options  
 **Available objects**  
 Lists the tables and views in the data source schema. The schema name prefixes the name of every object if more than one schema is listed. If only one schema is listed, the schema's name does not prefix the object names.  
  
 To reorder the list in ascending or descending order, click either **Name** or **Type**.  
  
 **Included objects**  
 Lists the tables and views to include in the data source view.  
  
 To reorder the list in ascending or descending order, click either **Name** or **Type**.  
  
 **Filter**  
 Filters the objects listed under **Available objects**. Type a string, and then click **Filter** to list only the names that contain a specified string. To find an exact string of characters, enclose the string between double quotation marks. The filter is not case sensitive.  
  
 You can include the wildcard characters listed in the following table anywhere in the filter string.  
  
|Wildcard character|Value|  
|------------------------|-----------|  
|**\***|Any string of characters|  
|**%**|Any string of characters|  
|**?**|A single character|  
|**"** *string* **"**|A literal string of characters. This wildcard character will match any substring within the object name.|  
  
 **Show system objects**  
 Displays system objects under **Available objects**. This option is available only if the data source provider exposes system objects. Removing a system object from the **Included objects** list automatically selects this option.  
  
 **Add related tables**  
 Adds all the tables that are related to those listed under **Included objects**. This option does not add views. However, this option does add partitioned tables. If you select name\-matching criteria on the **Name Matching** page of the wizard, this option also includes logically related tables according to the criteria you select. Tables are also included if they are related to the newly added related tables, and if they have an identical structure to the original table.  
  
## See Also  
 [Data Source View Wizard F1 Help &#40;Analysis Services&#41;](../Topic/Data%20Source%20View%20Wizard%20F1%20Help%20\(Analysis%20Services\).md)   
 [Data Source Views in Multidimensional Models](../../Topics\TopicNameNotContainA/Data-Source-Views-in-Multidimensional-Models.md)  
  
  