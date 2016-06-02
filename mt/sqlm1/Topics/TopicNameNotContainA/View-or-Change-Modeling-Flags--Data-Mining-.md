---
title: View or Change Modeling Flags (Data Mining)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
---
# View or Change Modeling Flags (Data Mining)
  Modeling flags are properties that you set on a mining structure column or mining model columns to control how the algorithm processes the data during analysis.  
  
 In Data Mining Designer, you can view and modify the modeling flags associated with a mining structure or mining column by viewing the properties of the structure or model. You can also set modeling flags by using DMX, AMO, or XMLA.  
  
 This procedure describes how to change the modeling flags in the designer.  
  
### View or change the modeling flag for a structure column or model column  
  
1.  In SQL Server Design Studio, open Solution Explorer, and then double\-click the mining structure.  
  
2.  To set the NOT NULL modeling flag, click the **Mining Structure** tab. To set the REGRESSOR or MODEL\_EXISTENCE\_ONLY flags, click the **Mining Model** tab.  
  
3.  Right\-click the column you want to view or change, and select **Properties**.  
  
4.  To add a new modeling flag, click the text box next to the **ModelingFlags** property, and select the check box or check boxes for the modeling flags you want to use.  
  
     Modeling flags are displayed only if they are appropriate for the column data type.  
  
    > [!NOTE]  
    >  After you change a modeling flag, you must reprocess the model.  
  
### Get the modeling flags used in the model  
  
-   In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], open a DMX Query window, and type a query like the following:  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## See Also  
 [Mining Model Tasks and How-tos](../../Topics\TopicNameNotContainA/Mining-Model-Tasks-and-How-tos.md)   
 [Modeling Flags &#40;Data Mining&#41;](../Topic/Modeling%20Flags%20\(Data%20Mining\).md)  
  
  