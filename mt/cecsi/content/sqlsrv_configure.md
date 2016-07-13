---
title: sqlsrv_configure
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - sqlsrv_configure
apitype: NA
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
manager:jhubbard
translation.priority.ht: 
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
# sqlsrv_configure
Changes the settings for error handling and logging options.  
  
## Syntax  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### Parameters  
*$setting*: The name of the setting to be configured. See table below for list of settings.  
  
*$value*: The value to be applied to the setting specified in the *$setting* parameter. The possible values for this parameter depend on which setting is specified. The following table lists the possible combinations:  
  
|Setting|Possible values for $value parameter \(integer equivalent in parentheses\)|Default value|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|A non negative number up to the PHP memory limit.<br /><br />Zero \(0\) means no limit to the buffer size.|10240|  
|LogSeverity<sup>2</sup>|SQLSRV\_LOG\_SEVERITY\_ALL \(\-1\)<br /><br />SQLSRV\_LOG\_SEVERITY\_ERROR \(1\)<br /><br />SQLSRV\_LOG\_SEVERITY\_NOTICE \(4\)<br /><br />SQLSRV\_LOG\_SEVERITY\_WARNING \(2\)|SQLSRV\_LOG\_SEVERITY\_ERROR \(1\)|  
|LogSubsystems<sup>2</sup>|SQLSRV\_LOG\_SYSTEM\_ALL \(\-1\)<br /><br />SQLSRV\_LOG\_SYSTEM\_CONN \(2\)<br /><br />SQLSRV\_LOG\_SYSTEM\_INIT \(1\)<br /><br />SQLSRV\_LOG\_SYSTEM\_OFF \(0\)<br /><br />SQLSRV\_LOG\_SYSTEM\_STMT \(4\)<br /><br />SQLSRV\_LOG\_SYSTEM\_UTIL \(8\)|SQLSRV\_LOG\_SYSTEM\_OFF \(0\)|  
|WarningsReturnAsErrors<sup>3</sup>|**true** \(1\) or **false** \(0\)|**true** \(1\)|  
  
## Return Value  
If **sqlsrv\_configure** is called with an unsupported setting or value, the function returns **false**. Otherwise, the function returns **true**.  
  
## Remarks  
\(1\) For more information about client\-side queries, see [Cursor Types &#40;SQLSRV Driver&#41;](../content/Cursor-Types--SQLSRV-Driver-.md).  
  
\(2\) For more information about logging activity, see [Logging Activity](../content/Logging-Activity.md).  
  
\(3\) For more information about configuring error and warning handling, see [How to: Configure Error and Warning Handling Using the SQLSRV Driver](../Topic/How%20to:%20Configure%20Error%20and%20Warning%20Handling%20Using%20the%20SQLSRV%20Driver.md).  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[Programming Guide for PHP SQL Driver](../content/Programming-Guide-for-PHP-SQL-Driver.md) 
  
