---
title: The &lt;xsd:redefine&gt; Element
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-xml
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
---
# The &lt;xsd:redefine&gt; Element
  The W3C XSD **redefine** element provides support for redefining schema components. However, support for this directive is potentially costly to performance and also requires that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] revalidate all instances of the **xml** data type associated with the redefined schema. Therefore, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not support this element. XML schemas that include the **\<xsd:redefine\>** element are rejected by the server.  
  
 To update a schema or its components, you can do the following instead:  
  
1.  Create a new XML Schema collection with the modified schema components.  
  
2.  Retype all **xml** data types \(XML DT\) that use the XML Schema collection to be redefined to use the new XML Schema collection instead. To do this, use the ALTER COLUMN option of the ALTER TABLE command for retyping columns, or change the XML Schema collection constraints on variables or parameters.  
  
3.  Drop the old version of the XML Schema collection.  
  
## See Also  
 [Requirements and Limitations for XML Schema Collections on the Server](../../Topics\TopicNameNotContainA/Requirements-and-Limitations-for-XML-Schema-Collections-on-the-Server.md)  
  
  