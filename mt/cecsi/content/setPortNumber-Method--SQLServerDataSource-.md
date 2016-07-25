---
title: "setPortNumber Method (SQLServerDataSource)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setPortNumber
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: 10
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
# setPortNumber Method (SQLServerDataSource)
  Sets the port number to be used to communicate with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)].  
  
## Syntax  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### Parameters  
 *portNumber*  
  
 An **int** value that contains the port number.  
  
## Remarks  
 The port number is the TCP/IP port number that is used when opening a socket connection to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)]. If the portNumber property is not set, the [getPortNumber](../content/getPortNumber-Method--SQLServerDataSource-.md) method returns the default value of 1433.  
  
> [!NOTE]  
>  The setPortNumber method does not do any range checking on the port value passed in. You can pass a port number that is not valid, like 99999, without triggering an error.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  