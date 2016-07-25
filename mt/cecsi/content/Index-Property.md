---
title: "Index Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
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
# Index Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the name of the index currently in effect for a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value, which is the name of the index.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The index named by the <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference> property must have previously been declared on the base table underlying the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object. That is, the index must have been declared programmatically either as an ADOX <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink> object, or when the base table was created.</para>
      <para>A run-time error will occur if the index cannot be set. The <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference> property cannot be set under the following conditions:  </para>
      <list class="bullet">
        <listItem>
          <para>Within a <legacyLink xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">WillChangeRecordset</legacyLink> or <legacyBold>RecordsetChangeComplete</legacyBold> event handler.</para>
        </listItem>
        <listItem>
          <para>If the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is still executing an operation (which can be determined by the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property).</para>
        </listItem>
        <listItem>
          <para>If a filter has been set on the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> with the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property.</para>
        </listItem>
      </list>
      <para>The <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference> property can always be set successfully if the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is closed, but the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> will not open successfully, or the index will not be usable, if the underlying provider does not support indexes.</para>
      <para>If the index can be set, the current row position may change. This will cause an update to the <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink> property, and will fire the <legacyBold>WillChangeRecordset</legacyBold>, <legacyBold>RecordsetChangeComplete</legacyBold>, <legacyLink xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">WillMove</legacyLink>, and <legacyLink xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">MoveComplete</legacyLink> events.</para>
      <para>If the index can be set and the <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink> property is <legacyBold>adLockPessimistic</legacyBold> or <legacyBold>adLockOptimistic</legacyBold>, then an implicit <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> operation is performed. This releases the current and affected groups. Any existing filter is released, and the current row position is changed to the first row of the reordered <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
      <para>The <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference> property is used in conjunction with the <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink> method. If the underlying provider does not support the <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference> property, and thus the <unmanagedCodeEntityReference>Seek</unmanagedCodeEntityReference> method, consider using the <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method instead. Determine whether the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports indexes with the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink><legacyBold>(adIndex)</legacyBold> method.</para>
      <para>The built-in <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference> property is not related to the dynamic <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink> property, although they both deal with indexes.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="337c9eda-9ddf-49ac-94d3-b33114ba6224">Visual Basic Example</link>
<link xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index Object</link>
<link xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>