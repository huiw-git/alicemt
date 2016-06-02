---
title: String Padding (SSIS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
---
# String Padding (SSIS)
  The expression evaluator does not check if a string contains leading and trailing spaces, and it does not pad strings to make them the same length before it compares them. If expressions requires string padding, you can use the \+ operator to concatenate column values and blank strings. For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](../Topic/+%20\(Concatenate\)%20\(SSIS%20Expression\).md).  
  
 On the other hand, if you want to remove spaces, the expression evaluator provides the LTRIM, RTRIM, and TRIM functions, which remove leading or trailing spaces, or both. For more information, see [LTRIM &#40;SSIS Expression&#41;](../Topic/LTRIM%20\(SSIS%20Expression\).md), [RTRIM &#40;SSIS Expression&#41;](../Topic/RTRIM%20\(SSIS%20Expression\).md), and [TRIM &#40;SSIS Expression&#41;](../Topic/TRIM%20\(SSIS%20Expression\).md).  
  
> [!NOTE]  
>  The LEN function includes leading and trailing blanks in its count.  
  
## Related Content  
 Technical article, [SSIS Expression Cheat Sheet](http://go.microsoft.com/fwlink/?LinkId=746575), on pragmaticworks.com  
  
  