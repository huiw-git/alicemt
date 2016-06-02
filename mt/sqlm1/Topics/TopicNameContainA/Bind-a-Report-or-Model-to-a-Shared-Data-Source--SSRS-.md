---
title: Bind a Report or Model to a Shared Data Source (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
---
# Bind a Report or Model to a Shared Data Source (SSRS)
  In some situations, such as when you move a report or model from a test server to a production server, you might want to save the file to your local computer and then upload it to a different report server. When you upload the report or model to the new server, you need to rebind it to a shared data source that is stored on the new report server. If you don't rebind the report or model, it will not work correctly when accessed from the new report server.  
  
> [!IMPORTANT]  
>  Before rebinding a report or model to a shared data source, the data source must already exist on the report server or SharePoint library. For more information about data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](../Topic/Create,%20Modify,%20and%20Delete%20Shared%20Data%20Sources%20\(SSRS\).md).  
  
### To bind a report or model to a shared data source on a report server running in native mode  
  
1.  In **Report Manager**, click the name of the report or model that you uploaded to the server.  
  
     The Properties tab opens.  
  
2.  Click **Data Sources**.  
  
3.  Click **Browse**, and then navigate to the data source to which you want to bind the report or model.  
  
4.  Select the data source and then click **OK**.  
  
5.  Click **Apply**.  
  
     The report or model is now bound to the data source that you selected.  
  
### To bind a report or model to a shared data source on a report server running in SharePoint integrated mode  
  
1.  If the library is not already open, click its name on the Quick Launch bar. If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.  
  
2.  Point to the report or model and click the down arrow.  
  
3.  Click **Manage Data Sources**.  
  
4.  Click **dataSource1**.  
  
5.  In the **Connection Type** area, verify that **Shared data source** is selected.  
  
6.  In the **Data Source Link** area, click the ellipsis \(…\) button.  
  
7.  Locate the data source you want to use.  
  
8.  Select the data source and **click OK**.  
  
9. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
10. Click **Close**.  
  
## See Also  
 [Upload a File or Report &#40;Report Manager&#41;](../Topic/Upload%20a%20File%20or%20Report%20\(Report%20Manager\).md)   
 [Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;](../Topic/Upload%20Documents%20to%20a%20SharePoint%20Library%20\(Reporting%20Services%20in%20SharePoint%20Mode\).md)   
 [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)   
 [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../Topic/Data%20Sources%20Supported%20by%20Reporting%20Services%20\(SSRS\).md)  
  
  