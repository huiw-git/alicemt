---
title: "Select Creation Method (Dimension Wizard)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 291b0b2d-a03a-4df6-82f7-90ad92d4d1cf
caps.latest.revision: 30
caps.handback.revision: 0
manager: mblythe
---
# Select Creation Method (Dimension Wizard)
Use the **Select Creation Method** page to select how to create the dimension.  
  
 **To open the Dimension Wizard**  
  
-   In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] project, and then click **New Dimension**.  
  
## Options  
 **Use an existing table**  
 Create a dimension from one or more tables in a data source. The attributes that are available for the dimension will depend on the structure of the data in the table.  
  
 For more information, see [Create a Dimension by Using an Existing Table](../../Topics/TopicNameContainA/Create-a-Dimension-by-Using-an-Existing-Table.md).  
  
 **Generate a time table in the data source**  
 Create a time table in the underlying data source and then use that table to create a time dimension. Use this option when no such table exists and you do not want to use a script to create one. The new time table will contain data for the date range, attributes, and calendars that you specify in the wizard.  
  
> [!NOTE]  
>  To use this option, you must have permission to create objects in the underlying data source. If you do not have permission to create objects on the data source, try to use the **Generate a time table on the server** option instead.  
  
 For more information, see [Create a Time Dimension by Generating a Time Table](../../Topics/TopicNameContainA/Create-a-Time-Dimension-by-Generating-a-Time-Table.md).  
  
 **Generate a time table on the server**  
 Create a time table directly on the server and then use that table to create a time dimension. Use this option if you do not have permission to create objects in the underlying data source. The new time dimension will contain data for the date range, attributes, and calendars that you specify in the wizard.  
  
 For more information, see [Create a Time Dimension by Generating a Time Table](../../Topics/TopicNameContainA/Create-a-Time-Dimension-by-Generating-a-Time-Table.md).  
  
 **Generate a non-time table in the data source**  
 Design the dimension without an underlying relational data source, and then generate the necessary schema for the data source. This approach is known as top-down modeling.  
  
> [!NOTE]  
>  To use this option, you must have permission to create objects in the underlying data source.  
  
 You can build the dimension with or without a template. To build the dimension with a template, select the template from the **Template** list.  
  
 For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](../../Topics/TopicNameContainA/Create-a-Dimension-by-Generating-a-Non-Time-Table-in-the-Data-Source.md).  
  
 **Template**  
 Select the template that you want to use to create the dimension. Templates provide a complete set of attribute and hierarchy definitions oriented towards a specific business purpose.  
  
> [!NOTE]  
>  This option is only available when the **Generate a non-time table in the data source** option has been selected.  
  
## See Also  
 [Dimension Wizard F1 Help](../../Topics/TopicNameNotContainA/Dimension-Wizard-F1-Help.md)   
 [Dimensions (SSAS)](assetId:///2b114135-2572-4479-8c81-3ccf0cfeb9f7)   
 [Dimensions in Multidimensional Models](../../Topics/TopicNameNotContainA/Dimensions-in-Multidimensional-Models.md)