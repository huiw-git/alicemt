---
title: Update Credentials in Report Data Sources from a SharePoint Site
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0c50b6e-89e7-4b4d-8fe5-c90682c5d1b1
---
# Update Credentials in Report Data Sources from a SharePoint Site
  This topic describes how to update data sources embedded in reports and shared data sources that are saved in a SharePoint document library.  
  
 Many of your reports might include data sources or use shared data sources that are configured to use Windows Authentication. Under some circumstances, such as creating data alerts on reports saved to a SharePoint document library, you need to update the data source credentials to stored credentials or require no credentials.  
  
 To use stored credentials in reports, you might decide to create and use a new SQL Server login. For more information, see [Create a Login](../../Topics\TopicNameContainA/Create-a-Login.md).  
  
### To update an embedded data source to use stored credentials  
  
1.  Go to the SharePoint document library where you saved the report.  
  
2.  Click the icon for the expand drop\-down menu on the report and then click **Manage Data Sources**.  
  
     The Manage Data Sources page opens.  
  
3.  In the **Name** column, click the data source.  
  
4.  For **Connection Type** verify that the **Custom data source** option is selected.  
  
     This option indicates that the data source is embedded in the report.  
  
5.  Leave the **Data Source Type** and **Connection string** options as they are, unless you want the report to connect to different type of data source, a different server, or data store.  
  
6.  For **Credentials**, select **Stored credentials**. This option works only if the data source does not accept credentials or if you are passing credentials some other way.  
  
     The **Credentials are not required** option can also be used under some circumstances.  
  
     From some data source types, the unattended execution account must be configured on the report server. For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../Topic/Add%20Data%20from%20External%20Data%20Sources%20\(SSRS\).md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Unattended%20Execution%20Account%20\(SSRS%20Configuration%20Manager\).md).  
  
7.  Type a user name and password.  
  
    -   If the account is a Windows domain user account, specify it in this format: \<domain\>\\\<account\>, and then select **Use as Windows credentials when connecting to the data source**.  
  
    -   If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**. If the database server supports impersonation or delegation, you can select **Set execution context to this account**.  
  
8.  To verify the data source can connect by using the updated credentials, click **Test connection**.  
  
9. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
### To update a shared data source to use stored credentials  
  
1.  Go to the SharePoint document library where you saved the shared data source.  
  
2.  Click the icon for the expand drop\-down menu on shared data source, and then click **Edit Data Source Definition**.  
  
     The Data Source page opens.  
  
3.  Leave the **Data Source Type** and **Connection string** options as they are, unless you want the shared data source to connect to different type of data source, a different server, or data store.  
  
4.  For **Credentials**, select **Stored credentials**.  
  
     The **Credentials are not required** option can also be used under some circumstances. This option works only if the data source does not accept credentials or if you are passing credentials some other way.  
  
     From some data source types, the unattended execution account must be configured on the report server. For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../Topic/Add%20Data%20from%20External%20Data%20Sources%20\(SSRS\).md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Unattended%20Execution%20Account%20\(SSRS%20Configuration%20Manager\).md).  
  
5.  Type a user name and password.  
  
    -   If the account is a Windows domain user account, specify it in this format: \<domain\>\\\<account\>, and then select **Use as Windows credentials when connecting to the data source.**  
  
    -   If the user name and password are database credentials, do not select **Use as Windows credentials when connecting to the data source**. If the database server supports impersonation or delegation, you can select **Set execution context to this account**.  
  
6.  To verify the data source can connect using the updated credentials, **Test connection**.  
  
7.  Verify that Enable this data source is selected.  
  
8.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;](../Topic/Upload%20Documents%20to%20a%20SharePoint%20Library%20\(Reporting%20Services%20in%20SharePoint%20Mode\).md)  
  
  