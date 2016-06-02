---
title: Work Around the Excel 2003 Row Limitation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
---
# Work Around the Excel 2003 Row Limitation
  This topic explains how to work around the Excel 2003 row limitation when you export paginated reports to Excel. The workaround is for a report that contains only a table.  
  
> [!IMPORTANT]  
>  The [!INCLUDE[ofprexcel](../../Token\Other/ofprexcel_md.md)] 2003 \(.xls\) rendering extension is deprecated. For more information, see [Deprecated Features in SQL Server Reporting Services in SQL Server 2016](../../Topics\TopicNameNotContainA/Deprecated-Features-in-SQL-Server-Reporting-Services-in-SQL-Server-2016.md).  
  
 Excel 2003 supports a maximum of 65,536 rows per worksheet. You can work around this limitation by forcing an explicit page break after a certain number of rows. The Excel renderer creates a new worksheet for each explicit page break.  
  
### To create an explicit page break  
  
1.  Open the report in [!INCLUDE[ss_dtbi](../../Token\Other/ss_dtbi_md.md)] or the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] web portal.  
  
2.  Right click the Data row in the table, and then click **Add Group** \> **Parent Group** to add an outer table group.  
  
     ![Select the Parent Group](../../Images\Image\ImageNotContaina/DataRow_SelectParentGroup.png "DataRow_SelectParentGroup")  
  
3.  Enter the following formula in the **Group by** expression box, and then click **OK** to add the parent group.  
  
     \=Int\(\(RowNumber\(Nothing\)\-1\)\/65000\)  
  
     The formula assigns a number to each set of 65000 rows in the dataset. When a page break is defined for the group, the expression results in a page break every 65000 rows.  
  
     Adding the outer table group adds a group column to the report.  
  
4.  Delete the group column by right\-clicking on the column header, clicking **Delete Columns**, selecting **Delete columns only**, and then click **OK**.  
  
     ![Delete a group column](../../Images\Image\ImageContaina/GroupColumn_Delete_updated.png "GroupColumn_Delete_updated")  
  
5.  Right click **Group 1** in the **Row Groups** section, and then click **Group Properties**.  
  
     ![View group properties](../../Images\Image\ImageNotContaina/GroupProperties_updated.png "GroupProperties_updated")  
  
6.  On the **Sorting** page of the **Group Properties** dialog box, select the default sorting option and click **Delete**.  
  
     ![Delete default sorting](../../Images\Image\ImageNotContaina/GroupProperties_Sorting_updated.png "GroupProperties_Sorting_updated")  
  
7.  On the **Page Breaks** page, click **Between each instance of a group** and then click **OK**.  
  
     ![Set page breaks](../../Images\Image\ImageNotContaina/GroupProperties_PageBreaks_updated.png "GroupProperties_PageBreaks_updated")  
  
8.  Save the report. When you export it to Excel, it exports to multiple worksheets and each worksheet contains a maximum of 65000 rows.  
  
  