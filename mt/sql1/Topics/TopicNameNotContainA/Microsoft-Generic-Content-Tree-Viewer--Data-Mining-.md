---
title: "Microsoft Generic Content Tree Viewer (Data Mining)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
caps.latest.revision: 38
caps.handback.revision: 0
manager: jhubbard
---
# Microsoft Generic Content Tree Viewer (Data Mining)
The **Microsoft Generic Content Tree Viewer** displays detailed information about the contents of a data mining mode in a standardized HTML table format. This view is useful because it exposes the underlying structure of the model, as well details about coefficients, the distribution of values, and much more.  
  
 The actual content displayed in the table varies depending on the algorithm that was used and might include columns, rules, properties, attributes, nodes, and formulas. For more information about model content, and how to interpret the information for each model type, see [Mining Model Content (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Model-Content--Analysis-Services---Data-Mining-.md).  
  
 The information that is displayed in the viewer uses a common structure that is based on the content schema rowset for mining models. The content schema rowset is a generic framework for storing patterns, statistics, and other contents of a data mining model. For a list of the columns in the data mining schema rowset for mining models, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](assetId:///1e85d9e7-3b74-42ac-b94e-f52f76d8a25d).  
  
## Options  
 **Node caption (Unique ID)**  
 This pane displays a list of all the nodes in the selected mining model. The way the nodes are arranged in the tree is different depending on the type of model you are viewing.  
  
 You can click each node to display details about the node in the **Node details** pane.  
  
 **Node details**  
 Displays detailed information about the content of the selected node. Each node stores its information in a standardized format, but the contents and significance of each line of the table depends on the type of model or type of node that you are viewing. For example, the information stored for a node that represents a rule in an association model contains different information than a node that represents a tree in a decision trees model.  
  
 For information about how to interpret the node information for a specific model type, see [Mining Model Content (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Model-Content--Analysis-Services---Data-Mining-.md).  
  
## See Also  
 [Data Mining Algorithms (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Algorithms--Analysis-Services---Data-Mining-.md)   
 [Mining Model Viewers (Data Mining Model Designer)](../../Topics/TopicNameNotContainA/Mining-Model-Viewers--Data-Mining-Model-Designer-.md)   
 [Data Mining Queries](../../Topics/TopicNameNotContainA/Data-Mining-Queries.md)