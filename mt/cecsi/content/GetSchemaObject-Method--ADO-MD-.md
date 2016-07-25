---
title: "GetSchemaObject Method (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
caps.latest.revision: 12
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
# GetSchemaObject Method (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Retrieves an ADO MD schema object (<legacyLink xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">Dimension</legacyLink>, <legacyLink xlink:href="034af340-ac79-494e-ba5e-2b57da1cb9de">Hierarchy</legacyLink>, <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink>, or <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink>) by its <legacyLink xlink:href="5b977956-e252-4861-8425-f1aaf6b80130">UniqueName</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set</legacyBold> <parameterReference>object</parameterReference> = <parameterReference>CubeDef</parameterReference>.<legacyBold>GetSchemaObject (</legacyBold><parameterReference>ObjType</parameterReference>, <parameterReference>UniqueName</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>ObjType </parameterReference>
        </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="bf53939f-5543-40ac-a707-aa35e9bde1dd">SchemaObjectTypeEnum</legacyLink> value specifying what type of schema object (Dimension, Hierarchy, Level, or Member) to retrieve.</para>
        </definition>
        <definedTerm>
          <parameterReference>UniqueName </parameterReference>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> specifying the <unmanagedCodeEntityReference>UniqueName</unmanagedCodeEntityReference> property value of the object to retrieve.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>
        <unmanagedCodeEntityReference>GetSchemaObject</unmanagedCodeEntityReference> retrieves objects using their unique names, as specified by the <unmanagedCodeEntityReference>UniqueName</unmanagedCodeEntityReference> property. The names of parent objects do not need to be known, and parent collections do not need to be populated to retrieve a schema object.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef Object (ADO MD)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef Object</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>