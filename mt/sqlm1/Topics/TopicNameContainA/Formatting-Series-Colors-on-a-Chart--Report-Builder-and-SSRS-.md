---
title: Formatting Series Colors on a Chart (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe541501-cac5-47b1-b95f-c410db789190
---
# Formatting Series Colors on a Chart (Report Builder and SSRS)
  Reporting Services provides several built\-in palettes for charts, or you can define a custom palette. By default, charts use the built\-in **Pacific** color palette to fill each series. These colors also appear in the legend. When multiple series are added to the chart, the chart assigns the series a color in the order that the colors have been defined in the palette.  
  
 If there are a greater number of series than there are colors in the palette, the chart will begin reusing colors, and two series may have the same color. This frequently occurs if you are using a Shape chart, where each data point is assigned a color from the palette. To avoid confusion, define a custom palette with at least the same number of colors as you have series on your chart.  
  
 You can select a new palette or define a custom palette from the Properties pane. For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](../Topic/Define%20Colors%20on%20a%20Chart%20Using%20a%20Palette%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Using Built\-In Palettes  
 Reporting Services provides a list of predefined, built\-in palettes that you can use to define a color set for series on your chart. All built\-in palettes contain between 10 and 16 color values. You cannot extend the built\-in palette to include more colors, so if you need more than 16 colors, you must define a custom palette.  
  
 If you are printing a report, consider using the **Greyscale** palette. This palette uses shades of black and white to represent each series in a chart.  
  
 The palette named Default was used as the default chart palette in earlier versions of Reporting Services. It has been maintained with the same name for consistency. Charts will upgrade seamlessly using the Default palette, but after upgrading, you might consider changing it.  
  
## Using Custom Palettes  
 If you want to apply your own colors to the chart, use a custom palette. A custom palette let you add your own colors in the order you want them to appear on the chart. A custom palette is especially helpful if the number of series in your chart is unknown at design time. For more information, see [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](../Topic/Define%20Colors%20on%20a%20Chart%20Using%20a%20Palette%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Using a Color Fill on Each Series  
 You can also define your own colors on the chart by specifying a color for each series on the chart. To do this, open the **Series Properties** dialog box and set the **Color** property for **Fill**. This approach will override all defined palettes. Generally, it is better to use a custom palette to define your own colors because the number of series in your dataset may not be known until report processing.  
  
 This approach is best suited when you want to conditionally set the color of the series based on an expression.  For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Data%20Points%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md).  
  
## In This Section  
 [Specify Consistent Colors across Multiple Shape Charts &#40;Report Builder and SSRS&#41;](../Topic/Specify%20Consistent%20Colors%20across%20Multiple%20Shape%20Charts%20\(Report%20Builder%20and%20SSRS\).md)  
  
 [Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](../Topic/Define%20Colors%20on%20a%20Chart%20Using%20a%20Palette%20\(Report%20Builder%20and%20SSRS\).md)\)  
  
 [Highlight Chart Data by Adding Strip Lines &#40;Report Builder and SSRS&#41;](../Topic/Highlight%20Chart%20Data%20by%20Adding%20Strip%20Lines%20\(Report%20Builder%20and%20SSRS\).md)  
  
## See Also  
 [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](../Topic/Add%20Bevel,%20Emboss,%20and%20Texture%20Styles%20to%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)   
 [Charts &#40;Report Builder and SSRS&#41;](../Topic/Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20the%20Legend%20on%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)  
  
  