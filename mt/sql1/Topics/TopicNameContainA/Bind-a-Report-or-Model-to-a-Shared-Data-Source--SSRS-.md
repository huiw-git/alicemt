---
title: "Bind a Report or Model to a Shared Data Source (SSRS)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
caps.latest.revision: 12
manager: mblythe
---
# Bind a Report or Model to a Shared Data Source (SSRS)
In some situations, such as when you move a report or model from a test server to a production server, you might want to save the file to your local computer and then upload it to a different report server. When you upload the report or model to the new server, you need to rebind it to a shared data source that is stored on the new report server. If you don't rebind the report or model, it will not work correctly when accessed from the new report server.  
  
> [!IMPORTANT]  
>  Before rebinding a report or model to a shared data source, the data source must already exist on the report server or SharePoint library. For more information about data sources, see [Create, Modify, and Delete Shared Data Sources (SSRS)](../../Topics/TopicNameNotContainA/Create--Modify--and-Delete-Shared-Data-Sources--SSRS-.md).  
  
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
  
6.  In the **Data Source Link** area, click the ellipsis (…) button.  
  
7.  Locate the data source you want to use.  
  
8.  Select the data source and **click OK**.  
  
9. [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
10. Click **Close**.  
  
## See Also  
 [Upload a File or Report (Report Manager)](../../Topics/TopicNameContainA/Upload-a-File-or-Report--Report-Manager-.md)   
 [Upload Documents to a SharePoint Library (Reporting Services in SharePoint Mode)](../../Topics/TopicNameContainA/Upload-Documents-to-a-SharePoint-Library--Reporting-Services-in-SharePoint-Mode-.md)   
 [Create and Manage Shared Data Sources (Reporting Services in SharePoint Integrated Mode)](../../Topics/TopicNameNotContainA/Create-and-Manage-Shared-Data-Sources--Reporting-Services-in-SharePoint-Integrated-Mode-.md)   
 [Create, Delete, or Modify a Shared Data Source (Report Manager)](../../Topics/TopicNameContainA/Create--Delete--or-Modify-a-Shared-Data-Source--Report-Manager-.md)   
 [Data Connections, Data Sources, and Connection Strings (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings--Report-Builder-and-SSRS-.md)   
 [Data Sources Supported by Reporting Services (SSRS)](../../Topics/TopicNameNotContainA/Data-Sources-Supported-by-Reporting-Services--SSRS-.md)