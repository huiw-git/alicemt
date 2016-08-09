---
title: "Fuzzy Lookup Transformation Editor (Advanced Tab)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
caps.latest.revision: 28
manager: jhubbard
---
# Fuzzy Lookup Transformation Editor (Advanced Tab)
Use the **Advanced** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set parameters for the fuzzy lookup.  
  
 To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](../../Topics/TopicNameNotContainA/Fuzzy-Lookup-Transformation.md).  
  
## Options  
 **Maximum number of matches to output per lookup**  
 Specify the maximum number of matches the transformation can return for each input row. The default is **1**.  
  
 **Similarity threshold**  
 Set the similarity threshold at the component level by using the slider. The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match. Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.  
  
 **Token delimiters**  
 Specify the delimiters that the transformation uses to tokenize column values.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics/TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Fuzzy Lookup Transformation Editor (Reference Table Tab)](../../Topics/TopicNameNotContainA/Fuzzy-Lookup-Transformation-Editor--Reference-Table-Tab-.md)   
 [Fuzzy Lookup Transformation Editor (Columns Tab)](../../Topics/TopicNameNotContainA/Fuzzy-Lookup-Transformation-Editor--Columns-Tab-.md)