---
title: Create InfoSource for Transaction Data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
---
# Create InfoSource for Transaction Data
  Use the **Create InfoSource for Transaction Data** dialog box to create a new InfoSource for transaction data in the SAP Netweaver BW system.  
  
 You can open the **Create InfoSource for Transaction Data** dialog box from the **Connection Manager** page of the **SAP BW Destination Editor**. To learn more about the SAP BW destination, see [SAP BW Destination](../../Topics\TopicNameNotContainA/SAP-BW-Destination.md).  
  
> [!IMPORTANT]  
>  The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment. For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.  
  
 **To open the Create InfoSource for Transaction Data dialog box**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package that contains the SAP BW destination.  
  
2.  On the **Data Flow** tab, double\-click the SAP BW destination.  
  
3.  In the **SAP BW Destination Editor**, click **Connection Manager** to open the **Connection Manager** page of the editor.  
  
4.  On the **Connection Manager** page, in the **Create SAP BW Objects** group box, select **InfoSource**, and then click **Create**.  
  
5.  In the **Create InfoSource** dialog box, select **Transaction data**, and then click **OK**.  
  
## General Options  
 **InfoSource name**  
 Enter a name for the new InfoSource.  
  
 **Short description**  
 Enter a short description for the new InfoSource.  
  
 **Long description**  
 Enter a long description for the new InfoSource.  
  
 **Source system**  
 Select the source system associated with the InfoSource.  
  
 **Save & Activate**  
 Save and activate the new InfoSource.  
  
## InfoSource Transfer Structure Options  
 The InfoSource transfer structure lets you associate data flow columns to InfoSources.  
  
 **PipelineElement**  
 Displays the column in the output of the data flow that is connected to the SAP BW destination.  
  
 **PipelineDataType**  
 Displays the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] data type of the data flow column.  
  
 **Iobject \- Search**  
 Associate an existing InfoObject to the data flow column in the current row. To make this association, click **Search**, and then use the **Look Up InfoObject** dialog box to select the existing InfoObject. For more information about this dialog box, see [Look Up InfoObject](../../Topics\TopicNameNotContainA/Look-Up-InfoObject.md).  
  
 After you select an existing InfoObject, the component populates the **InfoObject** and **Type** columns with the selected values.  
  
 **Iobject \- New**  
 Create a new InfoObject and associate this new InfoObect to the data flow column in the current row. To create the new InfoObject, click **New**, and then use the **Create New InfoObject** dialog box to create the InfoObject. For more information about this dialog box, see [Create New InfoObject](../../Topics\TopicNameNotContainA/Create-New-InfoObject.md).  
  
 After you create a new InfoObject, the component populates the **InfoObject** and **Type** columns with the new values.  
  
 **Iobject \- Remove**  
 Remove the association between the InfoObject and the data flow column for the current row. To remove this association, click **Remove**.  
  
 **InfoObject**  
 Displays the name of the InfoObject that is associated with the data flow column.  
  
 **Type**  
 Displays the type of the InfoObject that is associated with the data flow column. The following table lists the possible values for the type.  
  
|Value|Description|  
|-----------|-----------------|  
|CHA|Characteristics|  
|UNI|Units|  
|KYF|Key figures|  
|TIM|Time characteristics|  
  
 **Unit Field**  
 Specify the units that the InfoObject will use.  
  
## See Also  
 [Create InfoSource](../../Topics\TopicNameNotContainA/Create-InfoSource.md)   
 [Microsoft Connector for SAP BW F1 Help](../../Topics\TopicNameNotContainA/Microsoft-Connector-for-SAP-BW-F1-Help.md)  
  
  