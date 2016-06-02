---
title: DQS Cleansing Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
---
# DQS Cleansing Transformation
  The DQS Cleansing transformation uses Data Quality Services \(DQS\) to correct data from a connected data source, by applying approved rules that were created for the connected data source or a similar data source. For more information about data correction rules, see [DQS Knowledge Bases and Domains](../../Topics\TopicNameNotContainA/DQS-Knowledge-Bases-and-Domains.md). For more information DQS, see [Data Quality Services Concepts](../../Topics\TopicNameNotContainA/Data-Quality-Services-Concepts.md).  
  
 To determine whether the data has to be corrected, the DQS Cleansing transformation processes data from an input column when the following conditions are true:  
  
-   The column is selected for data correction.  
  
-   The column data type is supported for data correction.  
  
-   The column is mapped a domain that has a compatible data type.  
  
 The transformation also includes an error output that you configure to handle row\-level errors. To configure the error output, use the **DQS Cleansing Transformation Editor**.  
  
 You can include the [Fuzzy Grouping Transformation](../../Topics\TopicNameNotContainA/Fuzzy-Grouping-Transformation.md) in the data flow to identify rows of data that are likely to be duplicates.  
  
## Data Quality Projects and Values  
 When you process data with the DQS Cleansing transformation, a cleansing project is created on the Data Quality Server. You use the Data Quality Client to manage the project. In addition, you can use the Data Quality Client to import the project values into a DQS knowledge base domain. You can import the values only to a domain \(or linked domain\) that the DQS Cleansing transformation was configured to use.  
  
## Related Tasks  
  
-   [Open Integration Services Projects in Data Quality Client](../../Topics\TopicNameNotContainA/Open-Integration-Services-Projects-in-Data-Quality-Client.md)  
  
-   [Import Cleansing Project Values into a Domain](../../Topics\TopicNameContainA/Import-Cleansing-Project-Values-into-a-Domain.md)  
  
-   [Apply Data Quality Rules to Data Source](../../Topics\TopicNameNotContainA/Apply-Data-Quality-Rules-to-Data-Source.md)  
  
## Related Content  
  
-   [Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project](../Topic/Manage%20\(Open,%20Unlock,%20Rename,%20and%20Delete\)%20a%20Data%20Quality%20Project.md)  
  
-   Article, [Cleansing complex data using composite domains](http://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx), on social.technet.microsoft.com.  
  
  