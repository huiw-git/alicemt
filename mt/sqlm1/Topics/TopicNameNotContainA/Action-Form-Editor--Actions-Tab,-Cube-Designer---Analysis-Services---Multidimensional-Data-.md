---
title: Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c363a29b-6099-473c-9625-460cc15b3d95
---
# Action Form Editor (Actions Tab, Cube Designer) (Analysis Services - Multidimensional Data)
  Use the Action Form Editor pane on the **Actions** tab in Cube Designer to create and modify standard actions.  
  
## Options  
 **Name**  
 Type the name of the action.  
  
 **Action Target**  
 Expand to view the **Target type** and **Target object** options.  
  
 **Target type**  
 Select the type of object to which the action is to be associated. The server returns to the client only those actions that apply to the object of the specified type. The action is available to the client if the **Condition** is met and if the objects specified in the following table are selected.  
  
|Value|Selected Object|  
|-----------|---------------------|  
|Attribute members|A member is selected from a level based on the attribute in **Target object**.|  
|Cells|The named set in **Target object** is selected. Select **All cells** to select all of the cells in the cube.|  
|Cube|The cube in **Target object** is selected. Select CURRENTCUBE to use the current cube.<br /><br /> Note: Using CURRENTCUBE provides additional portability in cases where the cube may be renamed or the action copied to other cubes. It is recommended that you use CURRENTCUBE to represent the current cube.|  
|Dimension members|A member of the dimension in **Target object** is selected.|  
|Hierarchy|The hierarchy in **Target object** is selected.|  
|Hierarchy members|A member within the hierarchy in **Target object** is selected.|  
|Level|The level in **Target object** is selected.|  
|Level members|A member within the level in **Target object** is selected.|  
  
 **Target object**  
 Select the object to which the action is to be associated. The [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance returns to the client only those actions that apply to the selected object. The list of available objects is constrained by the choice of **Target type**.  
  
 **Condition \(Optional\)**  
 Enter the Multidimensional Expressions \(MDX\) expression that describes an optional condition, used in conjunction with **Target object**, which further restricts when the action is available. The expression must return a Boolean value that, if true, indicates the action is available.  
  
 Drag selected elements from the **Calculation Tools** pane to this option to include the MDX syntax for the selected element.  
  
 **Action Content**  
 Expand to view the **Type** and **Action expression** options.  
  
 **Type**  
 Select the type of action to take when the action is run. The following action types are available:  
  
|Value|Description|  
|-----------|-----------------|  
|Dataset|Returns a Multidimensional Expressions \(MDX\) statement, representing a multidimensional dataset, to be run and displayed by the client application.|  
|Proprietary|Returns a proprietary string that can be interpreted by client applications associated with the **Application** setting for this action.|  
|Rowset|Returns a Multidimensional Expressions \(MDX\) statement, representing a tabular rowset, to be run and displayed by the client application.|  
|Statement|Returns a command string to be run by the client application.|  
|URL|Returns a Uniform Resource Location \(URL\) string to be opened by the client application, typically with an Internet browser.|  
  
 For more information about action types, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Actions%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
 **Action expression**  
 Type the Multidimensional Expressions \(MDX\) expression that returns the string returned by the action to the client application for execution.  
  
 **Additional Properties**  
 Expand to view the **Invocation**, **Application**, **Description**, **Caption**, and **Caption Is MDX** options.  
  
 **Invocation**  
 Select the setting that indicates when the action should be carried out.  
  
> [!NOTE]  
>  This option only provides a recommendation to a client application as to when to execute an action, and does not directly control the invocation of the action.  
  
 The following table describes the available settings.  
  
|Value|Description|  
|-----------|-----------------|  
|Batch|The action should run as part of a batch operation or an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] task.|  
|Interactive|The action runs when the user invokes the action.|  
|On Open|The action runs when the cube is first opened.|  
  
 **Application**  
 Type the name of the application that can interpret the string returned by **Action expression**.  
  
 You can also use this option to identify which client application most commonly uses this action, as well as to display appropriate icons next to the action in a pop\-up menu.  
  
> [!NOTE]  
>  This option only provides a recommendation to a client application as to what client application should execute an action, and does not directly control access to the action. Client applications should hide any actions that are associated with other client applications.  
  
 **Description**  
 Type the optional description of the action.  
  
 **Caption**  
 Type the caption to be displayed for the action in the client application if **Caption Is MDX** is set to **False**.  
  
 Type the Multidimensional Expressions \(MDX\) expression that returns a string for the caption if **Caption Is MDX** is set to **True**.  
  
 **Caption is MDX**  
 Select **False** to indicate that **Caption** contains a literal string representing a caption to be displayed for the action in the client application.  
  
 Select **True** to indicate that **Caption** contains an MDX expression that returns a string representing a caption to be displayed for the action in the client application. The MDX expression must be resolved before the action is returned to the client application.  
  
## See Also  
 [Actions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Actions%20\(Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Toolbar &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Toolbar%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Action Organizer &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Action%20Organizer%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Calculation Tools &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Calculation%20Tools%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Drillthrough Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Drillthrough%20Action%20Form%20Editor%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Report Action Form Editor &#40;Actions Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Report%20Action%20Form%20Editor%20\(Actions%20Tab,%20Cube%20Designer\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)  
  
  