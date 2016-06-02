---
title: Object Binding Dialog Box
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
---
# Object Binding Dialog Box
  Use the **Object Binding** dialog box in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to define bindings between the property of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object and a table or column in a data source view. You can display the **Object Binding** dialog box by selecting **\(new\)** from the drop\-down list for the value of the following properties of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]:  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## Options  
 **Binding type**  
 Select the binding to use for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object. The following types of binding can be used:  
  
 Column binding  
 Binds the object to an existing table and column within a data source view.  
  
 Generate column  
 Indicates that a new column is to be defined in the data source view, and a column binding is then associated with it.  
  
> [!NOTE]  
>  If this option is selected, you must run the **Schema Generation Wizard** before deploying the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object.  
  
 Row binding  
 Binds the object to a row in a fact table and is used to facilitate count measures based on the number of rows processed in the fact table.  
  
 **Source table**  
 Displays a list of tables in the data source view associated with the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object.  
  
 **Source column**  
 Displays a list of columns in the table selected in **Source table**.  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)  
  
  