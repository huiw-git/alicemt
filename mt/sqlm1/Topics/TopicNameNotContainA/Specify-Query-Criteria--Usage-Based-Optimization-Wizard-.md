---
title: Specify Query Criteria (Usage-Based Optimization Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
---
# Specify Query Criteria (Usage-Based Optimization Wizard)
  Use the **Specify Query Criteria** page to choose one or more filter options in order to identify queries to optimize.  
  
> [!NOTE]  
>  This page is disabled if [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] cannot connect to the query log.  
  
## Options  
 **Query log statistics**  
 Displays information about the queries stored in the query log for the selected partitions. The following items are displayed:  
  
|Term|Definition|  
|----------|----------------|  
|**Total queries**|Displays the total number of queries stored in the query log for the selected partitions.|  
|**Distinct queries**|Displays the number of distinct queries stored in the query log for the selected partitions.|  
|**Distinct users**|Displays the total number of distinct users associated with queries stored in the query log for the selected partitions.|  
|**Average response time**|Displays the average response time for queries stored in the query log for the selected partitions.|  
  
 **Beginning date**  
 Filters queries in the query log based on a starting date and time. Choose or type a date in the dropdown list.  
  
> [!NOTE]  
>  If **Ending date** is not selected, all queries in the query log on or after the date and time specified for this option are considered.  
  
 **Ending date**  
 Filters queries in the query log based on an ending date and time. Choose or type a date in the dropdown list.  
  
> [!NOTE]  
>  If **Beginning date** is not selected, all queries in the query log on or before the date and time specified for this option are considered.  
  
 **Users**  
 Filters queries in the query log based on a specified set of users. Click the ellipsis \(**...**\) button to display the **User Selection** dialog box and choose users on which to filter queries. For more information about the **User Selection** dialog box, see [User Selection Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/User%20Selection%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
 **Most frequent queries**  
 Filters queries in the query log based on the topmost percentage of the distinct queries most often run for the selected partitions. Choose or type a percent value in the text box.  
  
## See Also  
 [Usage-Based Optimization Wizard F1 Help](../../Topics\TopicNameNotContainA/Usage-Based-Optimization-Wizard-F1-Help.md)   
 [Analysis Services Wizards &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Wizards%20\(Multidimensional%20Data\).md)  
  
  