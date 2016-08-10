---
title: "Set the Partition Slice Property (Analysis Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
caps.latest.revision: 34
caps.handback.revision: 0
manager: mblythe
---
# Set the Partition Slice Property (Analysis Services)
A data slice is an important optimization feature that helps direct queries to the data of the appropriate partitions. Explicitly setting the Slice property can improve query performance by overriding default slices generated for MOLAP and HOLAP partitions. Additionally, the Slice property provides an extra validation check when processing the partition.  
  
 You can specify a data slice after you create a partition, but before processing it, using the Slice property. On the Partitions tab, expand a measure group, right-click a partition, and select **Properties**.  
  
 For an explanation of data slice benefits, see [Set the Slice on your SSAS Cube Partition](http://go.microsoft.com/fwlink/?LinkId=317783).  
  
## Defining a Slice  
 Valid values for a slice property are an MDX member, set, or tuple. The following examples illustrate valid slice syntax:  
  
|Slice|Member, set or tuple|  
|-----------|--------------------------|  
|[Date].[Calendar].[Calendar Year].&[2010]|Specify this slice on a partition containing facts from year 2010 (assuming the model includes a Date dimension with Calendar Year hierarchy, where 2010 is a member). Although the partition source WHERE clause or table might already filter by 2010, specifying the Slice provides an additional check during processing, as well as more targeted scans during query execution.|  
|{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }|Specify this slice on a partition containing facts that include sales territory information. A slice can be an MDX set consisting of two or more members.|  
|[Measures].[Sales Amount Quota] > '5000'|This slice shows an MDX expression.|  
  
 A data slice of a partition should reflect, as closely as possible, the data in the partition. For example, if a partition is limited to 2012 data, the partition's data slice should specify the 2012 member of the Time dimension. It is not always possible to specify a data slice that reflects the exact contents of a partition. For example, if a partition contains data for only January and February, but the levels of the Time dimension are Year, Quarter, and Month, the Partition Wizard cannot select both the January and February members. In such cases, select the parent of the members that reflect the partition's contents. In this example, select Quarter 1.  
  
> [!NOTE]  
>  Note that dynamic MDX functions (such as [Generate (MDX)](assetId:///696a229d-c2f1-47b7-9dca-7b0a6b547d9b) or [Except (MDX)](assetId:///5d832c82-1e6d-4308-9c26-7edb8afe11dd)) are not supported in the Slice property for partitions. You must define the slice by using explicit tuples or member references.  
>   
>  For example, rather than using the range operator (:) to define a range, you would need to enumerate each member by the specific years.  
>   
>  If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script. Then, you can use either the ascmd command-line tool or the [Analysis Services Execute DDL Task](../../Topics/TopicNameNotContainA/Analysis-Services-Execute-DDL-Task.md) in Integration Services to run the script and create the specified set of members immediately before you process the partition.  
  
## See Also  
 [Create and Manage a Local Partition (Analysis Services)](../../Topics/TopicNameContainA/Create-and-Manage-a-Local-Partition--Analysis-Services-.md)