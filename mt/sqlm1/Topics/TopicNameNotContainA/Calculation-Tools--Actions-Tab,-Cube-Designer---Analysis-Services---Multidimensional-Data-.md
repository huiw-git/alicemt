---
title: Calculation Tools (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
---
# Calculation Tools (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)
  Use the **Calculation Tools** pane on the **Actions** tab in Cube Designer to explore metadata, functions, and templates available for use in actions, drillthrough actions, and report actions.  
  
## Options  
 **Metadata**  
 Displays the metadata for the selected cube.  
  
 Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the Multidimensional Expressions \(MDX\) syntax for that element at the selected location in the pane.  
  
 **Functions**  
 Displays the functions available for expressions and conditions.  
  
 Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.  
  
> [!NOTE]  
>  In project mode, the **Calculation Tools** dialog box reads information for this option from an XML file named MDXFunctions.xml, included with [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. In online mode, information for this option is retrieved from the MDSCHEMA\_FUNCTIONS schema rowset for the instance.  
  
 **Templates**  
 Displays the predefined templates available for actions.  
  
 Drag a selected element to the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor** pane to include the MDX syntax for that element at the selected location in the pane.  
  
## Context Menu  
 The following options are available in the context menu displayed by right\-clicking an element in the **Calculation Tools** pane:  
  
|Option|Definition|  
|------------|----------------|  
|**Copy**|Select to copy the selected element in **Metadata** or **Functions** to the Clipboard.<br /><br /> This option is not displayed if **Templates** is selected.<br /><br /> This option is disabled if the selected member cannot be copied, such as the **Sets** folder of a dimension displayed in **Metadata** or the function group folder for a function displayed in **Functions**.|  
|**Filter Members**|Select to display the **Filter Members** dialog box and filter members displayed for the selected element in **Metadata**. For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Filter%20Members%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).<br /><br /> This option is displayed only if **Metadata** is selected.<br /><br /> This option is enabled only if a level for an attribute is selected in **Metadata**.|  
|**Add Template**|Select to add a new action, drillthrough action, or report action based on the selected template to the cube and display, respectively, the **Action Form Editor**, **Drillthrough Action Form Editor**, or **Report Action Form Editor**.<br /><br /> This option is displayed only if **Metadata** is selected.|  
  
## See Also  
 [MDX Scripting Fundamentals &#40;Analysis Services&#41;](../Topic/MDX%20Scripting%20Fundamentals%20\(Analysis%20Services\).md)   
 [Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Actions%20\(Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Toolbar%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Action%20Organizer%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Action%20Form%20Editor%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Drillthrough%20Action%20Form%20Editor%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Report%20Action%20Form%20Editor%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  