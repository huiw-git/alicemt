---
title: Using the DQS Default Knowledge Base
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - data-quality-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
---
# Using the DQS Default Knowledge Base
  This topic describes the default knowledge base, **DQS Data**, which is installed with [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\). This is a pre\-built default knowledge base that contains the following domains:  
  
-   **Country\/Region**: Contains the conventional long \(official name as designated by the country\/region \) and short names \(common name used in lists, on maps, etc. \), two\-letter abbreviation, three\-letter abbreviation and three\-digit code for each location.  Leading value is set to the long country name.  
  
-   **Country\/Region \(three\-letter leading\)**: Contains the conventional long \(official name as designated by the country\/region\) and short names \(common name used in lists, on maps, and so on\), two\-letter abbreviation, three\-letter abbreviation and three\-digit code for each location.  Leading values is set to County three\-letter abbreviation.  
  
-   **Country\/Region \(two\-letter leading\)**: Contains the conventional long \(official name as designated by the country\/region \) and short names \(common name used in lists, on maps, etc. \), two\-letter abbreviation, three\-letter abbreviation and three\-digit code for each location.  Leading value is set to the Country two\-letter abbreviation.  
  
-   **US \- Counties**: Contains a list of US counties.  
  
-   **US \- Last Name**: Contains a list of last names \(surnames\) occurring 100 or more times in the Census 2000.  
  
-   **US \- Places**: Contains a list of places for the 50 states, the District of Columbia, and Puerto Rico extracted from the Census 2010.  
  
-   **US \- State**: Contains the conventional long \(official\) name and two\-letter abbreviation for each state in US. Leading value is set to the conventional state name.  
  
-   **US – State \(2\-letter heading\)**: Contains the conventional long \(official\) name and two\-letter abbreviation for each state in US. Leading value is set to the two\-letter abbreviation state name.  
  
## Using the Default Knowledge Base  
 You can use the default DQS knowledge base, DQS Data, in the following ways:  
  
-   Quickly start and run a cleansing data quality project using the default knowledge base without first having to create a new knowledge base in DQS.  
  
-   Run the Domain Management, Knowledge Discovery, or Matching Policy activities on the default knowledge base. To do so, click **Open Knowledge Base** in the [Data Quality Client Home Screen](../../Topics\TopicNameNotContainA/Data-Quality-Client-Home-Screen.md), select the **DQS Data** knowledge base in the **Open Knowledge Base** screen, and then select the required activity in the **Select Activity** area. Click **Next** to proceed.  
  
-   Create a new knowledge base using the default knowledge base. To create a knowledge base from an existing knowledge base, see [Create a Knowledge Base](../../Topics\TopicNameContainA/Create-a-Knowledge-Base.md).  
  
-   Use it in the [DQS Cleansing component in Integration Services](http://go.microsoft.com/fwlink/?LinkId=238830) and [Master Data Services Add\-in for Excel](../../Topics\TopicNameNotContainA/Data-Quality-Matching-in-the-MDS-Add-in-for-Excel.md).  
  
## See Also  
 [DQS Knowledge Bases and Domains](../../Topics\TopicNameNotContainA/DQS-Knowledge-Bases-and-Domains.md)  
  
  