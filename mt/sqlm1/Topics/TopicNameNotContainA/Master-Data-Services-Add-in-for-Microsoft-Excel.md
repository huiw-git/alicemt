---
title: Master Data Services Add-in for Microsoft Excel
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33d9c8fc-9602-494d-b9ab-8f0f42785974
---
# Master Data Services Add-in for Microsoft Excel
  With the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)][!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], you can load filtered lists of data from MDS into Excel, where you can work with it just as you would any other data. When you are done, you can publish the data back to MDS, where it is centrally stored. Security determines which data you can view and update.  
  
 If you are an administrator, use the [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)] to create entities and attributes and to load them with data. This eliminates the need to use any other tools to load data into your models.  
  
 In the [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], you can use Data Quality Services \(DQS\) to match data before loading it into MDS. This helps to prevent duplicate data in MDS.  
  
> [!NOTE]  
>  You can download the latest [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)][!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)] from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=51668).  
  
## Terms  
 When working with the Add\-in, you may encounter the following terms. For more information about these concepts, see [Master Data Services Overview &#40;MDS&#41;](../Topic/Master%20Data%20Services%20Overview%20\(MDS\).md).  
  
-   The *MDS repository* is where all master data is stored. It is a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database that is configured to store MDS data. To work with data from the repository, you load data it into Excel; when you’re done working with it, you publish changes back to the repository. Administrators can add new entities and attributes to the repository.  
  
-   *MDS\-managed data* is data that is stored in the MDS repository and that you load into Excel, where the data is displayed as highlighted rows. You can add data that is not MDS\-managed to your worksheet, and it is not affected when you refresh the MDS\-managed data.  
  
-   A *model* is a container of data. Versions of these containers can be created, and usually the latest version is the most recent. For more information, see [Models &#40;Master Data Services&#41;](../Topic/Models%20\(Master%20Data%20Services\).md).  
  
-   An *entity* is a list of data. You might think of an entity as a table in a database. For example, the **Color** entity might contain a list of colors. For more information, see [Entities &#40;Master Data Services&#41;](../Topic/Entities%20\(Master%20Data%20Services\).md).  
  
-   A *member* is a row of data \(a record\). Each entity contains members. An example of a member is **Blue**. For more information, see [Members &#40;Master Data Services&#41;](../Topic/Members%20\(Master%20Data%20Services\).md).  
  
-   An *attribute* is a column of data. Each member has attributes. For example, the **Code** attribute for the **Blue** member is **B**. For more information about attributes, see [Attributes &#40;Master Data Services&#41;](../Topic/Attributes%20\(Master%20Data%20Services\).md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a connection to a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] repository.|[Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](../Topic/Connect%20to%20an%20MDS%20Repository%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Load MDS\-managed data into Excel.|[Export Data to Excel from Master Data Services](../../Topics\TopicNameNotContainA/Export-Data-to-Excel-from-Master-Data-Services.md)|  
|Save a shortcut query that you can use open the currently displayed MDS\-managed data in the future.|[Save a Shortcut Query File &#40;MDS Add-in for Excel&#41;](../Topic/Save%20a%20Shortcut%20Query%20File%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Share shortcuts with others.|[Email a Shortcut Query File &#40;MDS Add-in for Excel&#41;](../Topic/Email%20a%20Shortcut%20Query%20File%20\(MDS%20Add-in%20for%20Excel\).md)|  
|View all changes that have been made to a member.|[View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](../Topic/View%20All%20Annotations%20or%20Transactions%20for%20a%20Member%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Before publishing new data, find out whether duplication exists.|[Match Similar Data &#40;MDS Add-in for Excel&#41;](../Topic/Match%20Similar%20Data%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Publish data from a worksheet into the MDS repository.|[Import Data from Excel to Master Data Services &#40;MDS Add-in for Excel&#41;](../Topic/Import%20Data%20from%20Excel%20to%20Master%20Data%20Services%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Create a new entity with data in the worksheet. \(Administrators only\)|[Create an Entity &#40;MDS Add-in for Excel&#41;](../Topic/Create%20an%20Entity%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Create a domain\-based attribute, also known as a constrained list. \(Administrators only\)|[Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](../Topic/Create%20a%20Domain-based%20Attribute%20\(MDS%20Add-in%20for%20Excel\).md)|  
|Set properties for loading and publishing data in the Master Data Services Add\-in for Excel. \(Administrators only\)|[Setting Properties for Master Data Services Add-in for Excel](../../Topics\TopicNameNotContainA/Setting-Properties-for-Master-Data-Services-Add-in-for-Excel.md)|  
  
## Related Content  
  
-   [Connections &#40;MDS Add-in for Excel&#41;](../Topic/Connections%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Overview: Exporting Data to Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Exporting%20Data%20to%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](../Topic/Shortcut%20Query%20Files%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Refreshing Data &#40;MDS Add-in for Excel&#41;](../Topic/Refreshing%20Data%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Overview: Importing Data from Excel &#40;MDS Add-in for Excel&#41;](../Topic/Overview:%20Importing%20Data%20from%20Excel%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Validating Data &#40;MDS Add-in for Excel&#41;](../Topic/Validating%20Data%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Data Quality Matching in the MDS Add-in for Excel](../../Topics\TopicNameNotContainA/Data-Quality-Matching-in-the-MDS-Add-in-for-Excel.md)  
  
-   [Building a Model &#40;MDS Add-in for Excel&#41;](../Topic/Building%20a%20Model%20\(MDS%20Add-in%20for%20Excel\).md)  
  
-   [Setting Properties for Master Data Services Add-in for Excel](../../Topics\TopicNameNotContainA/Setting-Properties-for-Master-Data-Services-Add-in-for-Excel.md)  
  
-   [Security &#40;Master Data Services&#41;](../Topic/Security%20\(Master%20Data%20Services\).md)  
  
  