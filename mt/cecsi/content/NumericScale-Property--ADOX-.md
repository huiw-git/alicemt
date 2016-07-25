---
title: "NumericScale Property (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 573ee5d1-57c7-4a27-be79-a0e12944ad9b
caps.latest.revision: 10
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# NumericScale Property (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the scale of a numeric value in the column.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets and returns a <legacyBold>Byte</legacyBold> value that is the scale of data values in the column when the <legacyLink xlink:href="5c6718b6-f728-478a-8afb-5d17b0a91d1f">Type</legacyLink> property is <legacyBold>adNumeric</legacyBold> or <legacyBold>adDecimal</legacyBold>. <legacyBold>NumericScale</legacyBold> is ignored for all other data types.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The default value is zero (0).</para>
      <para>
        <legacyBold>NumericScale</legacyBold> is read-only for <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> objects already appended to a collection.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ea2ec614-34c8-41b7-8ebd-063798bd56b4">ADOX Code Example: NumericScale and Precision Properties Example (VB)</link>
<link xlink:href="5c6718b6-f728-478a-8afb-5d17b0a91d1f">Type Property (Column)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>