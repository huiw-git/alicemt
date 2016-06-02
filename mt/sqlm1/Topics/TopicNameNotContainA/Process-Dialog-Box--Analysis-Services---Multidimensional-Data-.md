---
title: Process Dialog Box (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
---
# Process Dialog Box (Analysis Services - Multidimensional Data)
  Use the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] and [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to process [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects. You can display the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] by:  
  
-   Right\-clicking an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project, cube, dimension, or mining structure in **Solution Explorer** and selecting **Process**.  
  
-   Selecting **Process** from the toolbar on every page of **Cube Designer**, every page of **Dimension Designer**, or the **Mining Structure** and **Mining Models** pages of **Data Mining Model Designer**.  
  
-   Right\-clicking a mining model in the **Mining Models** page of **Data Mining Model Designer** and selecting **Process Mining Structure and All Models** or **Process Model**.  
  
 You can display the **Process** dialog box in **SQL Server Management Studio** by:  
  
-   Right\-clicking an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, cube, measure group, partition, dimension, mining structure, or mining model in **Object Explorer** and selecting **Process**.  
  
## Options  
 **Object list**  
 Select the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects to be processed and the processing options and settings to be applied. The grid contains the following columns:  
  
 **Object Name**  
 Displays the name of the object to be processed. The icon to the left of the name indicates the object type.  
  
 **Type**  
 Displays the type of the object to be processed.  
  
 **Process Options**  
 Select the type of processing to perform on the selected object. For more information about available processing options, see [Processing a multidimensional model &#40;Analysis Services&#41;](../Topic/Processing%20a%20multidimensional%20model%20\(Analysis%20Services\).md).  
  
 **Settings**  
 Displays the **Configure** hyperlink when you choose **Process Incremental** in **Process Options** for cubes, measure groups, or partitions. Click **Configure** to launch the **Incremental Update** dialog box. For more information about the **Incremental Update** dialog box, see [Incremental Update Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Incremental%20Update%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
 **Remove**  
 Click to remove the selected items from **Object list**.  
  
 **Impact Analysis**  
 Click to open the **Impact Analysis** dialog box and display the objects that will be affected by the processing task. For more information about the **Impact Analysis** dialog box, see [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Impact%20Analysis%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
> [!NOTE]  
>  This option is disabled when the **Process affected objects** option is selected in the **Change Settings** dialog box.  
  
 **Change Settings**  
 Click to open the **Change Settings** dialog box and change the settings that govern processing of the selected objects, including batch processing settings, writeback settings, and dimension key error settings. For more information about the **Change Settings** dialog box, see [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Change%20Settings%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
 **Run**  
 Click to process the objects.  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)   
 [Process Progress Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Process%20Progress%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  