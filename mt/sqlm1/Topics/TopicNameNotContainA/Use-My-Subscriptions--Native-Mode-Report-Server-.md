---
title: Use My Subscriptions (Native Mode Report Server)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
---
# Use My Subscriptions (Native Mode Report Server)
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Report Manager includes a **My Subscriptions** page that organizes all of your subscriptions into one place. You can use My Subscriptions to view, modify, and delete existing subscriptions. However, you cannot use it to create subscriptions.  
  
||  
|-|  
|**[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode|  
  
 Within My Subscriptions, you can sort subscriptions by folder, report, description, trigger, last run, or status. All values are sorted alphabetically except for Last Run, which is in chronological order.  
  
 My Subscriptions shows only the subscriptions that you create. It does not list subscriptions that are owned by other users, even if you are added as a subscriber to those subscriptions, nor does it show data\-driven subscriptions.  
  
 You cannot search for subscriptions by name, nor can you search for subscriptions based on trigger information, status information, and so forth. For more information, see [Create and Manage Subscriptions for Native Mode Report Servers](../../Topics\TopicNameNotContainA/Create-and-Manage-Subscriptions-for-Native-Mode-Report-Servers.md).  
  
## How to Use My Subscriptions  
 My Subscriptions is available through Report Manager. To access My Subscriptions, click **My Subscriptions** on the Report Manager global toolbar.  
  
## Use Windows PowerShell to list MySubscriptions  
 ![PowerShell related content](../../Images\Image\ImageNotContaina/rs_PowerShellicon.jpg "rs_PowerShellicon")  
  
 The following PowerShell script will return the list of subscriptions and subscription properties for the current user. For more information, see [ReportingService2010.ListMySubscriptions Method](http://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions  
  
```  
  
## See Also  
 [Data-Driven Subscriptions](../../Topics\TopicNameNotContainA/Data-Driven-Subscriptions.md)   
 [Subscriptions and Delivery &#40;Reporting Services&#41;](../Topic/Subscriptions%20and%20Delivery%20\(Reporting%20Services\).md)   
 [old\_Create and Manage Subscriptions for Native Mode Report Servers](assetId:///7f46cbdb-5102-4941-bca2-5e0ff9012c6b)  
  
  