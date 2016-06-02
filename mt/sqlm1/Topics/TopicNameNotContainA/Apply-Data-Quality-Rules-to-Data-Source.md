---
title: Apply Data Quality Rules to Data Source
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
---
# Apply Data Quality Rules to Data Source
  You can use Data Quality Services \(DQS\) to correct data in the package data flow by connecting the DQS Cleansing transformation to the data source. For more information about DQS, see [Data Quality Services Concepts](../../Topics\TopicNameNotContainA/Data-Quality-Services-Concepts.md). For more information about the transformation, see [DQS Cleansing Transformation](../../Topics\TopicNameNotContainA/DQS-Cleansing-Transformation.md).  
  
 When you process data with the DQS Cleansing transformation, a data quality project is created on the Data Quality Server. You use the Data Quality Client to manage the project. For more information, see [Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project](../Topic/Manage%20\(Open,%20Unlock,%20Rename,%20and%20Delete\)%20a%20Data%20Quality%20Project.md).  
  
### To correct data in the data flow  
  
1.  Create a package.  
  
2.  Add and configure the DQS Cleansing transformation. For more information, see [DQS Cleansing Transformation Editor Dialog Box](../../Topics\TopicNameNotContainA/DQS-Cleansing-Transformation-Editor-Dialog-Box.md).  
  
3.  Connect the DQS Cleansing transformation to a data source.  
  
  