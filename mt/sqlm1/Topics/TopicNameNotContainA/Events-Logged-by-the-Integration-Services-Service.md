---
title: Events Logged by the Integration Services Service
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4122dcf-f16f-47a0-93a2-ffa3d0d4f9cf
---
# Events Logged by the Integration Services Service
  The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service logs various messages to the Windows Application event log. The service logs these messages when the service starts, when the service stops, and when certain problems occur.  
  
 This topic provides information about the common event messages that the service logs to the Application event log. The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service logs all the messages described in this topic with an Event Source of SQLISService.  
  
 For general information about the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, see [Integration Services Service &#40;SSIS Service&#41;](../Topic/Integration%20Services%20Service%20\(SSIS%20Service\).md).  
  
## Messages about the Status of the Service  
 When you select [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] for installation, the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service is installed and started, and its Startup Type is set to Automatic.  
  
|Event ID|Symbolic Name|Text|Notes|  
|--------------|-------------------|----------|-----------|  
|256|DTS\_MSG\_SERVER\_STARTING|Starting [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service.|The service is about to start.|  
|257|DTS\_MSG\_SERVER\_STARTED|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service started.|The service started.|  
|260|DTS\_MSG\_SERVER\_START\_FAILED|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service failed to start.%nError: %1|The service was not able to start. This inability to start might be the result of a damaged installation or an inappropriate service account.|  
|258|DTS\_MSG\_SERVER\_STOPPING|Stopping [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service.%n%nStop all running packages on exit: %1|The service is stopping, and if you configure the service to do this, will stop all running packages. You can set a true or false value in the configuration file that determines whether the service stops running packages when the service itself stops. The message for this event includes the value of this setting.|  
|259|DTS\_MSG\_SERVER\_STOPPED|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service stopped.%nServer version %1|The service stopped.|  
  
## Messages about the Configuration File  
 Settings for the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service are stored in an XML file that you can modify. For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](../Topic/Configuring%20the%20Integration%20Services%20Service%20\(SSIS%20Service\).md).  
  
|Event ID|Symbolic Name|Text|Notes|  
|--------------|-------------------|----------|-----------|  
|274|DTS\_MSG\_SERVER\_MISSING\_CONFIG\_REG|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service: %nRegistry setting specifying configuration file does not exist. %nAttempting to load default config file.|The Registry entry that contains the path of the configuration file does not exist or is empty.|  
|272|DTS\_MSG\_SERVER\_MISSING\_CONFIG|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service configuration file does not exist.%nLoading with default settings.|The configuration file itself does not exist at the specified location.|  
|273|DTS\_MSG\_SERVER\_BAD\_CONFIG|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service configuration file is incorrect.%nError reading config file: %1%n%nLoading server with default settings.|The configuration file could not be read or is not valid. This error might be the result of an XML syntax error in the file.|  
  
## Other Messages  
  
|Event ID|Symbolic Name|Text|Notes|  
|--------------|-------------------|----------|-----------|  
|336|DTS\_MSG\_SERVER\_STOPPING\_PACKAGE|[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Service: stopping running package.%nPackage instance ID: %1%nPackage ID: %2%nPackage name: %3%nPackage description: %4%nPackage|The service is trying to stop a running package. You can monitor and stop running packages in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]. For information about how to manage packages in [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)], see [Package Management &#40;SSIS Service&#41;](../Topic/Package%20Management%20\(SSIS%20Service\).md).|  
  
## Related Tasks  
 For information about how to view log entries, see [View Log Entries in the Log Events Window](../../Topics\TopicNameNotContainA/View-Log-Entries-in-the-Log-Events-Window.md)  
  
## See Also  
 [Events Logged by an Integration Services Package](../../Topics\TopicNameNotContainA/Events-Logged-by-an-Integration-Services-Package.md)  
  
  