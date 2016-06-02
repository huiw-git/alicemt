---
title: Integration Services Transformations
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c70c4f6e-82dd-4948-b923-fd5193f67f7e
---
# Integration Services Transformations
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] transformations are the components in the data flow of a package that aggregate, merge, distribute, and modify data. Transformations can also perform lookup operations and generate sample datasets. This section describes the transformations that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes and explains how they work.  
  
## Business Intelligence Transformations  
 The following transformations perform business intelligence operations such as cleaning data, mining text, and running data mining prediction queries.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Slowly Changing Dimension Transformation](../../Topics\TopicNameNotContainA/Slowly-Changing-Dimension-Transformation.md)|The transformation that configures the updating of a slowly changing dimension.|  
|[Fuzzy Grouping Transformation](../../Topics\TopicNameNotContainA/Fuzzy-Grouping-Transformation.md)|The transformation that standardizes values in column data.|  
|[Fuzzy Lookup Transformation](../../Topics\TopicNameNotContainA/Fuzzy-Lookup-Transformation.md)|The transformation that looks up values in a reference table using a fuzzy match.|  
|[Term Extraction Transformation](../../Topics\TopicNameNotContainA/Term-Extraction-Transformation.md)|The transformation that extracts terms from text.|  
|[Term Lookup Transformation](../../Topics\TopicNameNotContainA/Term-Lookup-Transformation.md)|The transformation that looks up terms in a reference table and counts terms extracted from text.|  
|[Data Mining Query Transformation](../../Topics\TopicNameNotContainA/Data-Mining-Query-Transformation.md)|The transformation that runs data mining prediction queries.|  
|[DQS Cleansing Transformation](../../Topics\TopicNameNotContainA/DQS-Cleansing-Transformation.md)|The transformation that corrects data from a connected data source by applying rules that were created for the data source.|  
  
## Row Transformations  
 The following transformations update column values and create new columns. The transformation is applied to each row in the transformation input.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Character Map Transformation](../../Topics\TopicNameNotContainA/Character-Map-Transformation.md)|The transformation that applies string functions to character data.|  
|[Copy Column Transformation](../../Topics\TopicNameNotContainA/Copy-Column-Transformation.md)|The transformation that adds copies of input columns to the transformation output.|  
|[Data Conversion Transformation](../../Topics\TopicNameNotContainA/Data-Conversion-Transformation.md)|The transformation that converts the data type of a column to a different data type.|  
|[Derived Column Transformation](../../Topics\TopicNameNotContainA/Derived-Column-Transformation.md)|The transformation that populates columns with the results of expressions.|  
|[Export Column Transformation](../../Topics\TopicNameNotContainA/Export-Column-Transformation.md)|The transformation that inserts data from a data flow into a file.|  
|[Import Column Transformation](../../Topics\TopicNameNotContainA/Import-Column-Transformation.md)|The transformation that reads data from a file and adds it to a data flow.|  
|[Script Component](../../Topics\TopicNameNotContainA/Script-Component.md)|The transformation that uses script to extract, transform, or load data.|  
|[OLE DB Command Transformation](../../Topics\TopicNameNotContainA/OLE-DB-Command-Transformation.md)|The transformation that runs SQL commands for each row in a data flow.|  
  
## Rowset Transformations  
 The following transformations create new rowsets. The rowset can include aggregate and sorted values, sample rowsets, or pivoted and unpivoted rowsets.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Aggregate Transformation](../../Topics\TopicNameNotContainA/Aggregate-Transformation.md)|The transformation that performs aggregations such as AVERAGE, SUM, and COUNT.|  
|[Sort Transformation](../../Topics\TopicNameNotContainA/Sort-Transformation.md)|The transformation that sorts data.|  
|[Percentage Sampling Transformation](../../Topics\TopicNameNotContainA/Percentage-Sampling-Transformation.md)|The transformation that creates a sample data set using a percentage to specify the sample size.|  
|[Row Sampling Transformation](../../Topics\TopicNameNotContainA/Row-Sampling-Transformation.md)|The transformation that creates a sample data set by specifying the number of rows in the sample.|  
|[Pivot Transformation](../../Topics\TopicNameNotContainA/Pivot-Transformation.md)|The transformation that creates a less normalized version of a normalized table.|  
|[Unpivot Transformation](../../Topics\TopicNameNotContainA/Unpivot-Transformation.md)|The transformation that creates a more normalized version of a nonnormalized table.|  
  
## Split and Join Transformations  
 The following transformations distribute rows to different outputs, create copies of the transformation inputs, join multiple inputs into one output, and perform lookup operations.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Conditional Split Transformation](../../Topics\TopicNameNotContainA/Conditional-Split-Transformation.md)|The transformation that routes data rows to different outputs.|  
|[Multicast Transformation](../../Topics\TopicNameNotContainA/Multicast-Transformation.md)|The transformation that distributes data sets to multiple outputs.|  
|[Union All Transformation](../../Topics\TopicNameNotContainA/Union-All-Transformation.md)|The transformation that merges multiple data sets.|  
|[Merge Transformation](../../Topics\TopicNameNotContainA/Merge-Transformation.md)|The transformation that merges two sorted data sets.|  
|[Merge Join Transformation](../../Topics\TopicNameNotContainA/Merge-Join-Transformation.md)|The transformation that joins two data sets using a FULL, LEFT, or INNER join.|  
|[Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md)|The transformation that looks up values in a reference table using an exact match.|  
|[Cache Transform](../../Topics\TopicNameNotContainA/Cache-Transform.md)|The transformation that writes data from a connected data source in the data flow to a Cache connection manager that saves the data to a cache file. The Lookup transformation performs lookups on the data in the cache file.|  
|[Balanced Data Distributor Transformation](../../Topics\TopicNameNotContainA/Balanced-Data-Distributor-Transformation.md)|The transformation distributes buffers of incoming rows uniformly across outputs on separate threads to improve performance of SSIS packages running on multi\-core and multi\-processor servers.|  
  
## Auditing Transformations  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes the following transformations to add audit information and count rows.  
  
|Transformation|Description|  
|--------------------|-----------------|  
|[Audit Transformation](../../Topics\TopicNameNotContainA/Audit-Transformation.md)|The transformation that makes information about the environment available to the data flow in a package.|  
|[Row Count Transformation](../../Topics\TopicNameNotContainA/Row-Count-Transformation.md)|The transformation that counts rows as they move through it and stores the final count in a variable.|  
  
## Custom Transformations  
 You can also write custom transformations. For more information, see [Developing a Custom Transformation Component with Synchronous Outputs](../Topic/Developing%20a%20Custom%20Transformation%20Component%20with%20Synchronous%20Outputs.md) and [Developing a Custom Transformation Component with Asynchronous Outputs](../Topic/Developing%20a%20Custom%20Transformation%20Component%20with%20Asynchronous%20Outputs.md).  
  
  