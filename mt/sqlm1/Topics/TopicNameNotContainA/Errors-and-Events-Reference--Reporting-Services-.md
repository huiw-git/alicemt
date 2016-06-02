---
title: Errors and Events Reference (Reporting Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 818b4cc1-e65d-4f1a-bf7d-fe269e6dd739
---
# Errors and Events Reference (Reporting Services)
  This topic provides information about errors and events for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] log files also contain error information. For more information about the types of log files that are available and how to view the logs, see [Reporting Services Log Files and Sources](../../Topics\TopicNameNotContainA/Reporting-Services-Log-Files-and-Sources.md).  
  
## Cause and Resolution for Reporting Services Error Messages  
 Cause and resolution information is available for the errors most frequently searched for on the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Web sites. For more information, see [Cause and Resolution of Reporting Services Errors](../../Topics\TopicNameNotContainA/Cause-and-Resolution-of-Reporting-Services-Errors.md).  
  
## Report Server Events  
 The following report server events are recorded in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows application log.  
  
|Event ID|Type|Category|Source|Description|  
|--------------|----------|--------------|------------|-----------------|  
|106|Error|Scheduling|Report Server|SQL Server Agent must be running when you define a scheduled operation \(for example, report subscription and delivery\).|  
|[107](../Topic/Report%20Server%20Windows%20Service%20\(MSSQLServer\)%20107.md)|Error|Startup\/Shutdown|Report Server<br /><br /> Scheduling and Delivery Processor|*\<Source\>* cannot connect to the report server database. For more information, see [Report Server Windows Service &#40;MSSQLServer&#41; 107](../Topic/Report%20Server%20Windows%20Service%20\(MSSQLServer\)%20107.md).|  
|108|Error|Extension|Report Server<br /><br /> Report Manager|*\<Source\>* cannot load a delivery, data processing, or rendering extension.<br /><br /> Most likely, this is the result of an incomplete deployment or removal of an extension. For more information, see [Deploying a Data Processing Extension](../Topic/Deploying%20a%20Data%20Processing%20Extension.md) and [Deploying a Delivery Extension](../Topic/Deploying%20a%20Delivery%20Extension.md).|  
|109|Information|Management|Report Server<br /><br /> Report Manager|A configuration file has been modified. For more information, see [Reporting Services Configuration Files](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Files.md).|  
|110|Warning|Management|Report Server<br /><br /> Report Manager|A setting in one of the configuration files has been modified such that it is no longer valid. A default value will be used instead. For more information, see [Reporting Services Configuration Files](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Files.md).|  
|111|Error|Logging|Report Server<br /><br /> Report Manager|*\<Source\>* cannot create the trace log. For more information, see [Report Server Service Trace Log](../../Topics\TopicNameNotContainA/Report-Server-Service-Trace-Log.md).|  
|112|Warning|Security|Report Server|The report server has detected a possible denial of service attack. For more information, see [Reporting Services Security and Protection](../../Topics\TopicNameNotContainA/Reporting-Services-Security-and-Protection.md).|  
|113|Error|Logging|Report Server|The report server cannot create a performance counter.|  
|114|Error|Startup\/Shutdown|Report Manager|Report Manager cannot connect to the Report Server service.|  
|115|Warning|Scheduling|Scheduling and Delivery Processor|A scheduled task in the SQL Server Agent queue has been modified or deleted.|  
|116|Error|Internal|Report Server<br /><br /> Report Manager<br /><br /> Scheduling and Delivery Processor|An internal error occurred.|  
|117|Error|Startup\/Shutdown|Report Server|The report server database is an invalid version.|  
|118|Warning|Logging|Report Server<br /><br /> Report Manager|The trace log is not at the expected directory location; a new trace log will be created in the default directory. For more information, see [Report Server Service Trace Log](../../Topics\TopicNameNotContainA/Report-Server-Service-Trace-Log.md).|  
|119|Error|Activation|Report Server<br /><br /> Scheduling and Delivery Processor|*\<Source\>* has not been granted access to the contents of the report server database.|  
|120|Error|Activation|Report Server|The symmetric key cannot be decrypted. Most likely, the there has been a change to the account that the service runs as. For more information, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20and%20Manage%20Encryption%20Keys%20\(SSRS%20Configuration%20Manager\).md).|  
|121|Error|Startup\/Shutdown|Report Server|Remote Procedure Call \(RPC\) Service failed to start.|  
|122|Warning|Delivery|Scheduling and Delivery Processor|Scheduling and Delivery Processor cannot connect to the SMTP server that is used for e\-mail delivery. For more information about SMTP server connections, see [Configure a Report Server for E\-Mail Delivery \(SSRS Configuration Manager\)](assetId:///b838f970-d11a-4239-b164-8d11f4581d83).|  
|123|Warning|Logging|Report Server<br /><br /> Report Manager|The report server failed to write to the trace log. For more information about trace logs, see [Report Server Service Trace Log](../../Topics\TopicNameNotContainA/Report-Server-Service-Trace-Log.md).|  
|124|Information|Activation|Report Server|The Report Server service has been initialized. For more information, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../Topic/Initialize%20a%20Report%20Server%20\(SSRS%20Configuration%20Manager\).md).|  
|125|Information|Activation|Report Server|The key used for encrypting data was successfully extracted. For more information about keys, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20and%20Manage%20Encryption%20Keys%20\(SSRS%20Configuration%20Manager\).md).|  
|126|Information|Activation|Report Server|The key used for encrypting data was successfully applied. For more information about keys, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20and%20Manage%20Encryption%20Keys%20\(SSRS%20Configuration%20Manager\).md).|  
|127|Information|Activation|Report Server|Encrypted content was successfully removed from the report server database. For more information about deleting non\-recoverable encrypted data, see [Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20and%20Manage%20Encryption%20Keys%20\(SSRS%20Configuration%20Manager\).md).|  
|128|Error|Activation|Report Server|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] components from different editions cannot be used together.|  
|129|Error|Management|Report Server<br /><br /> Scheduling and Delivery Processor|An encrypted configuration file setting in cannot be decrypted.|  
|130|Error|Management|Report Server<br /><br /> Scheduling and Delivery Processor|*\<Source\>* cannot find the configuration file. Configuration files are required by the report server.|  
|131|Error|Security|Report Server<br /><br /> Scheduling and Delivery Processor|An encrypted user data value could not be decrypted.|  
|132|Error|Security|Report Server|A failure occurred during encryption of user data. The value cannot be saved.|  
|133|Error|Management|Report Server<br /><br /> Report Manager<br /><br /> Scheduling and Delivery Processor|A configuration file failed to load. This error may occur if the XML is not valid.|  
|134|Error|Management|Report Server|The report server failed to encrypt values for a setting in a configuration file.|  
  
## See Also  
 [Monitor Reporting Services Subscriptions](../../Topics\TopicNameNotContainA/Monitor-Reporting-Services-Subscriptions.md)   
 [Reporting Services Log Files and Sources](../../Topics\TopicNameNotContainA/Reporting-Services-Log-Files-and-Sources.md)  
  
  