---
title: Design first or data first when creating in Reporting Services mobile reports
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7b355fa-312b-4074-bc9b-776269d4fb51
---
# Design first or data first when creating in Reporting Services mobile reports
  
With [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Long.md)], you can quickly create mobile reports that scale well to any screen size, on a design surface with adjustable grid rows and columns, and flexible mobile report elements.   
  
When creating mobile reports, you have your choice of two basic approaches: start with the data first, or start with the design first. [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Short.md)] supports both.   
  
## Design first  
  
The following diagram shows the components of the [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Short.md)] layout view:   
  
![SS_MRP_LayoutTab](../../Images\Image\ImageNotContaina/SS_MRP_LayoutTab.png)  
  
In the design-first approach, you create a mobile report layout first without importing any data. This is a good way to create a mobile report when you are not sure if the data is formatted correctly. Without real data, gallery elements are automatically bound to generated simulated data, which you can export and use as a template to describe the required data.  
  
## Data first  
The data-first approach is to import all required data first, then design the mobile report and set data properties on the mobile report elements. This has the advantage of being able to connect each element to real data when you add it to the layout. When using a data-first approach, be sure that your real data is formatted correctly for use with [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Short.md)].   
  
 The following diagram shows all the components of the [!INCLUDE[SS_MobileReptPub_Long](../../Token\Other/SS_MobileReptPub_Short.md)] data view:  
  
![SS_MRP_DataTab](../../Images\Image\ImageNotContaina/SS_MRP_DataTab.png)  
  
### See also  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher](../../Topics\TopicNameNotContainA/Create-mobile-reports-with-SQL-Server-Mobile-Report-Publisher.md)  
-  View [SQL Server mobile reports and KPIs in the iPad app](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI for iOS)  
-  View [SQL Server mobile reports and KPIs in the iPhone app](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI for iOS)  
  
  
  
  
