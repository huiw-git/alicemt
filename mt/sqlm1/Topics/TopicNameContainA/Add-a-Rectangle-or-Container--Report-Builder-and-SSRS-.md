---
title: Add a Rectangle or Container (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f905c35f-754d-4d02-80f3-85e29ddda826
---
# Add a Rectangle or Container (Report Builder and SSRS)
  Add a rectangle to a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report when you want a graphical element to separate areas of the report, emphasize areas of a report, or provide a background for one or more report items. Rectangles are also used as containers to help control the way data regions render in a report. You can customize the appearance of a rectangle by editing rectangle properties such as the background and border colors. For more information about using a rectangle as a container, see [Rectangles and Lines &#40;Report Builder and SSRS&#41;](../Topic/Rectangles%20and%20Lines%20\(Report%20Builder%20and%20SSRS\).md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](../Topic/Display%20the%20Same%20Data%20on%20a%20Matrix%20and%20a%20Chart%20\(Report%20Builder\).md).    
   
## To add a rectangle    
    
1.  On the **Insert** tab, in the **Report Items** group, click **Rectangle.**    
    
2.  On the design surface, click the location where you want the upper left corner of the rectangle, and drag to where you want the lower\-right corner.    
    
     Note that as you move the cursor, "snap lines" appear as the cursor lines up with other objects on the design surface. These help you if you want objects to be aligned.    
    
## To create a container    
    
1.  Add a rectangle report item to the report.    
    
2.  Drag other report items into the rectangle.    
    
    > [!NOTE]    
    >  A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle. If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.    
    
## To change rectangle properties such as color, style, or weight    
    
1.  Select the rectangle, and then click the line color, style, or weight options in the **Border** section of the Home tab.    
    
2.  Click the arrow next to the **Border** button to determine which sides of the rectangle to change.    
    
    > [!NOTE]    
    >  If you set the line style to **Double** and the line width is 1 1\/2 pt or narrower, the line may not appear double when you run the report in Report Builder, Report Designer, or in the [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] web portal. It appears double when you export the report to other formats such as Microsoft Word and Acrobat PDF.    
    
## See Also    
 [Rectangles and Lines &#40;Report Builder and SSRS&#41;](../Topic/Rectangles%20and%20Lines%20\(Report%20Builder%20and%20SSRS\).md)     
 [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../Topic/Rendering%20Behaviors%20\(Report%20Builder%20%20and%20SSRS\).md)    
    
  