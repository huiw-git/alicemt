---
title: "CompareBookmarks Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
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
# CompareBookmarks Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Compares two bookmarks and returns an indication of their relative values.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>result = recordset</parameterReference>.<legacyBold>CompareBookmarks(</legacyBold><parameterReference>Bookmark1</parameterReference>, <parameterReference>Bookmark2</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyLink xlink:href="bc8f710d-0621-4673-8d8e-0361e44abed0">CompareEnum</legacyLink> value that indicates the relative row position of two records represented by their bookmarks.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>Bookmark1 </parameterReference></definedTerm>
        <definition>
          <para>The bookmark of the first row.</para>
        </definition>
        <definedTerm> <parameterReference>Bookmark2 </parameterReference></definedTerm>
        <definition>
          <para>The bookmark of the second row.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The bookmarks must apply to the same <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, or a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object and its <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">clone</legacyLink>. You cannot reliably compare bookmarks from different <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> objects, even if they were created from the same source or command. Nor can you compare bookmarks for a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object whose underlying provider does not support comparisons.</para>
      <para>A bookmark uniquely identifies a row in a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object. Use the <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink> property of the current row to obtain its bookmark.</para>
      <para>Because the data type of a bookmark is specific to each provider, ADO exposes it as a <languageKeyword>Variant</languageKeyword>. For example, SQL Server bookmarks are of type DBTYPE_R8 (<languageKeyword>Double</languageKeyword>). ADO would expose this type as a <languageKeyword>Variant</languageKeyword> with a subtype of <languageKeyword>Double</languageKeyword>.</para>
      <para>When comparing bookmarks, ADO does not attempt any type of coercion. The values are simply passed to the provider where the comparison occurs. If the bookmarks passed to the <unmanagedCodeEntityReference>CompareBookmarks</unmanagedCodeEntityReference> method are stored in variables of differing types, it can generate the following type mismatch error: "Arguments are of the wrong type, are out of the acceptable range, or are in conflict with each other."</para>
      <para>A bookmark that is not valid or incorrectly formed will cause an error.</para>
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
<link xlink:href="f156aa48-bfc2-40d1-962b-7b08855776c6">Visual Basic Example</link>
<link xlink:href="24ab3f3a-29c5-4ee1-942e-2634c02d0778">Visual C++ Example</link>
<link xlink:href="3c679a15-e924-49a5-8f3a-38a8266064f8">Visual J++ Example </link>
<link xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>