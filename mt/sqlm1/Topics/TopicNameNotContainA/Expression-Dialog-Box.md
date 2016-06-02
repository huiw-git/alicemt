---
title: Expression Dialog Box
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6c74ccb-4594-4d4f-b958-618d710e34eb
---
# Expression Dialog Box
  Use the **Expression** dialog box to write [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] simple and complex expressions for report item properties. You can use expressions to set many properties, including color, font, and borders. At run time, the report processor evaluates expressions and substitutes the result for the value of the property.  
  
 To open the **Expression** dialog box, click the Expression \(**fx**\) button in dialog boxes, or select **Expression** from the shortcut menu or drop\-down lists in the Properties pane.  
  
 The **Expression** dialog box includes a code window, category tree, category items, description pane, and example pane. The **Expression** dialog box is context\-sensitive; the category items and descriptions change according to the expression category that you are working with. It supports IntelliSense, statement completions, function call examples, and syntax coloring to help you detect syntax errors.  
  
## Expression Constructs  
 Expressions begin with an equal sign \(\=\) and can include constants, literals, operators, and references to built\-in fields, built\-in collections, built\-in functions, [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] run\-time library functions, [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] common language runtime classes, and custom functions. The following list describes the categories and values you can add to an expression.  
  
 **Set expression for:**  *\<PropertyName\>*  
 The name of the property that you are defining an expression for. You can also set this property, by name, in the Properties pane.  
  
 **Constants**  
 Provides a list of predefined values valid for this property for properties that are based on constants. For example, a property based on color shows valid color names. For a property that is a Boolean data type, values are **True** and **False**.  
  
 Not all items that support expressions can be set to a constant. If a property cannot be set to constant value, the description pane provides this information.  
  
 **Built\-in Fields**  
 Provides a list of the items in the global collection that you can use in an expression. Some collections are only supported after the report is published to the server. For more information, see [Built-in Globals and Users References &#40;Report Builder and SSRS&#41;](../Topic/Built-in%20Globals%20and%20Users%20References%20\(Report%20Builder%20and%20SSRS\).md).  
  
 **Parameters**  
 Provides a list of report parameters.  
  
 **Fields\(** *\<selected Dataset\>* **\)**  
 Displays the list of fields for the dataset selected in the Datasets category. Double\-click a field to copy the field to the **Expression** box.  
  
 **Datasets**  
 Provides a list of available datasets and shows the fields that are members of the dataset.  
  
 **Variables**  
 Displays a list of report variables. For more information, see [Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](../Topic/Report%20and%20Group%20Variables%20Collections%20References%20\(Report%20Builder%20and%20SSRS\).md).  
  
 **Operators**  
 Displays the operators you can include in a calculation or string manipulation. For more information, see [Operators in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Operators%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md).  
  
 **Common Functions**  
 Displays common functions, grouped by type. When you select a function in the Item pane, a description and example appear.  
  
 Common functions include built\-in report and aggregate functions, [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] run\-time library functions, and [!INCLUDE[dnprdnshort](../../Token\Other/dnprdnshort_md.md)] common language runtime classes \(CLR\) in the [Math](assetId:///T:System.Math) and [Convert](assetId:///T:System.Convert) namespace. You can also add references to CLR classes and external assemblies that do not appear in the category list. For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../Topic/Custom%20Code%20and%20Assembly%20References%20in%20Expressions%20in%20Report%20Designer%20\(SSRS\).md).  
  
## Options  
 Code window  
 Use the code window in the top pane to type an expression. When you open the **Expression** dialog box, the code window contains the expression. You can replace or revise the expression. You can add function calls, operators, constants, fields, parameters, items from the global collections, and references to custom code. The code window displays your changes as you make them.  
  
 A wavy red underline indicates a syntax error. Hover over the underlined text to see the error message.  
  
 When you type in global collection terms followed by a punctuation separator, you will see a drop\-down list of available members or properties. From the drop\-down list, you can type the first few characters followed by a tab to automatically fill the selection.  
  
 When you type in a function name followed by a left parenthesis, you will see a tooltip that provides information about the parameters and function return values.  
  
 **Category**  
 Displays categories of expressions. Choosing a category establishes a context for creating an expression and changes the list of valid values in the Item pane. For example, for an expression for a text box value, expand Common functions and select Aggregate functions to display **Avg**, **Count**, and other functions in the **Item** pane.  
  
 **Item**  
 Displays the list of valid values for the selected category. Double\-click on an item to add the expression text for this item at the insertion point in the code window.  
  
 **Values**  
 Depending on the category and item you select, the third pane contains a description, a sample expression, or a list of valid values. Drag the edge of the dialog box to widen the sample area.  
  
## See Also  
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Numbers%20and%20Dates%20\(Report%20Builder%20and%20SSRS\).md)   
 [Parameters Collection References &#40;Report Builder and SSRS&#41;](../Topic/Parameters%20Collection%20References%20\(Report%20Builder%20and%20SSRS\).md)   
 [Group Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Group%20Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Filter Equation Examples &#40;Report Builder and SSRS&#41;](../Topic/Filter%20Equation%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Types in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Data%20Types%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Built-in%20Collections%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add an Expression &#40;Report Builder and SSRS&#41;](../Topic/Add%20an%20Expression%20\(Report%20Builder%20and%20SSRS\).md)  
  
  