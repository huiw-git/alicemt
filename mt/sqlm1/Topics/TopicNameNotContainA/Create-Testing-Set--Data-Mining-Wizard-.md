---
title: Create Testing Set (Data Mining Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
---
# Create Testing Set (Data Mining Wizard)
  Use the **Create Testing Set** page to specify how much of the data is to be used for training, and how much is to be reserved for use as a test set. Separating data into a training and testing set when you create a mining structure makes it much easier to assess the accuracy of mining models that you create later.  
  
 You can specify the amount of testing data as a percentage, or you can specify a number to limit the number of cases used for testing. If you specify both a percentage and a maximum number of cases to use for testing, both settings are used, and the testing data set contains the smaller number of cases. By default, 30 percent of data is used for testing, 70 percent for training, and there is no maximum number of test cases.  
  
 By default, [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] generates a numeric seed that is used to start partitioning. This seed is based on the name of the mining structure. If you want to ensure that the partition stays the same even if the name of the mining structure is changed, you can specify a value for the seed, by setting the HoldoutSeed property of the mining structure. If you change the holdout seed, you must reprocess the structure.  
  
 If you later want to change the amount of testing or training data, you can modify the **HoldoutMaxCases** and **HoldoutMaxPercent** properties on the data mining structure by using the **Properties** window. However, after you make the change you must reprocess the mining structure and all associated mining models. The following limitations also apply:  
  
-   Partitioning of a data mining structure is supported only when the data mining structure is stored in [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]. Earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] do not support caching of partition information for mining structures.  
  
-   You cannot partition a mining structure if the mining structure contains a Key Time column, which is required for time series mining models.  
  
-   You cannot partition data if you are trying to predict a value that is stored in a nested table.  
  
 **For More Information:** [Testing and Validation &#40;Data Mining&#41;](../Topic/Testing%20and%20Validation%20\(Data%20Mining\).md), [Create a Relational Mining Structure](../../Topics\TopicNameContainA/Create-a-Relational-Mining-Structure.md), [Basic Data Mining Tutorial](../Topic/Basic%20Data%20Mining%20Tutorial.md)  
  
## Options  
 **Percentage of data for testing**  
 Click the up and down arrows to increase or decrease the percentage of data to use as a training set, or type a value between 0 and 100 in the text box.  
  
 **Maximum number of cases in testing data set**  
 Type a number to limit the number of cases that can be used for testing.  
  
 If you specify a number that is larger than the number of actual cases in the data, all the cases will be used.  
  
 The default is NULL. This means there is no limit.  
  
## See Also  
 [Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Suggest Related Columns &#40;Data Mining Wizard&#41;](../Topic/Suggest%20Related%20Columns%20\(Data%20Mining%20Wizard\).md)   
 [Specify Table Types &#40;Data Mining Wizard&#41;](../Topic/Specify%20Table%20Types%20\(Data%20Mining%20Wizard\).md)   
 [Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;](../Topic/Specify%20the%20Column's%20Content%20and%20Data%20Type%20\(Data%20Mining%20Wizard\).md)  
  
  