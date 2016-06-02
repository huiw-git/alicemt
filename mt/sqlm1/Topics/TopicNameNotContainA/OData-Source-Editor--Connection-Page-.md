---
title: OData Source Editor (Connection Page)
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
---
# OData Source Editor (Connection Page)
  Use the **Connection** page of the **OData Source Editor** dialog box to select the OData connection manager for the OData source. This page also lets you specify a collection or a resource path and any query options to indicate what data needs to be retrieved from the OData source. To learn more about the OData source, see [OData Source](../../Topics\TopicNameNotContainA/OData-Source.md).  
  
## Static Options  
 **OData connection manager**  
 Select an existing connection manager from the list, or create a new connection by clicking **New**.  
  
 After you select or create a connection manager, the dialog box displays the OData protocol version that the connection manager is using.  
  
 **New**  
 Create a new connection manager by using the **OData Connection Manager Editor** dialog box.  
  
 **Use collection or resource path**  
 Specify the method for selecting data from the source.  
  
|Option|Description|  
|------------|-----------------|  
|Collection|Retrieve data from the OData source by using a collection name.|  
|Resource Path|Retrieve data from the OData source by using a resource path.|  
  
 **Query options**  
 Specify options for the query.  For example: $top\=5  
  
 **Feed url**  
 Displays the read\-only Feed URL based on options you selected on this dialog box.  
  
 **Preview**  
 Preview results by using the **Preview** dialog box. **Preview** can display up to 20 rows.  
  
## Dynamic Options  
  
### Use collection or resource path \= Collection  
 **Collection**  
 Select a collection from the drop\-down list.  
  
### Use collection or resource path \= Resource Path  
 **Resource path**  
 Type a resource path. For example: Employees  
  
## See Also  
 [OData Source Editor &#40;Columns Page&#41;](../Topic/OData%20Source%20Editor%20\(Columns%20Page\).md)   
 [OData Source Editor &#40;Error Output Page&#41;](../Topic/OData%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [OData Connection Manager](../../Topics\TopicNameNotContainA/OData-Connection-Manager.md)  
  
  