---
title: Create a Model Using Report Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
robots: noindex,nofollow
---
# Create a Model Using Report Manager
  You can generate models from an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] cube, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database, or an Oracle database using Report Manager. Report models are generated from shared data sources that are published on the report server. If you do not already have a shared data source, you must create one.  
  
 The report model that you generate is based entirely on the schema of the shared data source. You cannot choose which parts of the data source are included in the model, nor can you edit the rules or metadata of a generated model. However, you can set properties on the model after it is generated and define role assignments that restrict access to all or part of the model.  
  
> [!NOTE]  
>  An Oracle\-based model generated using Report Manager or [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[offSPServ](../../Token\Other/offSPServ_md.md)] 2007 [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)] will include database objects that are a part of the schema for the user account used to connect to the Oracle data source. The user account name is specified in the data source properties credentials.  
  
### To create a new data source for a report model using Report Manager  
  
1.  In your Web browser, type the URL for your report server in the address bar.  
  
2.  Click **New Data Source**.  
  
3.  In the **Name** box, enter a name for the data source.  
  
4.  Optionally, enter a brief description of the mode in the **Description** text box.  
  
5.  Verify that the **Enable this data source** check box is selected.  
  
6.  In the **Connection type** list, select the data source type to which you want to connect. The connection type must be one of the following: **Oracle**, **Microsoft SQL Server** or **Microsoft SQL Server Analysis Services**.  
  
7.  In the **Connection string** box, enter the connection string that points to the database.  
  
8.  Select the connection method that Report Builder users will need to use to connect to the database.  
  
    -   Windows Authentication: Select this option when you want the operating system to authenticate [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] users. This option allows [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to use Windows security features, such as password encryption, to authenticate users. It is strongly recommended that you select this option.  
  
    -   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication: Select this option when you want users to use a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login account that you created. Users must supply a valid [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login name and password.  
  
        > [!CAUTION]  
        >  Whenever possible, use Windows Authentication.  
  
9. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
### To create a report model using Report Manager  
  
1.  In Report Manager, select the data source that you want to use for your model.  
  
     The Properties page is displayed.  
  
2.  Verify that you want to use the options specified for the data source.  
  
3.  Click **Generate Model**.  
  
     The General page is displayed for the data source.  
  
4.  In the **Name** box, enter a name for the report model.  
  
5.  In the **Description** box, enter a brief description of the model.  
  
6.  To specify a new location to save the report model to, click **Change Location**.  
  
     By default, the report model is saved to Report Manager Home.  
  
7.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
     The report model is created and saved to the location that you specified. You can assign permissions to this model by using Report Manager.  
  
## See Also  
 [Granting Permissions on a Native Mode Report Server](../../Topics\TopicNameContainA/Granting-Permissions-on-a-Native-Mode-Report-Server.md)   
 [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)   
 [New Data Source Page &#40;Report Manager&#41;](../Topic/New%20Data%20Source%20Page%20\(Report%20Manager\).md)  
  
  