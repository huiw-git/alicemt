---
title: Connect to an MDS Repository (MDS Add-in for Excel)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
---
# Connect to an MDS Repository (MDS Add-in for Excel)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], you must connect to an MDS repository before you can load or publish data.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **Explorer** functional area.  
  
### To connect to an MDS repository  
  
1.  In the MDS [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], on the **Master Data** tab, in the **Connect and Load** group, click the arrow under the **Connect** button and click **Manage Connections**.  
  
2.  On the **Manage Connections** dialog box, in the **New connection** section, click **Create a new connection**.  
  
3.  Click **New**.  
  
4.  On the **Add New Connection** dialog box, in the **Description** field, type a description for your connection. This connection will be displayed when you click the arrow under the **Connect** button on the toolbar.  
  
5.  In the **MDS server address** box, type the URL of the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application, for example http:\/\/contoso\/mds.  
  
    > [!NOTE]  
    >  Ensure that you use the computer name; do not use “localhost”.  
  
6.  Click **OK**. The name is displayed in the **Existing Connections** section.  
  
7.  Optionally, click **Test** to test the connection. A confirmation or error dialog is displayed. Click **OK** to close it.  
  
8.  Click **Connect**. The **Master Data Services** pane is displayed.  
  
## Next Steps  
  
-   [Export Data to Excel from Master Data Services](../../Topics\TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md)  
  
-   [Filter Data before Exporting &#40;MDS Add-in for Excel&#41;](../Topic/Filter%20Data%20before%20Exporting%20\(MDS%20Add-in%20for%20Excel\).md)  
  
## See Also  
 [Connections &#40;MDS Add-in for Excel&#41;](../Topic/Connections%20\(MDS%20Add-in%20for%20Excel\).md)  
  
  