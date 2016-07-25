---
title: "Select Rows That Do Not Match a Value (Visual Database Tools)"
ms.custom: na
ms.date: 07/21/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
caps.latest.revision: 3
manager: jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Select Rows That Do Not Match a Value (Visual Database Tools)
To find rows that do not match a value, use the NOT operator.  
  
### To find rows that do not match a value  
  
1.  If you have not done so already, add the columns or expressions that you want to use within your search condition to the [Criteria pane](../content/Criteria-Pane--Visual-Database-Tools-.md).  
  
2.  Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter the NOT operator followed by a search value.  
  
For example, to find all the rows in a `products` table where the values in the product code column begin with a character other than "A," you can enter a search condition such as the following:  
  
```  
NOT LIKE 'A%'  
```  
  
## See Also  
[Rules for Entering Search Values &#40;Visual Database Tools&#41;](../content/Rules-for-Entering-Search-Values--Visual-Database-Tools-.md)  
[Specify Search Criteria &#40;Visual Database Tools&#41;](../content/Specify-Search-Criteria--Visual-Database-Tools-.md)  
  
