---
title: Get data from shared datasets in Reporting Services mobile reports
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b846451-c8d0-412c-802d-a42bb1ff8c63
---
# Get data from shared datasets in Reporting Services mobile reports
Besides [loading data from Excel files](../../Topics\TopicNameNotContainA/Prepare-Excel-data-for-Reporting-Services-mobile-reports.md), [!INCLUDE[PRODUCT_NAME](../../Token\Other/PRODUCT_NAME.md)] can also access data from almost any source. Accessing data requires a shared data source, configured on a [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] [!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)]. Read more about [creating shared data sources](../../Topics\TopicNameNotContainA/Create,-Modify,-and-Delete-Shared-Data-Sources--SSRS-.md) and [creating shared datasets](../../Topics\TopicNameNotContainA/Manage-Shared-Datasets.md).  
  
After shared data sources and shared datasets are configured on the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] server, you can use them in mobile reports you create in [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)].   
  
After you've connected to a [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] server from the [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)], connecting a mobile report to a shared dataset is straightforward.   
  
1. On the **Data** tab, select **Add Data**.  
  
2. Select **Report Server**.   
  
3.  If this is the first time connecting to the server, fill in the server name and your name and password. Put the server name in the Server address box in this format:  
  
    <"servername">/reports/  
  
    As in this example:  
       
    ![SSMRP_ConnectToServer](../../Images\Image\ImageNotContaina/SSMRP_ConnectToServer.png)  
      
  
4. When you select the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] server, you see the available datasets in folders. Select a dataset to import the data into [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)].  
  
   ![SS_MRP_ServerData](../../Images\Image\ImageNotContaina/SS_MRP_ServerData.png)  
  
After you've imported the dataset, you can design your mobile report just as you would with simulated data, or local data from an Excel file.  
  
By default, the shared dataset is always up to date with the latest data, because every time someone views a mobile report based on that dataset, SQL Server runs the underlying query and returns the latest data. Clearly, if lots of people view your mobile report this might not be ideal, so you can set up caching to run the query periodically and cache the resulting dataset. This blog post explains [how caching and data refresh works in the web portal](http://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/).  
  
## Add, edit, or remove a report server  
  
If you're already connected to a report server, when you select **Add Data** on the Data tab, you don't see an option to add another report server. Follow these steps instead.  
  
1. In the upper-left corner, select **Connections**.  
  
   ![SSMRP_AddConnectionIcon](../../Images\Image\ImageNotContaina/SSMRP_AddConnectionIcon.png)  
     
   The Server Connection pane opens on the right.  
     
   ![SSMRP_ServerConnectnPane](../../Images\Image\ImageNotContaina/SSMRP_ServerConnectnPane.png)  
     
2. Add a new server connection, or edit or remove existing connections.  
  
### See also  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher](../../Topics\TopicNameNotContainA/Create-mobile-reports-with-SQL-Server-Mobile-Report-Publisher.md)  
-  [Reporting Services web portal](../../Topics\TopicNameNotContainA/Web-portal--SSRS-Native-Mode-.md)  
-  View [SQL Server mobile reports and KPIs in the iPad app](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI for iOS)  
-  View [SQL Server mobile reports and KPIs in the iPhone app](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI for iOS)  
  
  
  
  
