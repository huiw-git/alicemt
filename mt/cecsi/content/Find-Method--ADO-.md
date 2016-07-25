---
title: "Find Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 55c9810a-d8ca-46c2-a9dc-80e7ee7aa188
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
# Find Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Searches a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> for the row that satisfies the specified criteria. Optionally, the direction of the search, starting row, and offset from the starting row may be specified. If the criteria is met, the current row position is set on the found record; otherwise, the position is set to the end (or start) of the <legacyBold>Recordset</legacyBold>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Find</legacyBold> <parameterReference>(Criteria, SkipRows, SearchDirection, Start)</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Criteria</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> value that contains a statement specifying the column name, comparison operator, and value to use in the search.</para>
        </definition>
        <definedTerm> <legacyItalic>SkipRows</legacyItalic> </definedTerm>
        <definition>
          <para>Optional<legacyItalic>. </legacyItalic>A <legacyBold>Long</legacyBold> value, whose default value is zero, that specifies the row offset from the current row or <legacyItalic>Start </legacyItalic>bookmark to begin the search. By default, the search will start on the current row.</para>
        </definition>
        <definedTerm> <legacyItalic>SearchDirection</legacyItalic> </definedTerm>
        <definition>
          <para>Optional<legacyItalic>. </legacyItalic>A <legacyLink xlink:href="81272ae3-2165-4f4e-adfe-9ede0368cb17">SearchDirectionEnum</legacyLink> value that specifies whether the search should begin on the current row or the next available row in the direction of the search. An unsuccessful search stops at the end of the <legacyBold>Recordset</legacyBold> if the value is <legacyBold>adSearchForward</legacyBold>. An unsuccessful search stops at the start of the <legacyBold>Recordset</legacyBold> if the value is <legacyBold>adSearchBackward</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>Start</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Variant</legacyBold> bookmark that functions as the starting position for the search.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Only a single-column name may be specified in <legacyItalic>criteria</legacyItalic>. This method does not support multi-column searches.</para>
      <para>The comparison operator in <legacyItalic>Criteria</legacyItalic> may be "<legacyBold>&gt;</legacyBold>" (greater than), "<legacyBold>&lt;</legacyBold>" (less than), "=" (equal), "&gt;=" (greater than or equal), "&lt;=" (less than or equal), "&lt;&gt;" (not equal), or "like" (pattern matching).</para>
      <para>The value in <legacyItalic>Criteria</legacyItalic> may be a string, floating-point number, or date. String values are delimited with single quotes or "#" (number sign) marks (for example, "state = 'WA'" or "state = #WA#"). Date values are delimited with "#" (number sign) marks (for example, "start_date &gt; #7/22/97#"). These values can contain hours, minutes, and seconds to indicate time stamps, but should not contain milliseconds or errors will occur.</para>
      <para>If the comparison operator is "like", the string value may contain an asterisk (*) to find one or more occurrences of any character or substring. For example, "state like 'M*'" matches Maine and Massachusetts. You can also use leading and trailing asterisks to find a substring contained within the values. For example, "state like '*as*'" matches Alaska, Arkansas, and Massachusetts.</para>
      <para>Asterisks can be used only at the end of a criteria string, or at both the beginning and end of a criteria string, as shown above. You cannot use the asterisk as a leading wildcard ('*str'), or as an embedded wildcard ('s*r'). This will cause an error.</para>
      <alert class="note">
        <para>An error will occur if a current row position is not set before calling <legacyBold>Find</legacyBold>. Any method that sets row position, such as <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>, should be called before calling <legacyBold>Find</legacyBold>.</para>
      </alert>
      <alert class="note">
        <para>If you call the <legacyBold>Find</legacyBold> method on a recordset, and the current position in the recordset is at the last record or end of file (EOF), you will not find anything. You need to call the <legacyBold>MoveFirst</legacyBold> method to set the current position/cursor to the beginning of the recordset.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="bbf27dcc-9815-4e2f-8ea8-b8c9fe6dedd6">Visual Basic Example</link>
<link xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index Property</link>
<link xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize Property — Dynamic (ADO)</link>
<link xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>