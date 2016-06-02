---
title: Term Extraction Transformation Editor (Advanced Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
---
# Term Extraction Transformation Editor (Advanced Tab)
  Use the **Advanced** tab of the **Term Extraction Transformation Editor** dialog box to specify properties for the extraction such as frequency, length, and whether to extract words or phrases.  
  
 To learn more about the Term Extraction transformation, see [Term Extraction Transformation](../../Topics\TopicNameNotContainA/Term-Extraction-Transformation.md).  
  
## Options  
 **Noun**  
 Specify that the transformation extracts individual nouns only.  
  
 **Noun phrase**  
 Specify that the transformation extracts noun phrases only.  
  
 **Noun and noun phrase**  
 Specify that the transformation extracts both nouns and noun phrases.  
  
 **Frequency**  
 Specify that the score is the frequency of the term.  
  
 **TFIDF**  
 Specify that the score is the TFIDF value of the term. The TFIDF score is the product of Term Frequency and Inverse Document Frequency, defined as: TFIDF of a Term T \= \(frequency of T\) \* log\( \(\#rows in Input\) \/ \(\#rows having T\) \)  
  
 **Frequency threshold**  
 Specify the number of times a word or phrase must occur before extracting it. The default value is 2.  
  
 **Maximum length of term**  
 Specify the maximum length of a phrase in words. This option affects noun phrases only. The default value is 12.  
  
 **Use case\-sensitive term extraction**  
 Specify whether to make the extraction case\-sensitive. The default is **False**.  
  
 **Configure Error Output**  
 Use the [Configure Error Output](../../Topics\TopicNameNotContainA/Configure-Error-Output.md) dialog box to specify error handling for rows that cause errors.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../Topic/Term%20Extraction%20Transformation%20Editor%20\(Term%20Extraction%20Tab\).md)   
 [Term Extraction Transformation Editor &#40;Exclusion Tab&#41;](../Topic/Term%20Extraction%20Transformation%20Editor%20\(Exclusion%20Tab\).md)   
 [Term Lookup Transformation](../../Topics\TopicNameNotContainA/Term-Lookup-Transformation.md)  
  
  