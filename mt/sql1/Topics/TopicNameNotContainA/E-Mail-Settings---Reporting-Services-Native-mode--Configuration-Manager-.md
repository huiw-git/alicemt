---
title: "E-Mail Settings - Reporting Services Native mode (Configuration Manager)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
caps.latest.revision: 10
caps.handback.revision: 0
manager: mblythe
---
# E-Mail Settings - Reporting Services Native mode (Configuration Manager)
Use the **E-mail Settings** page of the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration Manager to configure a Native mode report server for Simple Mail Transport Protocol (SMTP) e-mail delivery. You can use the Report Server E-Mail delivery extension to distribute [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] reports or report processing notifications through e-mail subscriptions. The Report Server E-Mail delivery extension requires an SMTP server and an e-mail address to use in the From: field.  
  
 Additional configuration settings can be used to further customize e-mail subscriptions, including settings that restrict mail server hosts and rendering extension availability. You cannot specify these settings in the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration Manager. To configure the additional settings, edit the **RSReportServer.config** file. For more information, see [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83) and [Reporting Services Configuration Files](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Files.md) in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Books Online.  
  
 [!INCLUDE[applies](../../Topics/TopicNameContainA/tokens/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Native mode.  
  
## Options  
 **Sender Address**  
 Specifies the e-mail address to use in the **From:** field of a generated e-mail. You must specify a user account that has permission to send mail from the SMTP server. The value you type for the “sender address” is saved in the `<From>` field in the rsreportserver.config file.  
  
 **Current SMTP Delivery Method**  
 Specifies that report server e-mail is routed through an SMTP server. This is the only delivery method that you can specify in the Reporting Services Configuration Manager.  
  
 An alternative delivery method is to use a local SMTP service pickup directory. You can use this delivery method if a network SMTP service is not available. To specify a local SMTP service pickup directory, you must edit the RSReportServer.config file. If you edit the configuration file to use a local SMTP service pickup directory, the Reporting Services Configuration Manager sets the **Delivery method** option to *custom* to indicate that the delivery method is specified in the configuration file.  
  
 In the configuration file, the delivery method is set through the **SendUsing** configuration setting. For more information about specifying the **SendUsing** setting, see [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83).  
  
 **SMTP Server**  
 Specify the SMTP server or gateway to use. You can use a local server or an SMTP server on your network.  
  
## See Also  
 [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83)   
 [Reporting Services Configuration Manager Help Topics](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Manager-Help-Topics.md)