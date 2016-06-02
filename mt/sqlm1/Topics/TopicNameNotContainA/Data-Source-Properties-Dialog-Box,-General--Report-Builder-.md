---
title: Data Source Properties Dialog Box, General (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b956f43a-8426-4679-acc1-00f405d5ff5b
---
# Data Source Properties Dialog Box, General (Report Builder)
  Select **General** on the **Data Source Properties** dialog box to select a shared data source from a report server or to create or modify connection information for a data source embedded in the report.  
  
 The type of credentials used to connect to a data source is specified in the data source properties. When you open a report from the report server, the run\-time credentials, specified in the data source properties, might not work for design time tasks such as creating queries and previewing reports. For example, the data source might use Windows credentials other than yours or a user name and password that are unknown to you.  
  
 Report Builder opens the **Enter Data Source Credentials** dialog box when it is unable to connect to the data source using the credentials provided in the data source properties. Typically this happens when:  
  
-   The data source is configured to prompt for credentials.  
  
-   The data source is configured to use stored credentials.  To minimize potential security threats, Report Builder is designed to not retrieve credentials stored on the server.  
  
 You can use the **Enter Data Source Credentials** dialog box to change the credentials used by Report Builder at design time to connect to the data source as the current Windows user or provide a user name and password. If you provide a user name and password you can indicate whether they are used as Windows credentials.  
  
> [!NOTE]  
>  Although the query designers allow you to specify other another credentials type for design\-time credentials, report preview only allows you to enter the user name and password for the existing credentials options specified in the data source.  
  
 When you click **Test Connection**, the connection to the data source is tested using the credentials specified in the data source properties credentials page. You can test connections to embedded and shared data sources.  
  
 If the credentials specified are incomplete \(for example, a password is required\), Report Builder prompts you again for run\-time credentials when it needs to connect the data source. The design\-time credentials are stored and you are not prompted again.  
  
## Options  
 **Name**  
 Type the name of the data source. The data source name must be unique within the report. By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.  
  
 **Use a shared connection**  
 Select this option to browse to a shared data source that has been published to a report server.  
  
 After you select a data source from a report server, Report Builder maintains a connection to this report server.  
  
 **Use a connection embedded in my report**  
 Select this option to create a data source that is used only by this report.  
  
 **Type**  
 Select a data processing extension. The list displays all registered extensions.  
  
 **Connection string**  
 Enter a connection string for the data source. Click **Build** to build the connection string using the **Connection Properties** dialog box. Click the **Expressions** \(*fx*\) button to edit the expression.  
  
 **Use a single transaction when processing the queries**  
 Select this option to indicate that datasets that use this data source are run in a single transaction against the database. To include transactions for subreports that use the same data source, select the subreport, and in the Properties pane, set **MergeTransactions** to **True**.  
  
 **Test Connection**  
 Click to verify that the data source connection works by using the specified credentials. If the connection cannot be made, you need to verify your credentials and the server availability. You can test data source connections for embedded and shared data sources.  
  
## See Also  
 [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md)   
 [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../Topic/Add%20and%20Verify%20a%20Data%20Connection%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics\TopicNameNotContainA/Data-Connections,-Data-Sources,-and-Connection-Strings-in-Report-Builder.md)   
 [Data Source Properties Dialog Box, Credentials &#40;Report Builder&#41;](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20Credentials%20\(Report%20Builder\).md)   
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)  
  
  