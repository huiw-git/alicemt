---
title: "Customize the Parameters Pane in a Report (Report Builder)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ce9e8d5-911a-4422-928f-a8d005b79fc6
caps.latest.revision: 9
caps.handback.revision: 0
manager: mblythe
---
# Customize the Parameters Pane in a Report (Report Builder)
In [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/tokens/ssSQL15_md.md)] you can customize the parameters pane. Using the design surface in Report Builder, you can drag a parameter to a specific column and row in the parameters pane. You can add and remove columns to change the layout of the pane.  
  
 When you drag a parameter to a new column and row in the pane, the parameter order changes in the **Report Data** pane. When you change the order of the parameter in the **Report Data** pane, the location of the parameter in the pane is changed. For more information about the parameter order, see [Change the Order of a Report Parameter (Report Builder and SSRS)](../../Topics/TopicNameContainA/Change-the-Order-of-a-Report-Parameter--Report-Builder-and-SSRS-.md).  
  
## To customize the parameters pane  
  
1.  On the **View** tab, select the **Parameters** checkbox to display the parameters pane.  
  
     ![Access parameters pane from View tab](../../Topics/TopicNameContainA/images/ssrs_CustomParameter_AccessParameterPaneDesignMode.png "ssrs_CustomParameter_AccessParameterPaneDesignMode")  
  
     The pane appears at the top of the design surface.  
  
2.  To add a parameter to the pane, do one of the following.  
  
    -   Right click an empty cell in the parameters pane, and then click **Add Parameter**.  
  
         ![Add new parameter from parameters pane](../../Topics/TopicNameContainA/images/ssrs_CustomizeParameter_AddNewParameter.png "ssrs_CustomizeParameter_AddNewParameter")  
  
    -   Right click **Parameters** in the **Report Data** pane, and then click **Add Parameter**.  
  
3.  To move a parameter to a new location in the parameters pane, drag the parameter to a different cell in the pane.  
  
     When you change the location of the parameter in the pane, the order of the parameter in the **Parameters** list in the **Report Data** pane is automatically changed. For more information about the impact of the parameter order, see [Change the Order of a Report Parameter (Report Builder and SSRS)](../../Topics/TopicNameContainA/Change-the-Order-of-a-Report-Parameter--Report-Builder-and-SSRS-.md)  
  
4.  To access the properties for a parameter, do one of the following.  
  
    -   Right click the parameter in the parameters pane, and then click **Parameter Properties**.  
  
         ![Access parameter properties from the parameters pane](../../Topics/TopicNameContainA/images/ssrs_CustomizeParameter_AccessParameterProperties_composite.png "ssrs_CustomizeParameter_AccessParameterProperties_composite")  
  
    -   Right click the parameter in the **Report Data** pane, and then click **Parameter Properties**.  
  
5.  To add new columns and rows to the pane, or delete existing rows and columns, right click anywhere in the parameters pane and then click a command on the menu that displays.  
  
     ![Add columns and rows to the parameters pane](../../Topics/TopicNameContainA/images/ssrs_CustomParameter_AddColumnsRows.png "ssrs_CustomParameter_AddColumnsRows")  
  
    > [!IMPORTANT]  
    >  When you delete a column or row that contains parameters, the parameters are deleted from the report.  
  
6.  To delete a parameter from the pane and from the report, do one of the following.  
  
    -   Right click the parameter in the parameters pane, and then click  **Delete**.  
  
         ![Delete parameters from the parameters pane](../../Topics/TopicNameContainA/images/ssrs_CustomParameter_DeleteParameter.png "ssrs_CustomParameter_DeleteParameter")  
  
    -   Right click parameter in the **Report Data** pane, and then click **Delete**.  
  
## See Also  
 [Report Parameters (Report Builder and Report Designer)](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md)