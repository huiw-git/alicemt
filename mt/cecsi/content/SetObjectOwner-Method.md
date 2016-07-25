---
title: "SetObjectOwner Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
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
# SetObjectOwner Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the owner of an object in a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Catalog</parameterReference><legacyBold>.SetObjectOwner </legacyBold><parameterReference>ObjectName</parameterReference><legacyBold>,</legacyBold><parameterReference> ObjectType</parameterReference><legacyBold>,</legacyBold><parameterReference> OwnerName </parameterReference>[<legacyBold>,</legacyBold><parameterReference>ObjectTypeId</parameterReference>]</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>ObjectName </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that specifies the name of the object for which to specify the owner.</para>
        </definition>
        <definedTerm> <parameterReference>ObjectType </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value which can be one of the <legacyLink xlink:href="3fdecfca-aa91-4596-ad98-610f1b7f840b">ObjectTypeEnum</legacyLink> constants that specifies the owner type.</para>
        </definition>
        <definedTerm> <parameterReference>OwnerName </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that specifies the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> of the <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink> or <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink> to own the object.</para>
        </definition>
        <definedTerm> <parameterReference>ObjectTypeId </parameterReference></definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> value that specifies the GUID for a provider object type that is not defined by the OLE DB specification. This parameter is required if <parameterReference>ObjectType</parameterReference> is set to <legacyBold>adPermObjProviderSpecific</legacyBold>; otherwise, it is not used.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>An error will occur if the provider does not support specifying object owners.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e44ec3d4-42ae-447d-aaed-bdea53cb0cca">GetObjectOwner and SetObjectOwner Methods Example (VB)</link>
<link xlink:href="8965adf0-9075-4125-8142-73eb700029c3">GetObjectOwner Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>