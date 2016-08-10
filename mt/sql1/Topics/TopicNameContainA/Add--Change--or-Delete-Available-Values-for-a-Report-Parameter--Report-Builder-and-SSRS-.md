---
title: "Add, Change, or Delete Available Values for a Report Parameter (Report Builder and SSRS)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e03264c-523f-4c59-b71b-ceef600f75f6
caps.latest.revision: 12
manager: mblythe
---
# Add, Change, or Delete Available Values for a Report Parameter (Report Builder and SSRS)
After you create a report parameter, you can specify a list of available values to display to the user. An available values list limits the choices a user can make to only valid values for the parameter.  
  
 Available values appear in a drop-down list next to the report parameter on the toolbar when the report runs. Report parameters can represent one value or multiple values. For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.  
  
 You can provide a static list of values or a list from a report dataset. You can optionally provide a friendly name for values by specifying a label field. For example, for a parameter based on a `ProductID` field, you can display the `ProductName` field in the parameter label. When the report runs, the user can choose from the product names, but the actual chosen value is the corresponding `ProductID`.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
 After you publish a report, you can override the available values that you define in the report in the report authoring tool, by setting parameter property values on the report server. For more information, see [Report Parameters (Report Builder and Report Designer)](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md).  
  
### To add or change the available values for a report parameter  
  
1.  In the Report Data pane, expand the Parameters node. Right-click the parameter and click **Parameter Properties**. The **Report Parameter Properties** dialog box opens.  
  
    > [!NOTE]  
    >  If the Report Data pane is not visible, click **View** and then click **Report Data**.  
  
2.  Click **Available Values**. Select an available values option:  
  
    -   Click **Specify values** to manually provide a list of values, and optionally, friendly names (the labels) for the values.  
  
         Click **Add** and then enter the value in the **Value** text box, and optionally, the label in the **Label** text box. If you do not provide a label, the value is used. You can write an expression for a value. The data type must match the data type of the parameter. Field names cannot be used in an expression for a parameter. For examples, see [Commonly Used Filters (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Commonly-Used-Filters--Report-Builder-and-SSRS-.md).  
  
         Repeat this step for as many values as you want to provide. The order of items you see in this list determines the order that the user sees them in the drop-down list. To change the order of an item in the list, click a **Value** or **Label** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.  
  
    -   Click **Get values from a query** to provide the name of an existing dataset that retrieves the values, and optionally, the friendly names for this parameter.  
  
        > [!IMPORTANT]  
        >  If the same dataset contains the corresponding query parameter for the report parameter, the report will display an error message when you try to run it. You resolve this error by using a different dataset to retrieve the values.  
  
         In **Dataset**, choose the name of the dataset.  
  
         In **Value field**, choose the name of the field that provides parameter values.  
  
         In **Label field**, choose the name of the field that provides the friendly names for the parameter. If there is no separate field for friendly names, choose the same field as you chose for the **Value** field.  
  
3.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
     When you preview the report, you see a drop-down list of available values for the parameter.  
  
### To remove the available values for a report parameter  
  
1.  In the Report Data pane, expand the Parameters node. Right-click the parameter and click **Parameter Properties**. The **Report Parameters** dialog box opens.  
  
2.  Click **Available Values**.  
  
3.  In **Select from one of the following options**, click **None**.  
  
4.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
     When you preview the report, you the drop-down list of available values for the parameter no longer appears.  
  
## See Also  
 [Change the Order of a Report Parameter (Report Builder and SSRS)](../../Topics/TopicNameContainA/Change-the-Order-of-a-Report-Parameter--Report-Builder-and-SSRS-.md)   
 [Add, Change, or Delete a Report Parameter (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add--Change--or-Delete-a-Report-Parameter--Report-Builder-and-SSRS-.md)   
 [Add Cascading Parameters to a Report (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-Cascading-Parameters-to-a-Report--Report-Builder-and-SSRS-.md)   
 [Add, Change, or Delete Default Values for a Report Parameter (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add--Change--or-Delete-Default-Values-for-a-Report-Parameter--Report-Builder-and-SSRS-.md)   
 [Parameters Collection References (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Parameters-Collection-References--Report-Builder-and-SSRS-.md)   
 [Tutorial: Adding a Parameter to Your Report (Report Builder)](assetId:///eab34ec4-b3ad-4a76-95cc-07b2f75ee6d7)   
 [Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md)