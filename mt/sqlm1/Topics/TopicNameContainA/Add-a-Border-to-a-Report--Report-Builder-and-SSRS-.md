---
title: Add a Border to a Report (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
---
# Add a Border to a Report (Report Builder and SSRS)
  You can add a border to a [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] paginated report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.    
    
 If you add a report border that appears on the page header and footer, do not suppress the header and footer on the first and last pages of the report. If you do, the border may appear cut off at the top or bottom of the first and last pages of the report. For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](../Topic/Page%20Headers%20and%20Footers%20\(Report%20Builder%20and%20SSRS\).md).    
    
## To add a border to a report    
    
1.  Right\-click in the header outside any items in the header, and click **Header Properties**. On the **Border** tab, add a left, top, and right border with the style you want.    
    
    > [!NOTE]    
    >  If your report doesn't have headers, you can place borders around just the report body, or you can add headers from the **Insert** tab.    
    
2.  Right\-click in the body outside any items on the design surface, and click **Body Properties**. On the **Border** tab, add a left and right border with the style you want.    
    
3.  Right\-click in the footer outside any items in the footer, and click **Footer Properties**. On the **Border** tab, add a left, bottom, and right border with the style you want.    
    
## See Also    
 [Rectangles and Lines &#40;Report Builder and SSRS&#41;](../Topic/Rectangles%20and%20Lines%20\(Report%20Builder%20and%20SSRS\).md)    
    
  