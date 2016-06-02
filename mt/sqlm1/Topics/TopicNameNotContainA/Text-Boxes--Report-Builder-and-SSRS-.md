---
title: Text Boxes (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df49e4e3-f279-4c63-a03b-b70c095f4ba2
---
# Text Boxes (Report Builder and SSRS)
  When you think of a text box, you probably think of a stand\-alone box containing text on a surface like in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Office PowerPoint. In [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated reports, some text boxes are like that, and they can display static text for titles, descriptions, and labels, or dynamic text based on expressions. But every cell in a table or matrix \(a tablix data region\) also contains a text box, which you can format the same way you format stand\-alone text boxes in your report.  
  
> [!NOTE]  
>  If you drag a report dataset field value directly to the report design surface, or to a text box on the report design surface, you only see the first value in the result set when you run the report. To see all the values for a field, you need to create a table, matrix, or list data region first, and drag the field to a cell in the data region. That way, when you run the report, you will see all the values in that field.  
  
 To show repeating text in a free\-form layout, create a list data region and place the text box in it. Use a list when you want to repeat a form for multiple values, for example, a customer invoice form repeated once for each customer. Read more about [creating invoices and forms with lists](Create%20Invoices%20and%20Forms%20with%20Lists%20\(Report%20Builder%20and%20SSRS\).md).  
  
 Use a rectangle container when you want to control the text box layout and white space below the last text box. For more information, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](../Topic/Rectangles%20and%20Lines%20\(Report%20Builder%20and%20SSRS\).md).  
  
 The expressions in a text box can contain literal text, point to a field in the database, or calculate data. All expressions are shown as placeholder text so that you can format numbers, colors, and other appearance properties. You can also combine placeholders with literal text in the same text box.  
  
 You can format text in any single text box with multiple fonts, colors, styles, and actions. For more information, see [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Text%20and%20Placeholders%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
##  <a name="GrowShrinkTextBox"></a> Growing and Shrinking a Text Box  
 By default, text boxes are a fixed size. You can allow a text box to shrink or expand vertically based on its contents. For more information, see [Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;](../Topic/Allow%20a%20Text%20Box%20to%20Grow%20or%20Shrink%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Rotating a Text Box  
 Rotating text boxes can help you create more readable reports, support locale\-specific text orientation, fit more columns on a printed report that has fixed page size, and create reports with more graphical appeal. A text box can be rotated in different directions: horizontal, vertical (rotated 90 degrees), or rotated by 270 degrees. The vertical option is most commonly used for East Asian languages that are written top to bottom. In most renderers the vertical option handles the glyph rotation properly so that the text is written top to bottom, but the characters are not on their sides. For other languages, in the vertical and 270\-degree options the text is written sideways.  
  
 You can rotate text boxes that contain static text, fields from a report dataset, or calculated data. The text box can be stand\-alone in the report body, in a table or matrix, or in a report header and footer.  
  
 The following picture shows three versions of a table report that groups data by month. The text box that contains the month value uses a different text box orientation.  
  
 ![rs_TextBoxOrientation](../../Images\Image\ImageNotContaina/rs_TextBoxOrientation.gif "rs_TextBoxOrientation")  
  
 Orientation is set on the text box and applies to all the text in the box. You cannot specify a different orientation for parts of the text box.  
  
 To get started, see the section on rotating text in the [Tutorial: Format Text &#40;Report Builder&#41;](../Topic/Tutorial:%20Format%20Text%20\(Report%20Builder\).md), and see [Set Text Box Orientation &#40;Report Builder and SSRS&#41;](../Topic/Set%20Text%20Box%20Orientation%20\(Report%20Builder%20and%20SSRS\).md).  
  
##  <a name="HowTo"></a> How\-To Topics  
 [Add, Move, or Delete a Text Box &#40;Report Builder and SSRS&#41;](../Topic/Add,%20Move,%20or%20Delete%20a%20Text%20Box%20\(Report%20Builder%20and%20SSRS\).md)  
  
 [Format Text in a Text Box &#40;Report Builder and SSRS&#41;](../Topic/Format%20Text%20in%20a%20Text%20Box%20\(Report%20Builder%20and%20SSRS\).md)  
  
 [Set Text Box Orientation &#40;Report Builder and SSRS&#41;](../Topic/Set%20Text%20Box%20Orientation%20\(Report%20Builder%20and%20SSRS\).md)  
  
 [Allow a Text Box to Grow or Shrink &#40;Report Builder and SSRS&#41;](../Topic/Allow%20a%20Text%20Box%20to%20Grow%20or%20Shrink%20\(Report%20Builder%20and%20SSRS\).md)  
  
## See Also  
 [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Text%20and%20Placeholders%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Numbers%20and%20Dates%20\(Report%20Builder%20and%20SSRS\).md)  
  
  