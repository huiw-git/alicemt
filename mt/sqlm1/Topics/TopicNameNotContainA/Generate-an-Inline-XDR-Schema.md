---
title: Generate an Inline XDR Schema
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
---
# Generate an Inline XDR Schema
  The **XMLDATA** directive in FOR XML returns an inline XDR schema together with the query result. However, the XDR schema does not support all the new data types and other enhancements introduced in [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)] and later versions. Instead, you can request an inline XSD schema by using [the XMLSCHEMA directive](../../Topics\TopicNameNotContainA/Generate-an-Inline-XSD-Schema.md).  
  
> [!IMPORTANT]  
>  The XMLDATA directive to the FOR XML option is deprecated. Use XSD generation in the case of RAW and AUTO modes. There is no replacement for the XMLDATA directive in EXPLICIT mode. [!INCLUDE[ssNoteDepFutureAvoid](../../Token\Other/ssNoteDepFutureAvoid_md.md)]  
  
 Also note the following about the inline XDR schema support:  
  
-   If the FOR XML query result includes columns of **xml** type and you request an inline XDR schema, an error is returned. Inline XDR does not support these types.  
  
-   The **\(n\)varchar\(max\)** and **\(n\)varbinary\(max\)** types will be mapped to **\(n\)varchar\(n\)** and **varbinary\(n\)**, respectively.  
  
-   When compatibility mode is set to 90 or higher, **timestamp** values are considered as **varbinary\(8\)** data, are treated like binary data, and are returned in the result as follows:  
  
    -   Base 64 encoding is used when **binary base64** is specified.  
  
    -   URL encoding is used in AUTO mode when **binary base64** is not specified.  
  
  