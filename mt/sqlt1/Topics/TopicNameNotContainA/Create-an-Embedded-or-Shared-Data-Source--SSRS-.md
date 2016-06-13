---
title: Create an Embedded or Shared Data Source (SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b111a8d0-a60d-4c8b-b00a-51644b19c34b
robots: noindex,nofollow
---
# Create an Embedded or Shared Data Source (SSRS)
  A report data source specifies a name and connection information. [!INCLUDE[ssRSnoversion](../../Token/Other/ssRSnoversion_md.md)] supports two types of data sources: embedded and shared. An embedded data source is defined in a report definition and used only by that report. A shared data source is defined as a separate item and can be used by multiple reports. For more information, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Embedded-and-Shared-Data-Connections-or-Data-Sources--Report-Builder-and-SSRS-.md).  
  
 In Report Builder, you browse to the report server or SharePoint site and select data sources or create embedded data sources. You cannot create shared data sources in Report Builder.  
  
 In Report Designer, you can create shared or embedded data sources. From the Report Data pane, begin to create a data source reference, and then select the **New** option. After you create the data source reference, a new shared data source will automatically be added to Solution Explorer under the Shared Data Sources folder.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token/Other/ssRBRDDup_md.md)]  
  
 You can also create shared data sources directly on a report server or SharePoint site. For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../Topics/TopicNameContainA/Create--Delete--or-Modify-a-Shared-Data-Source--Report-Manager-.md) or [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../Topics/TopicNameNotContainA/Create-and-Manage-Shared-Data-Sources--Reporting-Services-in-SharePoint-Integrated-Mode-.md).  
  
### To create an embedded or shared data source  
  
1.  On the toolbar in the Report Data pane, click **New** and then click **Data Source**. The **Data Source Properties** dialog box opens.  
  
    > [!NOTE]  
    >  If the Report Data pane is not visible, click **Report Data** on the **View** menu.  
  
2.  In the **Name** text box, type a name for the data source or accept the default. The data source name is used internally within the report. For clarity, we recommend that the name of the data source contain the name of the database specified in the connection string.  
  
3.  For an embedded data source, verify that **Embedded connection** is selected.  
  
    1.  From the **Type** drop\-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.  
  
    2.  Specify a connection string using one of the following alternatives:  
  
    -   Type the connection string directly in the **Connection string** text box. For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings-in-Report-Builder.md) or [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings--Report-Builder-and-SSRS-.md).  
  
    -   Click the expression \(**fx\)** button to create an expression that evaluates to a connection string. In the **Expression** dialog box, type the expression in the Expression pane. [!INCLUDE[clickOK](../../Token/Other/clickOK_md.md)]  
  
    -   Click **Edit** to open the **Connection Properties** dialog box for the data source type you chose in step 2.  
  
         Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type. Connection properties include the type of data source, the name of the data source, and the credentials to use. After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct. For more information about specific data source types, see topics in [Add Data from External Data Sources &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Add-Data-from-External-Data-Sources--SSRS-.md).  
  
4.  For a shared data source, verify that **Use shared data source reference** is selected.  
  
    1.  Click **New**. In the **Shared Data Source** properties dialog box, follow steps 2 and 3 to create a new data source.  
  
    2.  [!INCLUDE[clickOK](../../Token/Other/clickOK_md.md)]  
  
         The new shared data source appears in the Shared Data Sources folder in Solution Explorer.  
  
5.  [!INCLUDE[clickOK](../../Token/Other/clickOK_md.md)]  
  
     The data source appears in the Report Data pane. In the Report Data pane, a shared data source points to the data source definition. In Report Builder, the data source definition is on a report server or SharePoint site. In Report Designer, the data source definition is a file in Solution Explorer under the Shared Data Sources folder.  
  
### To import an existing data source in Report Designer  
  
1.  In Solution Explorer, right\-click the **Shared Data Sources** folder in the report server project, and then click **Add Existing Item**. The **Add Existing Item** dialog box opens.  
  
2.  Navigate to an existing Report Definition Shared data source \(rds\) file and then click **Open**.  
  
3.  [!INCLUDE[clickOK](../../Token/Other/clickOK_md.md)]  
  
### To convert an embedded data source to a shared data source in Report Designer  
  
-   In the Report Data pane, right\-click the data source and then click **Convert to Shared Data Source**.  
  
### To convert a shared data source to an embedded data source in Report Builder  
  
-   In the Report Data pane, right\-click the data source and open **Data Source Properties**.  
  
-   Click **Embedded Connection** and finish creating the embedded data source as described in an earlier procedure.  
  
## See Also  
 [Store Credentials in a Reporting Services Data Source](../../Topics/TopicNameContainA/Store-Credentials-in-a-Reporting-Services-Data-Source.md)   
 [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Embedded-and-Shared-Data-Connections-or-Data-Sources--Report-Builder-and-SSRS-.md)   
 [Convert Data Sources &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameNotContainA/Convert-Data-Sources--Report-Builder-and-SSRS-.md)   
 [Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](../../Topics/TopicNameContainA/Bind-a-Report-or-Model-to-a-Shared-Data-Source--SSRS-.md)   
 [Configure Data Source Properties for a Report  &#40;Report Manager&#41;](../../Topics/TopicNameContainA/Configure-Data-Source-Properties-for-a-Report---Report-Manager-.md)   
 [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Data-Sources-Supported-by-Reporting-Services--SSRS-.md)  
  
  