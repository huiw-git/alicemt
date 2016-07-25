---
title: "National Character Set Support"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
caps.latest.revision: 15
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
# National Character Set Support
  The JDBC driver provides support for the JDBC 4.0 API, which includes new national character set conversion API methods. This support includes new setter, getter, and updater methods for **NCHAR**, **NVARCHAR**, **LONGNVARCHAR**, and **NCLOB** JDBC types.  
  
 The following is a list of new getter, setter, and updater methods to support the national character set conversion:  
  
-   [SQLServerPreparedStatement](../content/SQLServerPreparedStatement-Class.md): [setNString](../content/setNString-Method--int--java.lang.String-.md), [setNCharacterStream](../content/setNCharacterStream-Method--SQLServerPreparedStatement-.md), [setNClob](../content/setNClob-Method--SQLServerPreparedStatement-.md).  
  
-   [SQLServerCallableStatement](../content/SQLServerCallableStatement-Class.md): [getNClob](../content/getNClob-Method--SQLServerCallableStatement-.md), [getNString](../content/getNString-Method--SQLServerCallableStatement-.md), [getNCharacterStream](../content/getNCharacterStream-Method--SQLServerCallableStatement-.md), [setNString](../content/setNString-Method--SQLServerCallableStatement-.md), [setNCharacterStream](../content/setNCharacterStream-Method--SQLServerCallableStatement-.md), [setNClob](../content/setNClob-Method--SQLServerCallableStatement-.md).  
  
-   [SQLServerResultSet](../content/SQLServerResultSet-Class.md): [getNClob](../content/getNClob-Method--SQLServerResultSet-.md), [getNString](../content/getNString-Method--SQLServerResultSet-.md), [getNCharacterStream](../content/getNCharacterStream-Method--SQLServerResultSet-.md), [updateNClob](../content/updateNClob-Method--SQLServerResultSet-.md), [updateNString](../content/updateNString-Method--SQLServerResultSet-.md), [updateNCharacterStream](../content/updateNCharacterStream-Method--SQLServerResultSet-.md).  
  
> [!NOTE]  
>  You must set the classpath to include the sqljdbc4.jar file to use these methods in your application.  
  
 In order to send String parameters to the server in Unicode format, the applications should either use the new JDBC 4.0 national character methods; or set the **sendStringParametersAsUnicode** connection property to "**true**" when using the non-national character methods. The recommended way is to use the new JDBC 4.0 national character methods where possible. For more information about the **sendStringParametersAsUnicode** connection property, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
## See Also  
 [Understanding the JDBC Driver Data Types](../content/Understanding-the-JDBC-Driver-Data-Types.md)  
  
  