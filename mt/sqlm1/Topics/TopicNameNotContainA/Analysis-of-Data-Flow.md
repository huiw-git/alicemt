---
title: Analysis of Data Flow
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
---
# Analysis of Data Flow
  You can use the [catalog.execution_data_statistics](../Topic/catalog.execution_data_statistics.md)**SSISDB** database view to analyze the data flow of packages. This view displays a row each time a data flow component sends data to a downstream component. The information can be used to gain a deeper understanding of the rows that are sent to each component.  
  
> [!NOTE]  
>  The logging level must be set to **Verbose** in order to capture information with the catalog.execution\_data\_statistics view.  
  
 The following example displays the number of rows sent between components of a package.  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 The following example calculates the number of rows per millisecond sent by each component for a specific execution. The calculated values are:  
  
-   **total\_rows** \- the sum of all the rows sent by the component  
  
-   **wall\_clock\_time\_ms** – the total elapsed execution time, in milliseconds, for each component  
  
-   **num\_rows\_per\_millisecond** – the number of rows per millisecond sent by each component  
  
 The **HAVING** clause is used to prevent a divide\-by\-zero error in the calculations.  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## Related Tasks  
 [Debugging Data Flow](../../Topics\TopicNameNotContainA/Debugging-Data-Flow.md)  
  
 [Troubleshooting Tools for Package Execution](../../Topics\TopicNameNotContainA/Troubleshooting-Tools-for-Package-Execution.md)  
  
## See Also  
 [Data in Data Flows](../../Topics\TopicNameNotContainA/Data-in-Data-Flows.md)  
  
  