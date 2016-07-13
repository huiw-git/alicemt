---
title: setURL Method (SQLServerDataSource)
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
  - SQLServerDataSource.setURL
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: bea70100-ac98-4625-8748-ef7cc0b111ea
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
# setURL Method (SQLServerDataSource)
  Sets the URL that is used to connect to the data source.  
  
## Syntax  
  
```  
  
public void setURL(java.lang.String url)  
```  
  
#### Parameters  
 *url*  
  
 A **String** that contains the URL.  
  
## Remarks  
 For security reasons, you should not include the password in the URL supplied to the setURL method. The reason for this is that third\-party Java Application Servers will very often display the value set for the URL property in their data source configuration user interface. Instead, use the [setPassword](../content/setPassword-Method--SQLServerDataSource-.md) method to set the password value. Java Application Servers will not display a password that is set in their data source in the configuration user interface.  
  
> [!NOTE]  
>  If the setURL method is not called before calling the [getURL](../content/getURL-Method--SQLServerDataSource-.md) method, getURL returns the default value of "jdbc:sqlserver:\/\/".  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  