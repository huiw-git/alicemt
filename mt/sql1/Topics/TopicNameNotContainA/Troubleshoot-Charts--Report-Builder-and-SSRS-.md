---
title: "Troubleshoot Charts (Report Builder and SSRS)"
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
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 8
caps.handback.revision: 0
manager: mblythe
---
# Troubleshoot Charts (Report Builder and SSRS)
These issues can be helpful when working with charts.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
## Why does my chart count, not sum, the values on the value axis?  
 Most chart types require numeric values along the value axis, which is typically the y-axis, in order to draw correctly. If the data type of your value field is **String**, the chart cannot display a numeric value, even if there are numerals in the fields. Instead, the chart displays a count of the total number of rows that contain a value in that field. To avoid this behavior, make sure that the fields that you use for value series have numeric data types, as opposed to strings that contain formatted numbers.  
  
## See Also  
 [Charts (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Charts--Report-Builder-and-SSRS-.md)