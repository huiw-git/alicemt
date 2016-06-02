---
title: Add visualizations to Reporting Services mobile reports
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b220b74-9ecd-4084-93fb-545208d5d7a2
robots: noindex,nofollow
---
# Add visualizations to Reporting Services mobile reports
Charts are an essential part of data visualization. Learn about the variety of charts that [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] mobile reports offer to cover a range of scenarios. 

[!INCLUDE[SS_MobileReptPub_Short](../../Token\Other/SS_MobileReptPub_Long.md)] has three basic chart types: time, category, and totals. These three chart types have corresponding comparison charts, which are useful for comparing two distinct sets of series.  

## Shared chart properties

Some properties apply to all charts, and others only to specific charts. Here are some of the shared properties.

### Number format
You can assign a variety of formats to numbers in a chart in [!INCLUDE[SS_MobileReptPub_Short](../../Token\Other/SS_MobileReptPub_Short.md)] -- for example, general, currency with or without decimals, percentages with and without decimals, and so on. In a chart, number formatting applies to axis annotations, as well as data point pop-ups. You set number formatting on each chart individually, not on the mobile report as a whole. 

* To set the number format, select the **Layout** tab, select a chart on the design surface, and in the **Visual properties** pane select a **Number format**. 
  
### Legend
* To show the legend for a chart, select the **Layout** tab, select a chart on the design surface, and in the **Visual properties** pane set **Show legend** to **On**
  
### Series
Each individual metric, or value, displayed on a chart is referred to as a series; multiple series can, and do, share both a common x-axis and a common y-axis. Series are defined in the data properties panel of the data view by selecting one or more data tables and fields. Each field will result in an individual series of data points on the chart visualization with its own color.  

### Change aggregation 
For numeric fields in charts, the default aggregation is to sum. You can change it to average, count, minimum, maximum, first, or last.

* Select the **Data** tab, and in **Data properties**, select **Options** next to the numeric field > select a different aggregation.

### Set or clear filters

If you add a navigator to filter your mobile report, you can decide which charts you want it to filter.

1. Select the **Data** tab, and in **Data properties**, select **Options**.

2. Under **Filtered by**, you see navigators you can select or clear.

Read more about [adding navigators to filter a mobile report](../../Topics\TopicNameNotContainA/Add-navigators-to-Reporting-Services-mobile-reports.md).
   
## Time charts  
  
The time chart is the most basic chart in [!INCLUDE[SS_MobileReptPub_Short](../../Token\Other/SS_MobileReptPub_Short.md)]. The time (and date) axis of the chart is automatically set to the first valid date/time field in the data table.  

![mobile-report-time-chart](../../Images\Image\ImageNotContaina/mobile-report-time-chart.png)

1. Drag a **Time chart** from the **Layout** tab to the design surface and resize it.

2. By default, it's a stacked bar chart. You can change that in **Series visualization**.

3. If the chart needs data that's not already in the report, select the **Data** tab > **Add data** to [get data from Excel or a shared dataset](../../Topics\TopicNameNotContainA/Data-for-Reporting-Services-mobile-reports.md).

3. In the **Data properties** pane, **Main Series** is **SimulatedTable**. Select the arrow in the box > select your table.

5. If you set **Data structure** to **By columns** (on the **Layout** tab > **Visual properties** pane), here in the **Data properties** pane you can select multiple columns of numeric values.

   If you set **Data structure** to **By rows**, here in the **Data properties** pane you can select one **Series Name Field** and one column of numeric values.
   
Read more about [grouping data by columns or rows](Group%20data%20by%20columns%20or%20rows%20in%20a%20mobile%20report%20%7C%20Reporting%20Services.md).
  
## Category charts  
  
Unlike in a time chart, in a category chart you group on a field other than a date/time field on the x-axis. This grouping, called the *category coordinate*, has to be on a string, not a numeric, field.

![mobile-report-category-chart](../../Images\Image\ImageNotContaina/mobile-report-category-chart.png)   

1. Drag a **Category chart** from the **Layout** tab to the design surface, resize it, and [get data for it](../../Topics\TopicNameNotContainA/Data-for-Reporting-Services-mobile-reports.md), if necessary.

2. Select the **Data** tab, and in the **Data properties** pane under **Category Coordinate**, select a table and field to group on. This field will be on the x axis of the resulting chart.

3. Under **Main Series**, select the table and numeric fields to be aggregated for each category. 
  
## Totals charts  

![mobile-report-totals-chart](../../Images\Image\ImageNotContaina/mobile-report-totals-chart.png)
  
The totals chart accomplishes two separate things: 
* It doesn't present multiple series -- only the sum, or total, of the defined main series. 
* It gives the option to group data by columns or by rows. Grouping by columns can be useful when dealing with flattened data. When grouping by columns, only the main series property is available because the category column is automatically determined by the number of fields selected for the main series property.  

Read more about [grouping data by columns or rows](Group%20data%20by%20columns%20or%20rows%20in%20a%20mobile%20report%20%7C%20Reporting%20Services.md). 
  
## Comparison charts  
  
Time, category, and totals charts are also available as *comparison charts*. In a comparison chart, you can specify not only a main series, but also a second comparison series. The main and comparison series can be displayed in three different ways.

![mobile-report-comparison-time-chart](../../Images\Image\ImageNotContaina/mobile-report-comparison-time-chart.png)

1. Drag one of the **Comparison charts** (time, category, or totals) from the **Layout** tab to the design surface, resize it, and [get data for it](../../Topics\TopicNameNotContainA/Data-for-Reporting-Services-mobile-reports.md), if necessary.

2. In the **Visual properties** pane, in **Series visualization**, select one of the following: 
   * Bar vs. thin bar
   * Line vs. bar
   * Bar vs. step area 

In comparison charts, you can choose to have the same chart colors on the main and comparison values in a series.

* In the **Visual properties** pane, set **Reuse colors on comparison series** to **On**.

   If set to **On**, the color palette restarts between drawing the main and comparison series, so related values in the main and comparison series are the same. 

   If set to **Off**, the color palette continues its normal rotation when drawing the main series after the comparison series, preventing potentially misleading color coordination between the two sets of series.  
  
## Pie and funnel charts  
  
Pie and funnel charts are among the simplest of visualizations. You can structure the data either by rows or by columns. 
* **Pie charts** in [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)] mobile reports can be pies, donuts, or donuts with a total in the center. Pie charts are good for showing the relative size of different parts of a whole. Too many slices make them hard to read.
* **Funnel charts** are often used to show stages in a process, such as sales.

![mobile-report-funnel-chart](../../Images\Image\ImageNotContaina/mobile-report-funnel-chart.png)

### Structure pie and funnel chart data by rows or by columns
1. Drag a **Pie chart** or **Funnel chart** from the **Layout** tab to the design surface, resize it, and [get data for it](../../Topics\TopicNameNotContainA/Data-for-Reporting-Services-mobile-reports.md), if necessary.
2. In the **Visual properties** pane under **Data structure**, select either:
   * **By columns**
   * **By rows**
3. If you selected **By columns**, select the **Data** tab, and in the **Data properties** pane under **Main Series**, select the table and all the fields you want to aggregate in the pie or funnel chart. The field names will be used to label each area of the resulting chart.

   If you selected **By rows**, select the **Data** tab, and in the **Data properties** pane under **Category Column**, select the table and column with the values to use for grouping and labels in the pie. Under Main Series Column, select a numeric field for the values in the chart.

Read more about [grouping data by columns or rows](Group%20data%20by%20columns%20or%20rows%20in%20a%20mobile%20report%20%7C%20Reporting%20Services.md). 

## Treemaps  
  
Treemaps display metrics by applying their values to the size and color of tiles in a rectangular grid. 

![mobile-report-group-treemap](../../Images\Image\ImageNotContaina/mobile-report-group-treemap.png)

1. Drag a **Treemap** from the **Layout** tab to the design surface, resize it, and [get data for it](../../Topics\TopicNameNotContainA/Data-for-Reporting-Services-mobile-reports.md), if necessary.
2.	Select the **Data** tab, and in the **Data properties** pane: 

     * Under **Size Represents** select a numeric field for the tiles' size.
     * Under **Color Represents** select a numeric field for the tiles' color. 
     * [optional] To display a numeric field on the tile itself where space permits, under **Custom Center Value** select a field.
     * [optional] To display a popup when viewers select a tile in the grid, under **Popup Labels** select a field or fields. Treemap popups can display both text and numeric fields.  

By default, treemaps are hierarchical, grouping the tiles by category first, then by size and color.
* Still on the **Data** tab, under **Group by** select a table and field.

You can turn off grouping, so the tiles are arranged only by size and color. 

* Select the **Layout** tab and set **Two-level treemap** to **Off**.   

## See also 
* [Maps in Reporting Services mobile reports](../../Topics\TopicNameNotContainA/Maps-in-Reporting-Services-mobile-reports.md)
* [Navigators in Reporting Services mobile reports](../../Topics\TopicNameNotContainA/Add-navigators-to-Reporting-Services-mobile-reports.md)
* [Data grids in Reporting Services mobile reports](Add%20data%20grids%20to%20mobile%20reports%20%7C%20Reporting%20Services.md)
* [Gauges in Reporting Services mobile reports](Add%20gauges%20to%20mobile%20reports%20%7C%20Reporting%20Services.md)
  
