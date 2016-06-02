---
title: Set and Configure Measurement Units (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a15a96c3-7d2c-433e-a440-4ea051e967a9
---
# Set and Configure Measurement Units (Report Builder and SSRS)
  In a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report, indicators use one of two measurement units: percentage or numeric.   
    
  By default, indicators are configured to use percentages as the measurement unit. This means that the indicator values assigned to each icon in the indicator set are determined by a percentage range. The percentage ranges are evenly divided across the icons in the indicator set. Each icon represents an indicator state. You can change the percentages for each icon in the indicator set by specifying different start and end percentages. Indicators also automatically detect the minimum and maximum values in the data.  
  
 You can change the measurement unit to be a numeric value. In this case, you do not specify minimum or maximum for the data; instead, you provide only the start and end values for each icon that the indicator uses.  
  
 Options such as measurement units can be set by using expressions. For more information, see [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md).  
  
## To use the numeric state measurement unit  
  
1.  Right\-click the indicator you want to change and click **Indicator Properties**.  
  
2.  Click **Values and States** in the left pane.  
  
3.  In the **States Measurement Unit** list, click **Numeric**.  
  
     Optionally, click the **Expression** \(*fx*\) button to edit an expression that sets the value of the option.  
  
4.  For each icon in the indicator set, update the values in the **Start** and **End** text boxes.  
  
     Optionally, click the **Expression** \(*fx*\) button to edit an expression that sets the values of the **Start** and **End** options.  
  
    > [!NOTE]  
    >  The values in the **Start** and **End** text boxes must be numeric.  
  
5.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## To use the percentage measurement unit  
  
1.  Right\-click the indicator you want to change and click **Indicator Properties**.  
  
2.  Click **Values and States** in the left pane.  
  
3.  In the **States Measurement Unit** list, click **Percentage**.  
  
     Optionally, click the **Expression** \(*fx*\) button to edit an expression that sets the value of the option.  
  
4.  Optionally, change the **Minimum** and **Maximum** options to use specific values instead of automatically detecting the minimum and maximum values of the data that the indicator uses. The value of **Minimum** must be smaller than the value of **Maximum**.  
  
    > [!NOTE]  
    >  If you explicitly set minimum and maximum values, that value range is used by the indicator regardless of the actual the minimum and maximum values in the data. This means that values lower than the minimum and higher than the maximum are excluded from the evaluation that determine what indictor icon to show in the report.  
  
     Optionally, click the **Expression** \(*fx*\) button to edit an expression that sets the values of the option.  
  
5.  For each icon in the indicator set, update the values in the **Start** and **End** text boxes.  
  
     Optionally, click the **Expression** \(*fx*\) button to edit an expression that sets the values of the **Start** and **End** options.  
  
    > [!NOTE]  
    >  The values in the **Start** and **End** text boxes must be numeric.  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Indicators &#40;Report Builder and SSRS&#41;](../Topic/Indicators%20\(Report%20Builder%20and%20SSRS\).md)  
  
  