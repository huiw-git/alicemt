---
title: "GetRows Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
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
# GetRows Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Retrieves multiple records of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object into an array.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>array</parameterReference> = <parameterReference>recordset</parameterReference><legacyBold>.GetRows(</legacyBold><parameterReference>Rows</parameterReference><legacyBold>, </legacyBold><parameterReference>Start</parameterReference><legacyBold>, </legacyBold><parameterReference>Fields </parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <languageKeyword>Variant</languageKeyword> whose value is a two-dimensional array.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Rows</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="adc109b9-79f4-4946-a5eb-658e22e9a8a5">GetRowsOptionEnum</legacyLink> value that indicates the number of records to retrieve. The default is <legacyBold>adGetRowsRest</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>Start</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value or <languageKeyword>Variant</languageKeyword> that evaluates to the bookmark for the record from which the <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference> operation should begin. You can also use a <legacyLink xlink:href="55d273c4-ccee-48ef-ba90-8893d04313c8">BookmarkEnum</legacyLink> value.</para>
        </definition>
        <definedTerm> <legacyItalic>Fields</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> that represents a single field name or ordinal position, or an array of field names or ordinal position numbers. ADO returns only the data in these fields.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference> method to copy records from a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> into a two-dimensional array. The first subscript identifies the field and the second identifies the record number. The <legacyItalic>array</legacyItalic> variable is automatically dimensioned to the correct size when the <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference> method returns the data.</para>
      <para>If you do not specify a value for the <legacyItalic>Rows</legacyItalic> argument, the <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference> method automatically retrieves all the records in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object. If you request more records than are available, <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference> returns only the number of available records.</para>
      <para>If the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports bookmarks, you can specify at which record the <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference> method should begin retrieving data by passing the value of that record's <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink> property in the <legacyItalic>Start</legacyItalic> argument.</para>
      <para>If you want to restrict the fields that the <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference> call returns, you can pass either a single field name/number or an array of field names/numbers in the <legacyItalic>Fields</legacyItalic> argument.</para>
      <para>After you call <unmanagedCodeEntityReference>GetRows</unmanagedCodeEntityReference>, the next unread record becomes the current record, or the <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> property is set to <languageKeyword>True</languageKeyword> if there are no more records.</para>
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
<link xlink:href="9f7c78bb-7bb8-4c4f-8e5a-4d3bfc8a208f">Visual Basic Example</link>
<link xlink:href="08e5c5bf-f7de-4bf9-97a9-f214c128ad8c">Visual C++ Example</link>
<link xlink:href="44dde820-9596-439c-97a8-037d40d873f0">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>