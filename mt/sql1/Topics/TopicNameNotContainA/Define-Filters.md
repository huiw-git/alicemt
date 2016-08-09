---
title: "Define Filters"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: 19
manager: jhubbard
---
# Define Filters
The **Define Filters** dialog box allows you to define filters that you then apply to data conflicts to see a subset of the conflicts in the grid. To define a filter, choose an operator from the **Operator** drop-down list box and then enter a value. For example, to show only those conflicts in which the conflict loser is server **ReplTest1**, select **Equal to** from the **Operator** drop-down list box and enter **ReplTest1** in the first **Value** column.  
  
## Options  
 **Operator**  
 Select an operator for the filter, such as **Less than or Equal to**.  
  
 **Value**  
 Enter a value for the filter. Most operators only require a value in the first **Value** column, but the **Between** and **Not Between** operators require a value in both of the **Value** columns.  
  
 **Clear**  
 Click this button to clear all filters that have been previously defined.  
  
## See Also  
 [Microsoft Replication Conflict Viewer (Merge Replication)](../../Topics/TopicNameNotContainA/Microsoft-Replication-Conflict-Viewer--Merge-Replication-.md)   
 [Microsoft Replication Conflict Viewer (Transactional Replication)](../../Topics/TopicNameNotContainA/Microsoft-Replication-Conflict-Viewer--Transactional-Replication-.md)