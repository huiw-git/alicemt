---
title: OData Source
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
---
# OData Source
  Use the OData Source component in an SSIS package to consume data from an Open Data Protocol \(OData\) service. The component supports the OData v3 and v4 protocols.  
  
-   For OData V3 protocol, the component supports the ATOM and JSON data formats .  
  
-   For OData V4 protocol, the component supports the JSON data format .  
  
> [!NOTE]  
>  You can also use the OData Source to read from SharePoint lists. To see all the lists on a SharePoint server, use the following URL: http:\/\/\<server\>\/\_vti\_bin\/ListData.svc. For more information about SharePoint URL conventions, see [SharePoint Foundation REST Interface](http://msdn.microsoft.com/library/ff521587.aspx).  
  
## OData Format  
 Most OData services return results in multiple formats. You can specify the format of the result set by using the $format query option. Formats such as JSON and JSON Light are more efficient than ATOM or XML, and may give you better performance when transferring large amounts of data. The following table provides results from sample tests. As you can see, there was a 30\-53% performance gain when switching from ATOM to JSON and a 67% performance gain when switching from ATOM to the new JSON light format \(available in WCF Data Services 5.1\).  
  
|||||  
|-|-|-|-|  
|Rows|ATOM|JSON|JSON \(Light\)|  
|10000|113 seconds|74 seconds|68 seconds|  
|1000000|1110 seconds|853 seconds|665 seconds|  
  
> [!NOTE]  
>  The SSIS OData Source uses 5.6.1 to parse OData V3 feeds and ODataLib 6.12.0 to parse OData V4 feeds.  
  
## In This Section  
  
-   [Tutorial: Using the OData Source](../Topic/Tutorial:%20Using%20the%20OData%20Source.md)  
  
-   [Modify OData Source Query at Runtime](../../Topics\TopicNameNotContainA/Modify-OData-Source-Query-at-Runtime.md)  
  
-   [OData Source Editor &#40;Connection Page&#41;](../Topic/OData%20Source%20Editor%20\(Connection%20Page\).md)  
  
-   [OData Source Editor &#40;Columns Page&#41;](../Topic/OData%20Source%20Editor%20\(Columns%20Page\).md)  
  
-   [OData Source Editor &#40;Error Output Page&#41;](../Topic/OData%20Source%20Editor%20\(Error%20Output%20Page\).md)  
  
-   [OData Source Properties](../../Topics\TopicNameNotContainA/OData-Source-Properties.md)  
  
## See Also  
 [OData Connection Manager](../../Topics\TopicNameNotContainA/OData-Connection-Manager.md)  
  
  