---
title: Unary Operators in Parent-Child Dimensions
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8ef549c-5458-458a-bf1a-fd743a1417fd
---
# Unary Operators in Parent-Child Dimensions
  In a dimension that contains a parent\-child relationship in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], you specify a unary \(or custom rollup\) operator column that determines the custom rollup for all noncalculated members of the parent attribute. The unary operator is applied to members whenever the values of the parent members are evaluated. The **UnaryOperatorColumn** on a parent attribute \(**Usage**\=Parent\) specifies the column of a table in the data source view that contains unary operators. Values for the custom rollup operators that are stored in this column are applied to each member of the attribute.  
  
 You can create and specify a named calculation on a dimension table in the data source view as a unary operator column. The simplest expression, such as '\+', returns the same operator for all members. But you can use any expression as long as it returns an operator for every member.  
  
 You can change the **UnaryOperatorColumn** property setting manually on a parent attribute or use the Define Custom Aggregation enhancement of the Business Intelligence Wizard to replace the default aggregation that is associated with members of a dimension. For more information about how to use the Business Intelligence Wizard to perform this configuration, see [Add a Custom Aggregation to a Dimension](../../Topics\TopicNameContainA/Add-a-Custom-Aggregation-to-a-Dimension.md).  
  
 The default setting for the **UnaryOperatorColumn** property on a parent attribute is \(none\), which disables the custom rollup operators. The following table lists the unary operators and describes how they behave when they are applied to a level.  
  
|Unary operator|Description|  
|--------------------|-----------------|  
|\+ \(plus sign\)|The value of the member is added to the aggregate value of the sibling members that occur before the member. This operator is the default operator if no unary operator column is defined for an attribute.|  
|– \(minus sign\)|The value of the member is subtracted from the aggregate value of the sibling members that occur before the member.|  
|\* \(asterisk\)|The value of the member is multiplied by the aggregate value of the sibling members that occur before the member.|  
|\/ \(slash mark\)|The value of the member is divided by the aggregate value of the sibling members that occur before the member.|  
|~ \(tilde\)|The value of the member is ignored.|  
  
 Blank values and any other values not found in the table are treated the same as the plus sign \(\+\) unary operator. There is no operator precedence, so the order of members as stored in the unary operator column determines the order of evaluation. To change the order of evaluation, create a new attribute, set its **Type** property to **Sequence**, and then assign sequence numbers that correspond to the order of evaluation in its **Source Column** property. You must also order members of the attribute by that attribute. For information about how to use the Business Intelligence Wizard to order members of an attribute, see [Define the Ordering for a Dimension](../../Topics\TopicNameContainA/Define-the-Ordering-for-a-Dimension.md).  
  
 You can use the **UnaryOperatorColumn** property to specify a named calculation that returns a unary operator as a literal character for all members of the attribute. This could be as simple as typing a literal character such as `'*'` in the named calculation. This would replace the default operator, the plus sign \(\+\), with the multiplication operator, the asterisk \(\*\), for all members of the attribute. For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](../Topic/Define%20Named%20Calculations%20in%20a%20Data%20Source%20View%20\(Analysis%20Services\).md).  
  
 In the **Browser** tab of Dimension Designer, you can view the unary operators next to each member in a hierarchy. You can also change the unary operators when you work with a write\-enabled dimension. If the dimension is not write\-enabled, you must use a tool to modify the data source directly.  
  
## See Also  
 [Dimension Attribute Properties Reference](../../Topics\TopicNameNotContainA/Dimension-Attribute-Properties-Reference.md)   
 [Custom Rollup Operators in Parent-Child Dimensions](../../Topics\TopicNameNotContainA/Custom-Rollup-Operators-in-Parent-Child-Dimensions.md)   
 [Start the Business Intelligence Wizard in Dimension Designer](../../Topics\TopicNameNotContainA/Start-the-Business-Intelligence-Wizard-in-Dimension-Designer.md)  
  
  