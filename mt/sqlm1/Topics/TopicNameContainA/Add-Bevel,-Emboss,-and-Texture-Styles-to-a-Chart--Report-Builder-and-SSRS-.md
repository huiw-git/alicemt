---
title: Add Bevel, Emboss, and Texture Styles to a Chart (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
---
# Add Bevel, Emboss, and Texture Styles to a Chart (Report Builder and SSRS)
  When using certain chart types, you can specify a drawing effect to increase the visual impact of your chart. These drawing effects are only applied to the series of your chart. They have no effect on any other chart element.  
  
 When you are using any variant of a pie or doughnut chart, you can specify a soft edge or concave drawing style, similar to bevel or emboss effects that can be applied to an image.  
  
 When you are using any variant of a bar or column chart, you can apply texture styles, such as cylinder, wedge, and light\-to\-dark, to the individual bars or columns.  
  
 In addition to these drawing styles, you can add borders and shadows to many chart elements to give the illusion of depth. For more information on other ways to format the chart, see [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To add bevel or emboss styles to a pie or doughnut chart  
  
1.  On the **View** tab, select **Properties** to open the Properties pane.  
  
2.  Select the pie or doughnut chart that you want to enhance. Select a data field in the chart, not the entire chart.  
  
3.  In the Properties pane, expand the **CustomAttributes** node.  
  
4.  For PieDrawingStyle, select a style from the drop\-down list.  
  
> [!NOTE]  
>  You can't have 3D and bevel or emboss styles on the same chart. If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.  
  
 ![Pie chart with concave drawing style](../../Images\Image\ImageNotContaina/rs_PieDrawingEffects_Concave.gif "rs_PieDrawingEffects_Concave")  
  
### To add texture styles to a bar or column chart  
  
1.  Select the bar or column chart that you want to enhance. Select a data field in the chart, not the entire chart.  
  
2.  Open the Properties pane.  
  
3.  Expand the **CustomAttributes** node.  
  
4.  For DrawingStyle, select a style from the drop\-down list.  
  
> [!NOTE]  
>  You can't have 3D and bevel or emboss styles on the same chart. If you have enabled 3D for the chart, you will not see the PieDrawingStyle property.  
  
 ![Bar chart with LightToDark drawing effect](../../Images\Image\ImageNotContaina/rs_BarDrawingEffects_LightToDark.gif "rs_BarDrawingEffects_LightToDark")  
  
## See Also  
 [Bar Charts &#40;Report Builder and SSRS&#41;](../Topic/Bar%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Column Charts &#40;Report Builder and SSRS&#41;](../Topic/Column%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Pie Charts &#40;Report Builder and SSRS&#41;](../Topic/Pie%20Charts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md)  
  
  