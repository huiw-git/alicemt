---
title: Errors and Events Reference (Integration Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf4f0f14-8087-42d7-9b67-e4929228abd6
---
# Errors and Events Reference (Integration Services)
  This section of the documentation contains information about several errors and events related to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. Cause and resolution information is included for error messages.  
  
 For more information about [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] error messages, including a list of most [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] errors and their descriptions, see [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md). However, the list currently does not include troubleshooting information.  
  
> [!IMPORTANT]  
>  Many of the error messages that you may see when you are working with [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] come from other components. These may include OLE DB providers, other database components such as the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] , or other services or components such as the file system, the SMTP server, or Microsoft Message Queueing. To find information about these external error messages, see the documentation specific to the component.  
  
## Error Messages  
  
|Symbolic name of error|Description|  
|----------------------------|-----------------|  
|DTS\_E\_CACHELOADEDFROMFILE|Indicates that the package cannot run because a Cache Transform transformation is trying to write data to the in\-memory cache. However, a Cache connection manager has already loaded a cache file into the in\-memory cache.|  
|DTS\_E\_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER|Indicates that the package cannot run because a specified connection failed.|  
|DTS\_E\_CANNOTCONVERTBETWEENUNICODEANDNONUNICODESTRINGCOLUMN|Indicates that a data flow component is trying to pass Unicode string data to another component that expects non\-Unicode string data in the corresponding column, or vice versa.|  
|DTS\_E\_CANNOTCONVERTBETWEENUNICODEANDNONUNICODESTRINGCOLUMNS|Indicates that a data flow component is trying to pass Unicode string data to another component that expects non\-Unicode string data in the corresponding column, or vice versa.|  
|DTS\_E\_CANTINSERTCOLUMNTYPE|Indicates that the column cannot be added to the database table because the conversion between the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] column data type and the database column data type is not supported.|  
|DTS\_E\_CONNECTIONNOTFOUND|Indicates that the package cannot run because the specified connection manager cannot be found.|  
|DTS\_E\_CONNECTIONREQUIREDFORMETADATA|Indicates that [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer must connect to a data source to retrieve new or updated metadata for a source or destination, and that it is unable to connect to the data source.|  
|DTS\_E\_MULTIPLECACHEWRITES|Indicates that the package cannot run because a Cache Transform transformation is trying to write data to the in\-memory cache. However, another Cache Transform transformation has already written to the in\-memory cache.|  
|DTS\_E\_PRODUCTLEVELTOLOW|Indicates that the package cannot run because the appropriate version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] is not installed.|  
|DTS\_E\_READNOTFILLEDCACHE|Indicates that a Lookup transformation is trying to read data from the in\-memory cache at the same time that a Cache Transform transformation is writing data to the cache.|  
|DTS\_E\_UNPROTECTXMLFAILED|Indicates that the system did not decrypt a protected XML node.|  
|DTS\_E\_WRITEWHILECACHEINUSE|Indicates that a Cache Transform transformation is trying to write data to the in\-memory cache at the same time that a Lookup transformation is reading data from the in\-memory cache.|  
|DTS\_W\_EXTERNALMETADATACOLUMNSOUTOFSYNC|Indicates that the column metadata in the data source does not match the column metadata in the source or destination component that is connected to the data source.|  
  
## Events \(SQLISPackage\)  
 For more information, see [Events Logged by an Integration Services Package](../../Topics\TopicNameNotContainA/Events-Logged-by-an-Integration-Services-Package.md).  
  
|Event|Description|  
|-----------|-----------------|  
|SQLISPackage\_12288|Indicates that a package started.|  
|SQLISPackage\_12289|Indicates that a package has finished running successfully.|  
|SQLISPACKAGE\_12291|Indicates that a package was unable to finish running and has stopped.|  
|SQLISPackage\_12546|Indicates that a task or other executable in a package has finished its work.|  
|SQLISPackage\_12549|Indicates that a warning message was raised in a package.|  
|SQLISPackage\_12550|Indicates that an error message was raised in a package.|  
|SQLISPackage\_12551|Indicates that a package did not finish its work and stopped.|  
|SQLISPackage\_12557|Indicates that a package has finished running.|  
  
## Events \(SQLISService\)  
 For more information, see [Events Logged by the Integration Services Service](../../Topics\TopicNameNotContainA/Events-Logged-by-the-Integration-Services-Service.md).  
  
|Event|Description|  
|-----------|-----------------|  
|SQLISService\_256|Indicates that the service is about to start.|  
|SQLISService\_257|Indicates that the service has started.|  
|SQLISService\_258|Indicates that the service is about to stop.|  
|SQLISService\_259|Indicates that the service has stopped.|  
|SQLISService\_260|Indicates that the service tried to start, but could not.|  
|SQLISService\_272|Indicates that the configuration file does not exist at the specified location.|  
|SQLISService\_273|Indicates that the configuration file could not be read or is not valid.|  
|SQLISService\_274|Indicates that the registry entry that contains the location of the configuration file does not exist or is empty.|  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)  
  
  