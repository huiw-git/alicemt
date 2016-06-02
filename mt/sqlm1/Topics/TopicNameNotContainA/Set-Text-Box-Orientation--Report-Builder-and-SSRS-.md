---
title: Set Text Box Orientation (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
---
# Set Text Box Orientation (Report Builder and SSRS)
In a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report, you can rotate a text box in different directions:   
* Horizontally   
* Vertically \(rotated 90 degrees, with text reading from top to bottom\)  
* Rotated by 270 degrees \(text reading from bottom to top\).   
  
Because you rotate the text box not the text, the rotation applies to all the text in the text box. You cannot specify different directions for parts of the text. Size the column width and the row height manually to accommodate the rotated text.  
  
 The WritingMode property, which you use to specify text orientation, isn't in the **Text Box Properties** dialog box. It's in the Properties pane and set the property there.   
  
## To rotate text  
  
1.  Create a report or open an existing report, and [add a text box](Add,%20Move,%20or%20Delete%20a%20Text%20Box%20\(Report%20Builder%20and%20SSRS\).md) to the design surface.  
  
3.  Select the text box that you want to rotate.  
  
2.  If the Properties pane is not open, on the **View** tab, select the **Properties** check box.  
  
4.  In the Properties pane, find the WritingMode property and select the text orientation to apply to the text box.  
  
    > [!NOTE]  
    >  When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.  
  
5.  In the list box, select **Horizontal**, **Vertical**, or **Rotate270**.  
  
## See Also  
 [Text Boxes &#40;Report Builder and SSRS&#41;](../Topic/Text%20Boxes%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tutorial: Format Text &#40;Report Builder&#41;](../Topic/Tutorial:%20Format%20Text%20\(Report%20Builder\).md)  
  
  