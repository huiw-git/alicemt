---
title: SQL Server mobile reports: End-to-end walk-through
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e198575e-b154-4342-b944-2bf19ec49bfd
---
# SQL Server mobile reports: End-to-end walk-through
WIth the combination of the [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Long.md)], the Reporting Services web portal, and the Power BI mobile apps for iOS, you can quickly create mobile reports that scale well to any screen size, on a design surface with adjustable grid rows and columns, and flexible mobile report elements. You can connect to a variety of on-premises data sources, or upload Excel workbooks to create mobile reports. Then save them to a [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal and view them in a browser, or in the Power BI for iOS mobile app on an iPhone or iPad.  
  
This article walks you through:   
  
- Creating a shared data source and dataset on the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal, using the AdventureWorks database as a sample data source.  
- Creating  a SQL Server mobile report in the [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)]  
- Publishing the mobile report to the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal.  
- Viewing the mobile report in the Power BI for iOS mobile app.  
  
## Before we start  
If you plan to follow along, these are the products you need.  
  
* To create data sources and KPIs, and publish datasets and mobile reports, you need access to a [SQL Server 2016 CTP 3.2 Reporting Services report server in native mode](https://msdn.microsoft.com/library/ms143711.aspx).  
* To [create shared datasets](#shared-dataset), you need to [install Report Builder](http://www.microsoft.com/download/details.aspx?id=50016).  
* To create mobile reports, [install the SQL Server Mobile Report Publisher](http://go.microsoft.com/fwlink/?LinkId=717766).  
* To view your reports on an iOS device, [download the Power BI for iOS mobile app](http://go.microsoft.com/fwlink/?LinkId=522062) to either your iPad or iPhone.  
* If you'd like to follow along, you can download [AdventureWorks Sample Databases and Scripts for SQL Server 2016 CTP3](https://www.microsoft.com/download/details.aspx?id=49502).  
  
  
## Create a data source  
  
You can create a data source for your mobile reports from any of the data sources Reporting Services supports. See the [list of supported data sources](https://msdn.microsoft.com/library/ms159219.aspx).  
  
1. From your [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal, click **New** > **Data Source**.  
  
   ![PBI_SSMRP_NewMenu](../../Images\Image\ImageNotContaina/PBI_SSMRP_NewMenu.png)  
  
3. Click the link to switch screens.  
  
   ![PBI_SSMRP_ComingSoon](../../Images\Image\ImageNotContaina/PBI_SSMRP_ComingSoon.png)  
     
4.  Enter your data source information > **OK**.  
  
    ![PBI_SSMRP_NewDataSource](../../Images\Image\ImageNotContaina/PBI_SSMRP_NewDataSource.png)  
  
    By default, in the portal, data sources aren't displayed.    
   
5. To view data sources, click **Display** > **Data Source**.  
  
   ![PBI_SSMRP_DisplayDataSources](../../Images\Image\ImageNotContaina/PBI_SSMRP_DisplayDataSources.png)  
   
6. Now you see the data source in the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] portal.  
  
   ![PBI_SSMRP_PortlDataSource](../../Images\Image\ImageNotContaina/PBI_SSMRP_PortlDataSource.png)  
  
Read more about [shared data sources in Reporting Services](https://msdn.microsoft.com/library/ms155845.aspx).  
   
## <a name="shared-dataset">Create a shared dataset</a>  
  
Use an existing [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] client tool to create the shared dataset.  This walkthrough uses the new [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRBnoversion.md)]. [Install Report Builder](http://www.microsoft.com/download/details.aspx?id=50016).   
  
 Create three datasets, one each for: the KPI value, the KPI trend, and one with more fields for the SQL Server mobile report.   
  
1. Open [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRBnoversion.md)] and click **New Dataset**.  
  
   ![PBI_SSMRP_RBNewDataset](../../Images\Image\ImageNotContaina/PBI_SSMRP_RBNewDataset.png)  
   
3. Click **Browse other data sources**.  
   
4. In the Name field, type the name of the server where you saved your data source, in this format:   
   
   Name: http://localhost/ReportServer  
   Items of type: Data Sources (*.rsds)  
   
5. Click **Open**, and navigate to the data source you created on that server.  
   
6. Select your data source and click **Open** again.    
  
7. Design  your dataset in [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRBnoversion.md)].  
  
   ![PBI_SSMRP_RB_QueryDesignr600](../../Images\Image\ImageNotContaina/PBI_SSMRP_RB_QueryDesignr600.png)  
   
8. When complete, save the dataset to the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRS.md)] report server.    
   
Now you can use the dataset as the basis for your KPIs and mobile reports.  You can create multiple datasets against the same data source. And you can create multiple KPIs and mobile reports against these shared datasets.   
  
## <a name="create-KPI">Create a KPI</a>  
You create KPIs right on the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal.    
  
1. In the upper-right corner of the web portal, click **New** > **New KPI**.   
  
   ![PBI_SSMRP_NewMenu](../../Images\Image\ImageNotContaina/PBI_SSMRP_NewMenu.png)  
      
   In the KPI creation screen, you can manually enter values, or to use a shared dataset.    
2. Change **Value** from **Set manually** to **Dataset field**.  
   
   ![PBI_SSMRP_KPI_DatasetField](../../Images\Image\ImageNotContaina/PBI_SSMRP_KPI_DatasetField.png)  
   
3. Click the ellipsis (**...**) in the **Pick dataset field** box, and select the dataset from the previous step.  
   
   ![PBI_SSMRP_KPIPickDataset](../../Images\Image\ImageNotContaina/PBI_SSMRP_KPIPickDataset.png)  
   
4. Choose the value from the result in the dataset.    
   
   ![PBI_SSMRP_KPIPickField](../../Images\Image\ImageNotContaina/PBI_SSMRP_KPIPickField.png)  
   
   > **Note**: For the Value, Goal and Status fields, you can only choose the result returned in the first row of the results.  For the trend set, you can choose the column that accurately reflects the values that reflect the trend set.  
   
5. In the **Trend set** box, click **Dataset trend**.  
  
6. In the **Pick dataset trend** box, click the ellipsis (**...**)  
  
   ![PBI_SSMRP_KPIPickTrend](../../Images\Image\ImageNotContaina/PBI_SSMRP_KPIPickTrend.png)  
  
7. Select a field and click **OK**.  
  
8. Give your KPI a name and pick a visualization type, and click **Create**.   
  
   The KPI appears on the [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal.  
   
 ![PBI_SSMRP_NewKPI](../../Images\Image\ImageNotContaina/PBI_SSMRP_NewKPI.png)  
    
## <a name="create-mobile-report">Create a SQL Server mobile report</a>  
   
To create a SQL Server mobile report, [install the SQL Server Mobile Report Publisher](http://go.microsoft.com/fwlink/?LinkId=717766). When you first open the [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)], you see a blank canvas where you can create your mobile report. You can start by creating visuals first, or start with your data.    
   
If you create the visuals first, [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)] automatically generates simulated data that is tied to the report and changes dynamically as you change your visual selections. Try this yourself.   
  
### Start with the visuals  
  
1. Open [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)]. This is the master layout grid.  
  
2. On the **Layout** tab, scroll down to the Charts section.  
  
   ![PBI_SSMRP_LayoutTabCharts2](../../Images\Image\ImageNotContaina/PBI_SSMRP_LayoutTabCharts2.png)  
  
2. Drag the **Tree Map** to the grid, and drag the lower-right corner to make it three columns wide and three rows high.  
  
   ![PBI_SSMRP_TreeMap](../../Images\Image\ImageNotContaina/PBI_SSMRP_TreeMap.png)  
  
3. You can see its visual properties at the bottom. You may have to scroll sideways to see them all.   
  
   ![PBI_SSMRP_TreeMapVisProps](../../Images\Image\ImageNotContaina/PBI_SSMRP_TreeMapVisProps.png)  
  
4. With the tree map visual selected, select the **Data** tab in the upper-left corner.   
  
   Now you can see the simulated fields and values that [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)] has generated, and see what size and color represent in the tree map.  
  
   ![PBI_SSMRP_TreeMapDataProps](../../Images\Image\ImageNotContaina/PBI_SSMRP_TreeMapDataProps.png)  
  
6. Click the **Layout** tab.  
  
7. Click the Options cog ![PBI_SSMRP_Cog](../../Images\Image\ImageNotContaina/PBI_SSMRP_Cog.png) in the upper-right corner of the tree map to see the menu it contains.   
  
   ![PBI_SSMRP_OptionsWheel](../../Images\Image\ImageNotContaina/PBI_SSMRP_OptionsWheel.png)  
  
8. Click the arrow in the middle of the wheel to close it.  
  
### Add your own data  
  
1. Switch to the **Data** tab.    
   
2. To add your own data, click **Add Data** in the upper-right corner, and navigate to your data.    
  
3. Add data from a local Excel workbook or a shared dataset on your [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal. You see a "Server added" message.  
  
4. Select the server, then select the dataset you created.  
   
   *    You can change the data that your visuals are connected to.   
   
3. When you return to the canvas, you see the visuals have been updated with your data.  
   
### Create a mobile report for phones  
  
Now that you've created visuals on the master layout, you can create a mobile report with a layout specifically optimized for your phone users.    
  
1. In the upper-right corner, click the canvas icon > **Phone**.  
  
2. On the Layout tab under **Control Instances**, you see the two charts you've created.   
  
3. Drag the tree map to the phone canvas and make it four columns wide and three rows high.  
  
   
### Save your mobile report  
You can save your report locally or to a [!INCLUDE[PRODUCT_NAME](../../Token\Other/ssRSnoversion.md)] web portal. If you save it locally, [!INCLUDE[PRODUCT_NAME](../../Token\Other/SS_MobileReptPub_Short.md)] saves it with cached data, so you can open it and continue working on it. But you can't view it on a mobile device.   
  
1. Click the save icon in the upper-left corner.   
   
2. To share it with others, click **Save to Server**.  
  
3. On the server, browse to the folder where you want to save your mobile report.  
  
4. Click **Choose Folder** > **Save**.  
  
  You get a message confirming the report is saved.  
    
  After you save, you can return to the portal and see your mobile report thumbnail.   
    
5. Tap the thumbnail to see the report.  
  
## Connect to a server to view SQL Server mobile reports   
  
If you don't have the app yet, [download the Power BI for iOS mobile app](http://go.microsoft.com/fwlink/?LinkId=522062) to either your iPad or iPhone.  
  
Sign in to Power BI from your iPad.  
  
1.  In the iPad, open the Power BI app.  
    
2.  To view your SQL Server mobile reports and KPIs, tap **Reporting Services**.  
![PBI_iPad_GetStartedSm](../../Images\Image\ImageNotContaina/PBI_iPad_GetStartedSm.png)  
  
3. Tap the options icon ![PBI_iPad_OptionsIcon](../../Images\Image\ImageNotContaina/PBI_iPad_OptionsIcon.png) in the upper-left corner, and tap **Connect**.  
  
   ![PBI_iPad_SSMRP_ConnectCrop](../../Images\Image\ImageNotContaina/PBI_iPad_SSMRP_ConnectCrop.png)  
  
4. Give the server a name, and fill in the server address and your email address and password, in this format:  
  
   ![PBI_iPad_SSMRP_ConnectContoso](../../Images\Image\ImageNotContaina/PBI_iPad_SSMRP_ConnectContoso.png)   
  
5.  Now you see the server in the left navigation bar.  
  
    ![PBI_iPad_SSMRP_LeftNavBiggr](../../Images\Image\ImageNotContaina/PBI_iPad_SSMRP_LeftNavBiggr.png)  
      
>**Tip**: Tap the options icon ![PBI_iPad_OptionsIcon](../../Images\Image\ImageNotContaina/PBI_iPad_OptionsIcon.png) anytime to go between your SQL Server mobile reports in the Reporting Services web portal and your dashboards in the Power BI service.   
  
## View KPIs and mobile reports in the Power BI app  
  
Tap the **KPIs** or **Mobile Reports** tab.   
  
![PBI_iPad_SSMRP_Portal](../../Images\Image\ImageNotContaina/PBI_iPad_SSMRP_Portal.png)  
  
- Tap a KPI to see it in focus mode.  
  
    ![PBI_iPad_SSMRP_Tile](../../Images\Image\ImageNotContaina/PBI_iPad_SSMRP_Tile.png)  
  
- Tap a mobile report to open and interact with it in the Power BI app.  
  
The KPIs and mobile reports are displayed in the same folders they're in on the Reporting Services web portal.   
  
### See also  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher](Create%20and%20publish%20mobile%20reports%20with%20SQL%20Server%20Mobile%20Report%20Publisher.md)   
-  View [SQL Server mobile reports and KPIs in the iPad app](https://pbiwebprod-docs.azurewebsites.net/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI for iOS)  
-  View [SQL Server mobile reports and KPIs in the iPhone app](https://pbiwebprod-docs.azurewebsites.net/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI for iOS)  
  
   
