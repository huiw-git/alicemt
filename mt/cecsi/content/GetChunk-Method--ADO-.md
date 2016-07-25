---
title: "GetChunk Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
caps.latest.revision: 11
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
# GetChunk Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns all, or a portion, of the contents of a large text or binary data <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>variable</parameterReference> = <parameterReference>field</parameterReference><legacyBold>.GetChunk(</legacyBold><parameterReference>Size</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyBold>Variant</legacyBold>.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Size</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> expression that is equal to the number of bytes or characters that you want to retrieve.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>GetChunk</legacyBold> method on a <legacyBold>Field</legacyBold> object to retrieve part or all of its long binary or character data. In situations where system memory is limited, you can use the <legacyBold>GetChunk</legacyBold> method to manipulate long values in portions, rather than in their entirety.</para>
      <para>The data that a <legacyBold>GetChunk</legacyBold> call returns is assigned to <legacyItalic>variable</legacyItalic>. If <legacyItalic>Size</legacyItalic> is greater than the remaining data, the <legacyBold>GetChunk</legacyBold> method returns only the remaining data without padding <legacyItalic>variable</legacyItalic> with empty spaces. If the field is empty, the <legacyBold>GetChunk</legacyBold> method returns a null value.</para>
      <para>Each subsequent <legacyBold>GetChunk</legacyBold> call retrieves data starting from where the previous <legacyBold>GetChunk</legacyBold> call left off. However, if you are retrieving data from one field and then you set or read the value of another field in the current record, ADO assumes you have finished retrieving data from the first field. If you call the <legacyBold>GetChunk</legacyBold> method on the first field again, ADO interprets the call as a new <legacyBold>GetChunk</legacyBold> operation and starts reading from the beginning of the data. Accessing fields in other <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects that are not clones of the first <legacyBold>Recordset</legacyBold> object will not disrupt <legacyBold>GetChunk</legacyBold> operations.</para>
      <para>If the <legacyBold>adFldLong</legacyBold> bit in the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property of a <legacyBold>Field</legacyBold> object is set to <legacyBold>True</legacyBold>, you can use the <legacyBold>GetChunk</legacyBold> method for that field.</para>
      <para>If there is no current record when you use the <legacyBold>GetChunk</legacyBold> method on a <legacyBold>Field</legacyBold> object, error 3021 (no current record) occurs.</para>
      <alert class="note">
        <para>The <legacyBold>GetChunk</legacyBold> method does not operate on <legacyBold>Field</legacyBold> objects of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object. It does not perform any operation and will produce a run-time error.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="c07862b5-e466-46bd-910b-59ac96709cb9">Visual Basic Example</link>
<link xlink:href="51aa99be-d5ca-46ac-8b3f-1b03ce4f0b2a">Visual C++ Example</link>
<link xlink:href="c21d0e82-81b3-4b06-a91e-77efad17c093">Visual J++ Example</link>
<link xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk Method</link>
<link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>