---
title: Create a Stepped Report (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5933c4f0-c713-4ecb-b521-ff46c9c63fff
---
# Create a Stepped Report (Report Builder and SSRS)
  A stepped report shows detail rows or child groups indented under a parent group in the same column, as shown in the example below:  
  
 ![Rendered stepped report](../../Images\Image\ImageNotContaina/SteppedReportRendered.gif "SteppedReportRendered")  
  
 Traditional table reports place the parent group in an adjacent column on the report. The new tablix data region enables you to add a group and detail rows or child groups to the same column. To differentiate the group rows from the detail or child group rows, you can apply formatting such as font color, or you can indent the detail rows.  
  
 The procedures in this topic show you how to manually create a stepped report, but you can also use the New Table and Matrix Wizard. It provides the layout for stepped reports, making it easy to create them. After you complete the wizard, you can further enhance the report.  
  
> [!NOTE]  
>  The wizard is available only in Report Builder.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To create a stepped report  
  
1.  Create a table report. For example, insert a tablix data region and add fields to the Data row.  
  
2.  Add a parent group to your report.  
  
    1.  Click anywhere in the table to select it. The Grouping pane displays the Details group in the Row Groups pane.  
  
    2.  In the Grouping Pane, right\-click the Details Group, point to **Add Group**, and then click **Parent Group**.  
  
    3.  In the **Tablix Group** dialog box, provide a name for the group and type or select a group expression from the drop\-down list. The drop\-down list displays the simple field expressions that are available in the Report Data pane. For example, \[PostalCode\] is a simple field expression for the PostalCode field in a dataset.  
  
    4.  Select **Add group header**. This option adds a static row above the group for the group label and group totals. Likewise, you can select **Add group footer** to add a static row below the group. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
     You now have a basic tabular report. When it is rendered, you see one column with the group instance value, and one or more columns with grouped detail data. The following figure shows what the data region might look like on the design surface.  
  
     ![Table data region with group](../../Images\Image\ImageNotContaina/TableDataRegionWithGroup.gif "TableDataRegionWithGroup")  
  
     The following figure shows how the rendered data region might look when you view the report.  
  
     ![Rendered grouped report](../../Images\Image\ImageNotContaina/TableReportRendered.gif "TableReportRendered")  
  
3.  For a stepped report, you do not need the first column that shows the group instance. Instead, copy the value in the group header cell, delete the group column, and paste in the first text box in the group header row. To remove the group column, right\-click the group column or cell, and click **Delete Columns**. The following figure shows what the data region might look like on the design surface.  
  
     ![Data region with group header row](../../Images\Image\ImageNotContaina/TableDataRegionGroupHeader.gif "TableDataRegionGroupHeader")  
  
4.  To indent the detail rows under the group header row in the same column, change the padding of the detail data cell.  
  
    1.  Select the cell with the detail field that you want to indent. The text box properties for that cell appear in the Properties pane.  
  
    2.  In the Properties pane, under **Alignment**, expand the properties for **Padding**.  
  
    3.  For **Left**, type a new padding value, such as **.5in**. Padding indents the text in the cell by the value you specify. The default padding is 2 points. Valid values for the Padding properties are zero or a positive number, followed by a size designator.  
  
         Size designators are:  
  
        |||  
        |-|-|  
        |**in**|Inches \(1 inch \= 2.54 centimeters\)|  
        |**cm**|Centimeters|  
        |**mm**|Millimeters|  
        |**pt**|Points \(1 point \= 1\/72 inch\)|  
        |**pc**|Picas \(1 pica \= 12 points\)|  
  
     Your data region will look similar to the following example.  
  
     ![Data region for stepped report](../../Images\Image\ImageNotContaina/SteppedReportDataRegion.gif "SteppedReportDataRegion")  
  
     **Data Region for Stepped Report Layout**  
  
     On the **Home** tab Click **Run**. The report displays the group with indented levels for the child group values.  
  
### To create a stepped report with multiple groups  
  
1.  Create a report as described in the previous procedure.  
  
2.  Add additional groups to your report.  
  
    1.  In the Row Groups pane, right\-click the group, click **Add Group**, and then choose the type of group you want to add.  
  
        > [!NOTE]  
        >  There are several ways to add groups to a data region. For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20or%20Delete%20a%20Group%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
    2.  In the **Tablix Group** dialog box, type a name.  
  
    3.  In **Group expression**, type an expression or select a dataset field to group on. To create an expression, click the expression \(**fx**\) button to open the **Expression** dialog box.  
  
    4.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
3.  Change the padding for the cell that displays the group data.  
  
## See Also  
 [Page Headers and Footers &#40;Report Builder and SSRS&#41;](../Topic/Page%20Headers%20and%20Footers%20\(Report%20Builder%20and%20SSRS\).md)   
 [Formatting Report Items &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Report%20Items%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables &#40;Report Builder  and SSRS&#41;](../Topic/Tables%20\(Report%20Builder%20%20and%20SSRS\).md)   
 [Matrices &#40;Report Builder and SSRS&#41;](../Topic/Matrices%20\(Report%20Builder%20and%20SSRS\).md)   
 [Lists &#40;Report Builder and SSRS&#41;](../Topic/Lists%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../Topic/Tables,%20Matrices,%20and%20Lists%20\(Report%20Builder%20and%20SSRS\).md)  
  
  