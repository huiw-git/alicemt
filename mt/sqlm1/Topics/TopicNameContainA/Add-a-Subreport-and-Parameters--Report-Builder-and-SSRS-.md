---
title: Add a Subreport and Parameters (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94f960f8-a629-4f1e-8277-c3b8f0680d98
---
# Add a Subreport and Parameters (Report Builder and SSRS)
  Add subreports to a report when you want to create a main report that is a container for multiple related reports. A subreport is a reference to another report. To relate the reports through data values \(for example, to have multiple reports show data for the same customer\), you must design a parameterized report \(for example, a report that shows the details for a specific customer\) as the subreport. When you add a subreport to the main report, you can specify parameters to pass to the subreport.  
  
 You can also add subreports to dynamic rows or columns in a table or matrix. When the main report is processed, the subreport is processed for each row. In this case, consider whether you can achieve the desired effect by using data regions or nested data regions.  
  
 To add a subreport to a report, you must first create the report that will act as the subreport. For more information on creating the subreport, see [Subreports &#40;Report Builder and SSRS&#41;](../Topic/Subreports%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To add a subreport  
  
1.  On the **Insert** tab, click **Subreport**.  
  
2.  On the design surface, click a location on the report and then drag a box to the desired size of the subreport. Alternatively, click the design surface to create a subreport of default size.  
  
3.  Right\-click the subreport, and then click **Subreport Properties**.  
  
4.  In the **Subreport Properties** dialog box, type a name in the **Name** text box or accept the default. The name must be unique within the report. By default, a general name such as Subreport1 or Subreport2 is assigned.  
  
5.  In the **Use this report as a subreport** box, click **Browse**, or type the name of the report. Clicking **Browse** is preferred because the path to the subreport will be specified automatically. You can specify the report in the several ways. For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](../Topic/Specifying%20Paths%20to%20External%20Items%20\(Report%20Builder%20and%20SSRS\).md).  
  
6.  \(Optional\) Click **Yes** for **Omit border on page break** to prevent a border from being rendered in the middle of the subreport if the subreport spans more than one page.  
  
7.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
### To specify parameters to pass to a subreport  
  
1.  In Design view, right\-click the subreport and then click **Subreport Properties**.  
  
2.  In the **Subreport Properties** dialog box, click **Parameters**.  
  
3.  Click **Add**. A new row is added to the parameter grid.  
  
4.  In the **Name** text box, type the name of a parameter in the subreport or choose it from the list box. This name must match a report parameter, not a query parameter, in the subreport.  
  
5.  In the **Value** list box, type or select a value to pass to the subreport. This value can be static text or an expression that references a field or other object in the main report.  
  
    > [!NOTE]  
    >  In Report Builder, if a parameter is missing from the **Parameters** list and the subreport has a default value defined, the subreport will be processed correctly.  
    >   
    >  In Report Designer, all parameters that are required by the subreport must be included in the **Parameters** list. If a required parameter is missing, the subreport is not displayed correctly in the main report.  
  
6.  Repeat steps 3\-5 to specify a name and value for each subreport parameter.  
  
7.  To delete a subreport parameter, click the parameter in the parameter grid, and then click **Delete**.  
  
8.  To change the order of a subreport parameter, click the parameter, and then click the up button or the down button.  
  
     Changing the order of a subreport parameter does not affect the processing of the subreport.  
  
## See Also  
 [Subreports &#40;Report Builder and SSRS&#41;](../Topic/Subreports%20\(Report%20Builder%20and%20SSRS\).md)   
 [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../Topic/Rendering%20Behaviors%20\(Report%20Builder%20%20and%20SSRS\).md)  
  
  