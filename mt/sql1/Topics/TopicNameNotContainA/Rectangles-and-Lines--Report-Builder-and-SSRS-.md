---
title: "Rectangles and Lines (Report Builder and SSRS)"
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
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
caps.latest.revision: 10
caps.handback.revision: 0
manager: mblythe
---
# Rectangles and Lines (Report Builder and SSRS)
Rectangles and lines can create visual effects within a report. You can set display properties on these report items from the Border section of the Home tab, and set other properties by using the Properties pane. You can add features like a background color or image, a tooltip, or a bookmark to a rectangle.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
##  <a name="RectanglesLinesReportParts"></a> Rectangles and Lines as Report Parts  
 You can publish rectangles with the items that they contain separately from the report as report parts. [!INCLUDE[ssRBrptparts](../../Topics/TopicNameContainA/tokens/ssRBrptparts_md.md)]  
  
 You cannot publish the report items within the rectangle as report parts. When people add the rectangle to a report, they get the rectangle and the items it contains.  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="RectangleAsContainer"></a> Using a Rectangle as a Container  
 You can use a rectangle as a container for other items. When you move the rectangle, the items that are contained within the rectangle move along with it. An item within the rectangle shows the name of the rectangle in its **Parent** property. For more information about using a rectangle as a container, see [Add a Rectangle or Container (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Rectangle-or-Container--Report-Builder-and-SSRS-.md) and [Display the Same Data on a Matrix and a Chart (Report Builder)](../../Topics/TopicNameContainA/Display-the-Same-Data-on-a-Matrix-and-a-Chart--Report-Builder-.md).  
  
> [!NOTE]  
>  A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle. If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container. The rectangle will not be listed in the item's Parent property.  
  
 When using rectangles to contain report items, consider how the items will be affected as a whole during report rendering. Report items that contain repeated rows of data (for example, tables) will expand to accommodate the data that is returned by a query, and this affects the positioning of other items in the rectangle. A table will push items down if they are positioned below the data region. To anchor an item in place, you can place the report item inside of a rectangle that has an upper edge above the lower edge of the table. For more information, see [Rendering Behaviors (Report Builder  and SSRS)](../../Topics/TopicNameNotContainA/Rendering-Behaviors--Report-Builder--and-SSRS-.md).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="ReportBorder"></a> Adding a Report Border  
 You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles. For more information, see [Add a Border to a Report (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Border-to-a-Report--Report-Builder-and-SSRS-.md).  
  
 ![Arrow icon used with Back to Top link](../../Topics/TopicNameContainA/images/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="HowTo"></a> How-To Topics  
 [Add a Border to a Report (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Border-to-a-Report--Report-Builder-and-SSRS-.md)  
  
 [Add a Rectangle or Container (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Rectangle-or-Container--Report-Builder-and-SSRS-.md)  
  
 [Add and Modify a Line (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-and-Modify-a-Line--Report-Builder-and-SSRS-.md)  
  
## See Also  
 [Add a Rectangle or Container (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Rectangle-or-Container--Report-Builder-and-SSRS-.md)