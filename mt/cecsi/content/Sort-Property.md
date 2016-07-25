---
title: "Sort Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3683ffa0-6f93-4906-9533-ef6942f24f39
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
# Sort Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates one or more field names on which the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> is sorted, and whether each field is sorted in ascending or descending order.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value that indicates the field names in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> on which to sort. Each name is separated by a comma, and is optionally followed by a blank and the keyword, <languageKeyword>ASC</languageKeyword>, which sorts the field in ascending order, or <languageKeyword>DESC</languageKeyword>, which sorts the field in descending order. By default, if no keyword is specified, the field is sorted in ascending order.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>This property requires the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to be set to <legacyBold>adUseClient</legacyBold>. A temporary index will be created for each field specified in the <unmanagedCodeEntityReference>Sort</unmanagedCodeEntityReference> property if an index does not already exist.</para>
      <para>The sort operation is efficient because data is not physically rearranged, but is simply accessed in the order specified by the index.</para>
      <para>When the value of the <unmanagedCodeEntityReference>Sort</unmanagedCodeEntityReference> property is anything other than an empty string, the <unmanagedCodeEntityReference>Sort</unmanagedCodeEntityReference> property order takes precedence over the order specified in an <languageKeyword>ORDER BY</languageKeyword> clause included in the SQL statement used to open the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
      <para>The <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> does not have to be opened before accessing the <unmanagedCodeEntityReference>Sort</unmanagedCodeEntityReference> property; it can be set at any time after the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object is instantiated.</para>
      <para>Setting the <unmanagedCodeEntityReference>Sort</unmanagedCodeEntityReference> property to an empty string will reset the rows to their original order and delete temporary indexes. Existing indexes will not be deleted.</para>
      <para>Suppose a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> contains three fields named <legacyItalic>firstName</legacyItalic>, <legacyItalic>middleInitial</legacyItalic>, and <legacyItalic>lastName</legacyItalic>. Set the <unmanagedCodeEntityReference>Sort</unmanagedCodeEntityReference> property to the string, "<codeInline>lastName DESC, firstName ASC</codeInline>", which will order the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> by last name in descending order, then by first name in ascending order. The middle initial is ignored.</para>
      <para>No field can be named "ASC" or "DESC" because those names conflict with the keywords <languageKeyword>ASC</languageKeyword> and <languageKeyword>DESC</languageKeyword>. You can create an alias for a field with a conflicting name by using the <languageKeyword>AS</languageKeyword> keyword in the query that returns the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
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
<link xlink:href="fc2fd40b-65d6-4023-90a3-90c9a88ef6cf">Visual Basic Example</link>
<link xlink:href="58199284-747b-4312-b97f-797ee7bd4435">Visual C++ Example</link>
<link xlink:href="460d4bbc-6250-475e-843e-899cf3c11742">Visual J++ Example</link>
<link xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize Property — Dynamic (ADO)</link>
<link xlink:href="f6f80f67-f0fb-4e63-a5f5-8fdf312aac63">SortColumn Property (RDS)</link>
<link xlink:href="1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2">SortDirection Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>