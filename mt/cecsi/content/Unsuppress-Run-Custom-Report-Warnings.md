---
title: Unsuppress Run Custom Report Warnings
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - tools-ssms
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
manager:jhubbard
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Unsuppress Run Custom Report Warnings
There are two warning dialog boxes for custom reports. This topic describes how to unsuppress the display of these boxes in [!INCLUDE[ssCurrent](../content/includes/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)].  
  
By default, the **Run Custom Reports** dialog box appears before a custom report runs. If you select the **Please don't show this warning again** check box, the dialog box will no longer appear. Also by default, the **Run Custom Reports** dialog box appears when you open a custom report and then click a link to open another custom report. This dialog box displays the fill path to the drill\-through custom report file. If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.  
  
## <a name="SSMSProcedure"></a>Using SQL Server Management Studio  
  
#### To unsuppress the main custom report warning dialog box  
  
1.  Connect to <*Server*>\\<*Share*>|<*Drive*>\\Documents and Settings\\<UserProfile>\\Application Data\\Microsoft\\Microsoft SQL Server\\130\\Tools\\Shell\\reports.xml.  
  
2.  Right\-click **reports.xml**, and then click **Edit**.  
  
3.  Change**<SuppressWarning>true<\/SuppressWarning> to <SuppressWarning>false<\/SuppressWarning>**.  
  
4.  Restart [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)].  
  
#### To unsuppress the drill\-through custom report warning dialog box  
  
1.  Connect to <*Server*>\\<*Share*>|<*Drive*>\\Documents and Settings\\<UserProfile>\\Application Data\\Microsoft\\Microsoft SQL Server\\130\\Tools\\Shell\\reports.xml.  
  
2.  Right\-click **reports.xml**, and click **Edit**.  
  
3.  Change **<SuppressDrillthroughWarning>true<\/SuppressDrillthroughWarning>to <SuppressDrillthroughWarning>false<\/SuppressDrillthroughWarning>**.  
  
4.  Restart [!INCLUDE[ssManStudioFull](../content/includes/ssManStudioFull_md.md)].  
  
## See Also  
[Custom Reports in Management Studio](../content/Custom-Reports-in-Management-Studio.md)  
[Add a Custom Report to Management Studio](../content/Add-a-Custom-Report-to-Management-Studio.md)  
[Use Custom Reports with Object Explorer Node Properties](../content/Use-Custom-Reports-with-Object-Explorer-Node-Properties.md)  
  
