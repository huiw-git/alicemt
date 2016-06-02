---
title: Group Expression Examples (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
---
# Group Expression Examples (Report Builder and SSRS)
  In a data region, you can group data by a single field, or create more complex expressions that identify the data on which to group. Complex expressions include references to multiple fields or parameters, conditional statements, or custom code. When you define a group for a data region, you add these expressions to the **Group** properties. For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20or%20Delete%20a%20Group%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
 To merge two or more groups that are based on simple field expressions, add each field to the group expressions list in the group definition.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Examples of Group Expressions  
 The following table provides examples of group expressions that you can use to define a group.  
  
|Description|Expression|  
|-----------------|----------------|  
|Group by the `Region` field.|`=Fields!Region.Value`|  
|Group by last name and first name.|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|Group by the first letter of the last name.|`=Fields!LastName.Value.Substring(0,1)`|  
|Group by parameter, based on user selection.<br /><br /> In this example, the parameter `GroupBy` must be based on an available values list that provides a valid choice to group on.|`=Fields(Parameters!GroupBy.Value).Value`|  
|Group by three separate age ranges:<br /><br /> "Under 21", "Between 21 and 50", and "Over 50".|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|Group by many age ranges. This example shows custom code, written in [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] .NET, that returns a string for the following ranges:<br /><br /> 25 or Under<br /><br /> 26 to 50<br /><br /> 51 to 75<br /><br /> Over 75|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> Custom code:<br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## See Also  
 [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../Topic/Filter,%20Group,%20and%20Sort%20Data%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../Topic/Custom%20Code%20and%20Assembly%20References%20in%20Expressions%20in%20Report%20Designer%20\(SSRS\).md)  
  
  