---
title: Create a Date Attribute (Master Data Services)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
robots: noindex,nofollow
---
# Create a Date Attribute (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], create a date attribute when you want users to enter a date as an attribute value.  
  
> [!NOTE]  
>  The attribute is called DateTime, but time values are not supported.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators &#40;Master Data Services&#41;](../Topic/Administrators%20\(Master%20Data%20Services\).md).  
  
-   You must have an entity to create the attribute for. For more information, see [Create an Entity &#40;Master Data Services&#41;](../Topic/Create%20an%20Entity%20\(Master%20Data%20Services\).md).  
  
### To create a date attribute  
  
1.  In [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  On the **Manage Model** page, select a model from the grid and then click **Entities**.  
  
3.  On the **Manage Entity** page, select the row for the entity that you want to create an attribute for.  
  
4.  Click **Attributes**.  
  
5.  On the **Manage Attributes** page, do one of the following and then click **Add**.  
  
    -   If the attribute is for leaf members, select **Leaf** from the **Member Types** list box.  
  
    -   If the attribute is for consolidated members, select **Consolidated** from the **Member Types** list box.  
  
    -   If the attribute is for collections, select **Collection** from the **Member Types** list box.  
  
6.  In the **Name** box, type a name for the attribute. For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../Topic/Reserved%20Words%20\(Master%20Data%20Services\).md).  
  
7.  Optionally, type a display name, and type a description for the attribute in the **Description** box.  
  
8.  In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.  
  
9. From the **Attribute type** list, select **Free\-form**.  
  
10. From the **Data type** list, select **DateTime**.  
  
11. From the **Input mask** list, select a format for dates.  
  
12. Optionally, select **Enable change tracking** to track changes to groups of attributes. For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../Topic/Add%20Attributes%20to%20a%20Change%20Tracking%20Group%20\(Master%20Data%20Services\).md).  
  
13. Click **Save**.  
  
## To display the time portion of a datetime value  
 To have the user interface display the time portion of a datetime value, you must select an appropriate input mask for the attribute. None of the built\-in masks for Datetime attributes do this, but you can add a new mask that will allow you to display time. To do so, add a row in the mdm.tblList table of the MDS database, where the built\-in masks are stored. The row should have the following values:  
  
|||  
|-|-|  
|ListCode|lstInputMask|  
|ListName|Input Mask|  
|Seq|19|  
|List Option|dd\/MM\/yyyy hh:mm:ss tt|  
|Option ID|19|  
|IsVisible|1|  
|Group\_ID|3|  
  
 After you enter a row with the above values in the mdm.tblList table, the “dd\/MM\/yyyy hh:mm:ss tt” mask will be available in the Input mask list box. You can then select that mask to display the date and time in a datetime attribute column of an entity in the MDS Explorer.  
  
 The Input Mask is a custom .NET DateTime format string. For more information, see [Custom Date and Time Format Strings](https://msdn.microsoft.com/en-us/library/8kb3ddd4\(v=vs.110\).aspx)  
  
## See Also  
 [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md)   
 [Change an Attribute Name and Data Type &#40;Master Data Services&#41;](../Topic/Change%20an%20Attribute%20Name%20and%20Data%20Type%20\(Master%20Data%20Services\).md)   
 [Create a Domain-Based Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20Domain-Based%20Attribute%20\(Master%20Data%20Services\).md)   
 [Create a File Attribute &#40;Master Data Services&#41;](../Topic/Create%20a%20File%20Attribute%20\(Master%20Data%20Services\).md)  
  
  