---
title: sqlsrv_get_config
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - sqlsrv_get_config
apitype: NA
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
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
# sqlsrv_get_config
Returns the current value of the specified configuration setting.  
  
## Syntax  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### Parameters  
*$setting*: The configuration setting for which the value is returned. For a list of configurable settings, see [sqlsrv_configure](../content/sqlsrv_configure.md).  
  
## Return Value  
The value of the setting specified by the *$setting* parameter. If an invalid setting is specified, **false** is returned and an error is added to the error collection.  
  
## Remarks  
If **false** is returned by **sqlsrv\_get\_config**, you must call [sqlsrv_errors](../content/sqlsrv_errors.md) to determine if an error occurred or if **false** is the value of the setting specified by the *$setting* parameter.  
  
## See Also  
[SQLSRV Driver API Reference](../content/SQLSRV-Driver-API-Reference.md)  
[sqlsrv_configure](../content/sqlsrv_configure.md)  
[sqlsrv_errors](../content/sqlsrv_errors.md)  
  
