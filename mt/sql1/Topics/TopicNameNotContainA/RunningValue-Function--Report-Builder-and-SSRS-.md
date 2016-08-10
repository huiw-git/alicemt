---
title: "RunningValue Function (Report Builder and SSRS)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
caps.latest.revision: 9
caps.handback.revision: 0
manager: mblythe
---
# RunningValue Function (Report Builder and SSRS)
Returns a running aggregate of all non-null numeric values specified by the expression, evaluated for the given scope.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
## Syntax  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### Parameters  
 *expression*  
 The expression on which to perform the aggregation, for example, `[Quantity]`.  
  
 *function*  
 (**Enum**) The name of the aggregate function to apply to the expression, for example, **Sum**. This function cannot be **RunningValue**, **RowNumber**, or **Aggregate**.  
  
 *scope*  
 (**String**) A string constant that is the name of a dataset, data region, or group, or null (**Nothing** in [!INCLUDE[vbprvb](../../Topics/TopicNameContainA/tokens/vbprvb_md.md)]), that specifies the context in which to evaluate the aggregation. **Nothing** specifies the outermost context, usually the report dataset.  
  
## Return Type  
 Determined by the aggregate function that is specified in the *function* parameter.  
  
## Remarks  
 The value for **RunningValue** resets to 0 for each new instance of the scope. If a group is specified, the running value is reset when the group expression changes. If a data region is specified, the running value is reset for each new instance of the data region. If a dataset is specified, the running value is not reset throughout the entire dataset.  
  
 **RunningValue** cannot be used in a filter or sort expression.  
  
 The set of data for which the running value is calculated must have the same data type. To convert data that has multiple numeric data types to the same data type, use conversion functions like **CInt**, **CDbl** or **CDec**. For more information, see [Type Conversion Functions](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 *Scope* cannot be an expression.  
  
 *Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:  
  
-   Scope for nested aggregates must be the same as, or contained by, the scope of the outer aggregate. For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.  
  
-   Scope for nested aggregates cannot be the name of a dataset.  
  
-   *Expression* must not contain **First**, **Last**, **Previous**, or **RunningValue** functions.  
  
-   *Expression* must not contain nested aggregates that specify *recursive*.  
  
 To calculate the running value of the number of rows, use **RowNumber**. For more information, see [RowNumber Function (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/RowNumber-Function--Report-Builder-and-SSRS-.md).  
  
 For more information, see [Aggregate Functions Reference (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Aggregate-Functions-Reference--Report-Builder-and-SSRS-.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Scope-for-Totals--Aggregates--and-Built-in-Collections--Report-Builder-and-SSRS-.md).  
  
 For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Creating-Recursive-Hierarchy-Groups--Report-Builder-and-SSRS-.md).  
  
## Examples  
 The following code example provides a running sum of the field named `Cost` in the outermost scope, which is the dataset.  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 The following code example provides a running sum of the field named `Score` in the dataset named `DataSet1`.  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 The following code example provides a running sum of the field named `Traffic Charges` in the outermost scope.  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## See Also  
 [Expression Uses in Reports (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Uses-in-Reports--Report-Builder-and-SSRS-.md)   
 [Expression Examples (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Examples--Report-Builder-and-SSRS-.md)   
 [Data Types in Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Data-Types-in-Expressions--Report-Builder-and-SSRS-.md)   
 [Expression Scope for Totals, Aggregates, and Built-in Collections (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Scope-for-Totals--Aggregates--and-Built-in-Collections--Report-Builder-and-SSRS-.md)