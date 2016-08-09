---
title: "Dataset Properties Dialog Box, Options"
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
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
caps.latest.revision: 39
manager: mblythe
robots: noindex,nofollow
---
# Dataset Properties Dialog Box, Options
Select **Options** on the **DatasetProperties** dialog box to change data options, such as collation options and subtotals, for the query. For more information, see [Collation and Unicode Support](../../Topics/TopicNameNotContainA/Collation-and-Unicode-Support.md).  
  
## Options  
 **Collation**  
 Select a locale that determines the collation sequence to be used for sorting data. **Default** indicates that the report server should attempt to derive the value from the data provider when the report runs. If the value cannot be derived, the default value is derived from the locale setting of the computer.  
  
 **Case sensitivity**  
 Select a value that determines case sensitivity. This option indicates whether the data is case-sensitive. You can set **Case Sensitivity** to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs. If the data provider does not support the case-sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Accent sensitivity**  
 Select a value that determines accent sensitivity. **Accent Sensitivity** indicates whether the data is accent sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report is run. If the data provider does not support the accent sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Kanatype sensitivity**  
 Select a value that determines kanatype sensitivity. This option indicates whether the data is kanatype sensitive; it can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs. If the data provider does not support the kanatype sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Width sensitivity**  
 Select a value that determines width sensitivity. This option indicates whether the data is width-sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs. If the data provider does not support the width sensitivity type, the report runs as though the value were **False**. If you know the value and you know it is supported, choose **True**.  
  
 **Interpret subtotals as detail rows**  
 Select a value that indicates whether you want subtotal rows to be interpreted as detail rows instead of aggregate rows. The default value, **Auto**, indicates that the subtotal rows should be treated as detail rows if the report does not use the **Aggregate**() function to access any fields in the data set. If you want subtotal rows to be interpreted as aggregate rows, choose **False**. If you want the subtotal rows to be interpreted as detail rows and you know that they do not use the **Aggregate**() function, choose **True**.  
  
## See Also  
 [Set the Locale for a Report or Text Box (Reporting Services)](../../Topics/TopicNameContainA/Set-the-Locale-for-a-Report-or-Text-Box--Reporting-Services-.md)   
 [Report Datasets (SSRS)](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md)   
 [Windows Collation Name (Transact-SQL)](assetId:///acceef84-2c68-46e2-a021-be019b7ab14e)   
 [SQL Server Collation Name (Transact-SQL)](assetId:///56483d24-add7-483d-9b96-c6fda460ddbc)   
 [Aggregate Function (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Aggregate-Function--Report-Builder-and-SSRS-.md)