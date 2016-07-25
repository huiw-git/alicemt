---
title: "AppendChunk Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: c648b5a8-d4f1-4d16-836e-3957feb03617
caps.latest.revision: 13
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
# AppendChunk Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Appends data to a large text or binary data <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>, or to a <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
object.AppendChunk Data</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>object</legacyItalic> </definedTerm>
        <definition>
          <para>A <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Data</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Variant</legacyBold> that contains the data to append to the object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> method on a <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> object to fill it with long binary or character data. In situations where system memory is limited, you can use the <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> method to manipulate long values in portions rather than in their entirety.</para>
    </content>
    <sections>
      <section>
        <title>Field</title>
        <content>
          <para>If the <legacyBold>adFldLong</legacyBold> bit in the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property of a <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> object is set to <languageKeyword>true</languageKeyword>, you can use the <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> method for that field.</para>
          <para>The first <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> call on a <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> object writes data to the field, overwriting any existing data. Subsequent <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> calls add to existing data. If you are appending data to one field and then you set or read the value of another field in the current record, ADO assumes that you are finished appending data to the first field. If you call the <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> method on the first field again, ADO interprets the call as a new <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> operation and overwrites the existing data. Accessing fields in other <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects that are not clones of the first <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object will not disrupt <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> operations.</para>
          <para>If there is no current record when you call <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> on a <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> object, an error occurs.</para>
          <alert class="note">
            <para>The <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> method does not operate on <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> objects of a <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object_ADO</link> object. It does not perform any operation and will produce a run-time error.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Parameter</title>
        <content>
          <para>If the <legacyBold>adParamLong</legacyBold> bit in the <unmanagedCodeEntityReference>Attributes</unmanagedCodeEntityReference> property of a <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> object is set to <languageKeyword>true</languageKeyword>, you can use the <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> method for that parameter.</para>
          <para>The first <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> call on a <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> object writes data to the parameter, overwriting any existing data. Subsequent <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> calls on a <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> object add to existing parameter data. An <unmanagedCodeEntityReference>AppendChunk</unmanagedCodeEntityReference> call that passes a null value discards all of the parameter data.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="c07862b5-e466-46bd-910b-59ac96709cb9">AppendChunk and GetChunk Methods Example (VB)</link>
<link xlink:href="51aa99be-d5ca-46ac-8b3f-1b03ce4f0b2a">AppendChunk and GetChunk Methods Example (VC++)</link>
<link xlink:href="c21d0e82-81b3-4b06-a91e-77efad17c093">AppendChunk and GetChunk Methods Example (VJ++)</link>
<link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property (ADO)</link>
<link xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk Method (ADO)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>