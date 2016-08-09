---
title: "Set a Minimum or Maximum on a Gauge (Report Builder and SSRS)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4c260c0-5a88-4f30-8977-eb5cc78fc146
caps.latest.revision: 9
caps.handback.revision: 0
manager: mblythe
---
# Set a Minimum or Maximum on a Gauge (Report Builder and SSRS)
Unlike the chart, where multiple groups are defined, the gauge only shows one value. Since Report Builder and Report Designer determine the context or relative significance of the one value that you are trying to show on the gauge, you must define the minimum and maximum of the scale. For example, if your data values are rankings between 0 and 10, you will want to set the minimum to 0 and maximum to 10. The interval numbers are calculated automatically based on the values specified for the minimum and maximum. By default, the minimum and maximum are set to 0 and 100, but this is an arbitrary value that you should change. The application does not calculate your value as a percentage.  
  
 If the range of your values is large, for example from 0 to 10000, consider using a multiplier to reduce the number of zeroes on the gauge. The multiplier will only reduce the scale of the numbers on the gauge, not the value itself.  
  
 You can use expressions to set the values of the **Minimum** and **Maximum** options. For more information, see [Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
### To set the minimum and maximum on the gauge  
  
1.  Right-click on the scale and select **Scale Properties**. The **Scale Properties** dialog box appears.  
  
2.  In **General**, specify a value for **Minimum**. By default, this value is 0. Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.  
  
3.  Specify a value for **Maximum**. By default, this value is 100. Optionally, click the **Expression** (*fx*) button to edit the expression that sets the value of the option.  
  
4.  (Optional) If the values for your minimum and maximum are large, specify a value for the **Multiply scale labels by** option. To specify a multiplier that reduces your scale, use a decimal number. For example, if you have a scale from 0 to 1000, you can specify a multiplier value of 0.01 to reduce the scale to read 0 to 10.  
  
## See Also  
 [Formatting Scales on a Gauge (Report Builder and SSRS)](../../Topics/TopicNameContainA/Formatting-Scales-on-a-Gauge--Report-Builder-and-SSRS-.md)   
 [Formatting Pointers on a Gauge (Report Builder and SSRS)](../../Topics/TopicNameContainA/Formatting-Pointers-on-a-Gauge--Report-Builder-and-SSRS-.md)   
 [Gauges (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Gauges--Report-Builder-and-SSRS-.md)