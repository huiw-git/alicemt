---
title: "Estimate the Size of a Table"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 31
manager: jhubbard
---
# Estimate the Size of a Table
You can use the following steps to estimate the amount of space required to store data in a table:  
  
1.  Calculate the space required for the heap or clustered index following the instructions in [Estimate the Size of a Heap](../../Topics/TopicNameContainA/Estimate-the-Size-of-a-Heap.md) or [Estimate the Size of a Clustered Index](../../Topics/TopicNameContainA/Estimate-the-Size-of-a-Clustered-Index.md).  
  
2.  For each nonclustered index, calculate the space required for it by following the instructions in [Estimate the Size of a Nonclustered Index](../../Topics/TopicNameContainA/Estimate-the-Size-of-a-Nonclustered-Index.md).  
  
3.  Add the values calculated in steps 1 and 2.  
  
## See Also  
 [Estimate the Size of a Database](../../Topics/TopicNameContainA/Estimate-the-Size-of-a-Database.md)   
 [Estimate the Size of a Heap](../../Topics/TopicNameContainA/Estimate-the-Size-of-a-Heap.md)   
 [Estimate the Size of a Clustered Index](../../Topics/TopicNameContainA/Estimate-the-Size-of-a-Clustered-Index.md)   
 [Estimate the Size of a Nonclustered Index](../../Topics/TopicNameContainA/Estimate-the-Size-of-a-Nonclustered-Index.md)