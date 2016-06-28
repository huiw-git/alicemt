---
title: setSendStringParametersAsUnicode Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setSendStringParametersAsUnicode
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 49198d63-76cb-4843-8d04-e49b1fbb6916
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# setSendStringParametersAsUnicode Method (SQLServerDataSource)
  Sets a **boolean** value that indicates if sending string parameters to the server in UNICODE format is enabled.  
  
## Syntax  
  
```  
  
public void setSendStringParametersAsUnicode(boolean sendStringParametersAsUnicode)  
```  
  
#### Parameters  
 *sendStringParametersAsUnicode*  
  
 **true** if string parameters are sent to the server in UNICODE format. Otherwise, **false**.  
  
## Remarks  
 If the sendStringParametersAsUnicode property is set to **true**, which is the default value, string parameters are sent to the server in UNICODE format. If sendStringParametersAsUnicode is set to **false** string parameters are sent to the server in an ASCII\/MBCS format, not in UNICODE. If sendStringParametersAsUnicode is not set, [getSendStringParametersAsUnicode](../content/getSendStringParametersAsUnicode-Method--SQLServerDataSource-.md) returns the default value of **true**.  
  
 For more information about the sendStringParametersAsUnicode connection property, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  