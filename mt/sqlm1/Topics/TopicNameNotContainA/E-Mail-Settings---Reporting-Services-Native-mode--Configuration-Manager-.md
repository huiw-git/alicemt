---
title: E-Mail Settings - Reporting Services Native mode (Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
---
# E-Mail Settings - Reporting Services Native mode (Configuration Manager)
Reporting Services includes an e-mail delivery extension so that you can distribute reports through e-mail. Depending on how you define the e-mail subscription, a delivery might consist of a notification, link, attachment, or embedded report. The e-mail delivery extension works with your existing mail server technology. The mail server must be an SMTP server or forwarder. The report server connects to an SMTP server through Collaboration Data Objects (CDO) libraries (cdosys.dll) that are provided by the operating system.

The report server e-mail delivery extension is not configured by default. You must use the Reporting Services Configuration Manager to minimally configure the extension. To set advanced properties, you must edit the RSReportServer.config file. If you cannot configure the report server to use this extension, you can deliver reports to a shared folder instead. For more information, see File Share Delivery in Reporting Services.

## Configuration Requirements

- Report server e-mail delivery is implemented on Collaboration Data Objects (CDO) and requires a local or remote Simple Mail Transfer Protocol (SMTP) server or SMTP forwarder. SMTP is not supported on all Windows operating systems. If you are using the Itanium-based edition of Windows Server 2008, SMTP is not supported. For more information about configuration options provided through CDO, see [Configuration CoClass](http://go.microsoft.com/fwlink/?LinkId=98237) on MSDN.

The configured authentication account must have permission on the SMTP server to send mail.

- The e-mail delivery extension uses UTF-8 encoding in e-mail attachments. You cannot modify the encoding; the HTML rendering extension only supports UTF-8.

> [!NOTE] The default e-mail delivery extension does not provide support for digitally signing or encrypting outgoing mail messages.

## Configuring a Report Server for Local or Remote SMTP Service

You can use a local SMTP service or a remote SMTP server or forwarder to support e-mail delivery. If you have access to an existing remote SMTP server, you should consider using it. If there is no SMTP server available or if you subsequently encounter report delivery errors that can be attributed to computer connection failures, you should switch to using a local SMTP service. Details about how to configure a report server for local or remote service are provided further on in this topic.

## Setting Configuration Options for E-Mail Delivery
Before you can use Report Server e-mail delivery, you must set configuration values that provide information about which SMTP server to use.

To configure a report server for e-mail delivery, do the following:

- Use the Reporting Services Configuration Manager if you are specifying just an SMTP server and a user account that has permission to send e-mail. These are the minimum settings that are required for configuring the Report Server e-mail delivery extension. For more information, see [E-Mail Delivery in Reporting Services](../../Topics\TopicNameNotContainA/E-Mail-Delivery-in-Reporting-Services.md).

- (Optionally) Use a text editor to specify additional settings in the RSreportserver.config file. This file contains all of the configuration settings for Report Server e-mail delivery. Specifying additional settings in these files is required if you are using a local SMTP server or if you are restricting e-mail delivery to specific hosts. For more information about finding and modifying configuration files, see [Modify a Reporting Services Configuration File (RSreportserver.config)](Modify%20a%20Reporting%20Services%20Configuration%20File%20\(RSreportserver.config\).md) in SQL Server Books Online.

> [!NOTE] Report server e-mail settings are based on CDO. If you want more detail about specific settings, you can refer to the CDO production documentation.

## Configure report server e-mail using the Reporting Services Configuration Manager

1. If using the report server service account for authentication, verify that the service account has **Send As** permissions on the SMTP server.

1. Start the Reporting Services Configuration Manager and connect to the report server instance.

2. In **Sender Address**, enter the name an account that has permission to send e-mail from the SMTP server.

2. On the Email Settings page, enter the name of the SMTP server. This value can be an IP address, a NetBIOS name of a computer on your corporate intranet, or a fully qualified domain name.

Click Apply.


## Example Report Server E-Mail Configuration
The following example illustrates the settings in the RSreportserver.config file for a remote SMTP server. To read about the setting descriptions and valid values, see RSReportServer Configuration File in SQL Server Books Online or the CDO product documentation.

```
<RSEmailDPConfiguration>
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>
     <SMTPServerPort></SMTPServerPort>
     <SMTPAccountName></SMTPAccountName>
     <SMTPConnectionTimeout></SMTPConnectionTimeout>
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>
     <SMTPUseSSL></SMTPUseSSL>
     <SendUsing>2</SendUsing>
     <SMTPAuthenticate></SMTPAuthenticate>
     <From>my-rs-email-account@Adventure-Works.com</From>
     <EmbeddedRenderFormats>
          <RenderingExtension>MHTML</RenderingExtension>
     </EmbeddedRenderFormats>
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>
     <ExcludedRenderFormats>
          <RenderingExtension>HTMLOWC</RenderingExtension>
          <RenderingExtension>NULL</RenderingExtension>
     </ExcludedRenderFormats>
     <SendEmailToUserAlias>True</SendEmailToUserAlias>
     <DefaultHostName></DefaultHostName>
     <PermittedHosts>
          <HostName>Adventure-Works.com</HostName>
          <HostName>hotmail.com</HostName>
     </PermittedHosts>
</RSEmailDPConfiguration>
```
## Configuration Options for Setting the To: Field in a Message
User-defined subscriptions that are created according to the permissions granted by the Manage individual subscriptions task contain a pre-set user name that is based on the domain user account. When the user creates the subscription, the recipient name in the **To:** field is self-addressed using the domain user account of the person creating the subscription.

If you are using an SMTP server or forwarder that uses e-mail accounts that are different from the domain user account, the report delivery will fail when the SMTP server tries to deliver the report to that user.

To workaround this issue, you can modify configuration settings that allow users to enter a name in the **To:** field:

1. Open RSReportServer.config with a text editor.

2. Set **SendEmailToUserAlias** to **False**.

3. Set **DefaultHostName** to the Domain Name System (DNS) name or IP address of the SMTP server or forwarder.

4. Save the file.

## Configuration Options for Remote SMTP Service
The connection between the report server and an SMTP server or forwarder is determined by the following configuration settings:

- **SendUsing** specifies a method for sending messages. You can choose between a network SMTP service or a local SMTP service pickup directory. To use a remote SMTP service, this value must be set to **2** in the RSReportServer.config file.
- SMTPServer specifies the remote SMTP server or forwarder. This value is a required value if you are using a remote SMTP server or forwarder.
- **From** sets the value that appears in the **From:** line of an e-mail message. This value is a required value if you are using a remote SMTP server or forwarder.

Other values that are used for remote SMTP service include the following (note that you do not need to specify these values unless you want to override the default values).

- **SMTPServerPort** is configured for port 25.
- **SMTPAuthenticate** specifies how the report server connects to the remote SMTP server. The default value is **0** (or no authentication). In this case, the connection is made through Anonymous access. Depending on your domain configuration, the report server and the SMTP server may need to be members of the same domain.
- To send e-mail to restricted distribution lists (for example, distribution lists that accept incoming messages only from authenticated accounts), set **SMTPAuthenticate** to **2**.

## Configuration Options for Local SMTP Service
Configuring a local SMTP service is useful if you are testing or troubleshooting report server e-mail delivery. The local SMTP service is not enabled by default.

The connection between the report server and a local SMTP server or forwarder is determined by the following configuration settings:

- **SendUsing** is set to **1**.
- **SMTPServerPickupDirectory** is set to a folder on the local drive.

  > [!NOTE] Be sure that you do not set SMTPServer if you are using a local SMTP server.

- **From** sets the value that appears in the **From:** line of an e-mail message. This value is required.








  
  Use the **E\-mail Settings** page of the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager to configure a Native mode report server for Simple Mail Transport Protocol \(SMTP\) e\-mail delivery. You can use the Report Server E\-Mail delivery extension to distribute [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] reports or report processing notifications through e\-mail subscriptions. The Report Server E\-Mail delivery extension requires an SMTP server and an e\-mail address to use in the From: field.  
  
 Additional configuration settings can be used to further customize e\-mail subscriptions, including settings that restrict mail server hosts and rendering extension availability. You cannot specify these settings in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Configuration Manager. To configure the additional settings, edit the **RSReportServer.config** file. For more information, see [Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83) and [Reporting Services Configuration Files](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Files.md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode.  
  
## Options  
 **Sender Address**  
 Specifies the e\-mail address to use in the **From:** field of a generated e\-mail. You must specify a user account that has permission to send mail from the SMTP server. The value you type for the “sender address” is saved in the `<From>` field in the rsreportserver.config file.  
  
 **Current SMTP Delivery Method**  
 Specifies that report server e\-mail is routed through an SMTP server. This is the only delivery method that you can specify in the Reporting Services Configuration Manager.  
  
 An alternative delivery method is to use a local SMTP service pickup directory. You can use this delivery method if a network SMTP service is not available. To specify a local SMTP service pickup directory, you must edit the RSReportServer.config file. If you edit the configuration file to use a local SMTP service pickup directory, the Reporting Services Configuration Manager sets the **Delivery method** option to *custom* to indicate that the delivery method is specified in the configuration file.  
  
 In the configuration file, the delivery method is set through the **SendUsing** configuration setting. For more information about specifying the **SendUsing** setting, see [Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83).  
  
 **SMTP Server**  
 Specify the SMTP server or gateway to use. You can use a local server or an SMTP server on your network.  
  
## See Also  
[Reporting Services Configuration Manager (Native Mode)](Reporting%20Services%20Configuration%20Manager%20\(Native%20Mode\).md)
  
  