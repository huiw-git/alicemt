---
title: Store Credentials in a Reporting Services Data Source
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
---
# Store Credentials in a Reporting Services Data Source
  You can configure stored credentials that a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server uses to access external data for a report. Stored credentials are used if the report runs unattended, for example a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscription that publishes a report as an e\-mail. The report server retrieves and uses the credentials when report processing is scheduled or triggered. This topic walks you through configuring stored credentials for both Native mode and SharePoint mode report servers.  
  
||  
|-|  
|**[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode|  
  
-   [Configure stored credentials for a report-specific data source (Native mode)](#bkmk_stored_credentials_data_source_native)  
  
-   [Configure stored credentials for a report-specific data source (SharePoint mode)](#bkmk_stored_credentials_data_source_sharepoint)  
  
-   [Configure stored credentials for a shared data source (Native mode)](#bkmk_stored_credentials_shared_data_source_native)  
  
-   [Configure stored credentials for a shared data source (SharePoint mode)](#bkmk_stored_credentials_shared_data_source_sharepoint)  
  
##  <a name="bkmk_top"></a> Security policy requirements for stored credentials  
 ![as_powerpivot_refresh_sss_set_key](../../Images\Image\ImageNotContaina/as_powerpivot_refresh_sss_set_key.gif "as_powerpivot_refresh_sss_set_key") It is required that the account you use for stored credentials, is configured for one of the following security policies on the report server. It is recommended you select the policy with the minimum level of permissions you require for your environment.  
  
1.  **Allow log on locally**. For more information, see [Allow log on locally](http://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).  
  
2.  **Log on as a batch job**. For more information, see [Log on as a batch job](http://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).  
  
3.  For general information on policies, see [Edit security settings on a Group Policy object](http://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).  
  
##  <a name="bkmk_stored_credentials_data_source_native"></a> Configure stored credentials for a report\-specific data source \(Native mode\)  
  
1.  In Native mode Report Manager, browse to the folder that contains the report. Click the item context menu ![context menu in report manager for ssrs items](../../Images\Image\ImageNotContaina/ssrs_report_manager_item_context_menu.png "ssrs_report_manager_item_context_menu").  
  
2.  Click **Manage** and then click **Data Sources**.  
  
3.  Select **A custom data source**.  
  
4.  In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.  
  
5.  For **Connection String**, specify the connection string that the report server uses to connect to the data source. The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database:  
  
    ```  
    data source=<servername>;initial catalog=AdventureWorks2012  
    ```  
  
6.  For **Connect Using**, select **Credentials stored securely in the report server**.  
  
7.  Type a user name and password.  
  
    -   If the account is a Windows domain user account, specify it in this format: \<domain\>\\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**  
  
    -   If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**. If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.  
  
8.  Click **Apply**.  
  
     ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Security policy requirements for stored credentials](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_data_source_sharepoint"></a> Configure stored credentials for a report\-specific data source \(SharePoint mode\)  
  
1.  Browse to the document library that contains the report and then click the open menu ![document library context menu for ssrs items](../../Images\Image\ImageNotContaina/ssrs_sharepoint_item_context_menu.png "ssrs_sharepoint_item_context_menu").  
  
2.  Click second open menu ![document library context menu for ssrs items](../../Images\Image\ImageNotContaina/ssrs_sharepoint_item_context_menu.png "ssrs_sharepoint_item_context_menu") and then click **Manage Data Sources**.  
  
3.  Click the name of the **Custom** data source you want to configure with stored credentials.  
  
4.  In the **Data Source Type** list, select the data processing extension that is used to process data from the data source.  
  
5.  For **Connection String**, specify the connection string that the report server uses to connect to the data source. The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database:  
  
    ```  
    data source=<servername>;initial catalog=AdventureWorks2012  
    ```  
  
6.  For **Credentials**, select **Stored Credentials**.  
  
7.  Type a **user name** and **password**.  
  
    -   If the account is a Windows domain user account, specify it in this format: \<domain\>\\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**  
  
    -   If the user name and password are database credentials, do not select **Use as Windows credentials**. If the database server supports impersonation or delegation, you can select **Set execution context to this account**.  
  
8.  Click **ok**.  
  
     ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Security policy requirements for stored credentials](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_shared_data_source_native"></a> Configure stored credentials for a shared data source \(Native mode\)  
  
1.  In Native mode Report Manager, browse to the shared data source item. ![Shared data source icon](../../Images\Image\ImageNotContaina/hlp_16datasource.png "hlp_16datasource")  
  
2.  Click the context menu ![context menu in report manager for ssrs items](../../Images\Image\ImageNotContaina/ssrs_report_manager_item_context_menu.png "ssrs_report_manager_item_context_menu") and then click **Manage**.  
  
3.  In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.  
  
4.  For **Connection String**, specify the connection string that the report server uses to connect to the data source. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you do not specify credentials in the connection string.  
  
     The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database:  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
5.  Type a user name and password.  
  
    -   If the account is a Windows domain user account, specify it in this format: \<domain\>\\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**  
  
    -   If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**. If the database server supports impersonation or delegation, you can select **Impersonate the authenticated user after a connection has been made to the data source**.  
  
6.  Click **Apply**.  
  
     ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Security policy requirements for stored credentials](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a> Configure stored credentials for a shared data source \(SharePoint mode\)  
  
1.  In the document library, browse to the shared data source item.![Shared data source icon](../../Images\Image\ImageNotContaina/hlp_16datasource.png "hlp_16datasource")  
  
2.  Click the context menu ![document library context menu for ssrs items](../../Images\Image\ImageNotContaina/ssrs_sharepoint_item_context_menu.png "ssrs_sharepoint_item_context_menu") and then click the second context menu ![document library context menu for ssrs items](../../Images\Image\ImageNotContaina/ssrs_sharepoint_item_context_menu.png "ssrs_sharepoint_item_context_menu").  
  
3.  Click **Edit Data Source Definition**.  
  
4.  In the **Data Source Type** list, specify the data processing extension that is used to process data from the data source.  
  
5.  For **Connection String**, specify the connection string that the report server uses to connect to the data source. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that you do not specify credentials in the connection string.  
  
     The following example illustrates a connection string used to connect to the local [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database:  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
6.  Type a user name and password.  
  
    -   If the account is a Windows domain user account, specify it in this format: \<domain\>\\\<account\>, and then select **Use as Windows credentials.**  
  
    -   If the user name and password are database credentials, do not select **Use as Windows credentials**. If the database server supports impersonation or delegation, you can select **Set Execution context to this account**.  
  
7.  Click **Ok**.  
  
     ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Security policy requirements for stored credentials](#bkmk_top)  
  
## See Also  
 [Specify Credential and Connection Information for Report Data Sources](../../Topics\TopicNameNotContainA/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md)   
 [Configure Data Source Properties for a Report  &#40;Report Manager&#41;](../Topic/Configure%20Data%20Source%20Properties%20for%20a%20Report%20%20\(Report%20Manager\).md)   
 [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Data Sources Properties Page &#40;Report Manager&#41;](../Topic/Data%20Sources%20Properties%20Page%20\(Report%20Manager\).md)   
 [New Data Source Page &#40;Report Manager&#41;](../Topic/New%20Data%20Source%20Page%20\(Report%20Manager\).md)  
  
  