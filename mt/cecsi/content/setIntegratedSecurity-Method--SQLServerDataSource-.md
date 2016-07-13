---
title: setIntegratedSecurity Method (SQLServerDataSource)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setIntegratedSecurity
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
manager: jhubbard
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
# setIntegratedSecurity Method (SQLServerDataSource)
  Sets a **Boolean** value that indicates if the integratedSecurity property is enabled.  
  
## Syntax  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### Parameters  
 *enable*  
  
 **true** if integratedSecurity is enabled. Otherwise, **false**.  
  
## Remarks  
 Set to "**true**" to indicate that Windows credentials will be used by [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] to authenticate the user of the application. If "**true**", the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will search the local computer credential cache for credentials that have already been provided at the computer or network logon. If "**false**", the username and password must be supplied.  
  
> [!NOTE]  
>  This property is only supported on [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] Windows operating systems.  
  
 For more information about using integrated authentication, see [Building the Connection URL](../content/Building-the-Connection-URL.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  