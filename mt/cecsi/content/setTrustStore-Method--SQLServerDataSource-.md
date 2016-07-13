---
title: setTrustStore Method (SQLServerDataSource)
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
  - setTrustStore Method (SQLServerDataSource)
apilocation: 
  - setTrustStore Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: bab5485d-4547-426c-adbe-44e2b5702d1d
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
# setTrustStore Method (SQLServerDataSource)
  Sets the path \(including file name\) to the certificate trustStore file.  
  
## Syntax  
  
```  
  
public void setTrustStore(java.lang.String trustStore)  
```  
  
#### Parameters  
 *trustStore*  
  
 A **String** that contains the path \(including file name\) to the certificate trustStore file.  
  
## Remarks  
 If the trustStore property is unspecified or set to null, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will rely on the trust manager factory's look up rules to determine which certificate store to use. The default SunX509 TrustManagerFactory tries to find the trust material in the following locations in this order:  
  
-   1. A file specified by the "javax.net.ssl.trustStore" Java Virtual Machine \(JVM\) system property.  
  
-   2. "\<java\-home\>\/lib\/security\/jssecacerts" file.  
  
-   3. "\<java\-home\>\/lib\/security\/cacerts" file.  
  
 For more information, see the SunX509 TrustManager Interface documentation on the Sun Microsystems Web site.  
  
 If the trustStore property is set to a string or an empty string "", the driver will use that value to find the trustStore file to validate the server SSL certificate.  
  
 The trustStorePassword property can be specified along with the trustStore property and its value is used to open the trustStore file. For more information, see [setTrustStorePassword](../content/setTrustStorePassword-Method--SQLServerDataSource-.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  