---
title: "Supports Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
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
# Supports Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Determines whether a specified <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object supports a particular type of functionality.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>boolean</parameterReference> = <parameterReference>recordset</parameterReference><legacyBold>.Supports(</legacyBold><parameterReference>CursorOptions </parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <languageKeyword>Boolean</languageKeyword> value that indicates whether all of the features identified by the <legacyItalic>CursorOptions</legacyItalic> argument are supported by the provider.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>CursorOptions </parameterReference>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> expression that consists of one or more <legacyLink xlink:href="4e10cda7-ce81-4466-94c2-844d38191cf1">CursorOptionEnum</legacyLink> values.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Supports</unmanagedCodeEntityReference> method to determine what types of functionality a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports. If the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports the features whose corresponding constants are in <parameterReference>CursorOptions</parameterReference>, the <unmanagedCodeEntityReference>Supports</unmanagedCodeEntityReference> method returns <languageKeyword>True</languageKeyword>. Otherwise, it returns <languageKeyword>False</languageKeyword>.</para>
      <alert class="note">
        <para>Although the <unmanagedCodeEntityReference>Supports</unmanagedCodeEntityReference> method may return <languageKeyword>True</languageKeyword> for a given functionality, it does not guarantee that the provider can make the feature available under all circumstances. The <unmanagedCodeEntityReference>Supports</unmanagedCodeEntityReference> method simply returns whether the provider can support the specified functionality, assuming certain conditions are met. For example, the <unmanagedCodeEntityReference>Supports</unmanagedCodeEntityReference> method may indicate that a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports updates even though the cursor is based on a multiple table join, some columns of which are not updatable.</para>
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
<link xlink:href="135aab26-ff5c-4fd9-910f-65cdead0b47e">Visual Basic Example</link>
<link xlink:href="6e174179-9d95-41b9-b72b-6cdbdca6e255">Visual C++ Example</link>
<link xlink:href="eb7a5d97-0f3c-4bd4-b66d-cd1c454c4a93">Visual J++ Example</link>
<link xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>