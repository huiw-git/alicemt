---
title: "GetObjectOwner Method (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
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
# GetObjectOwner Method (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns the owner of an object in a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Owner </parameterReference><legacyBold>= </legacyBold><parameterReference>Catalog</parameterReference><legacyBold>.GetObjectOwner(</legacyBold><parameterReference>ObjectName</parameterReference><legacyBold>,</legacyBold> <parameterReference>ObjectType </parameterReference>[<legacyBold>,</legacyBold><parameterReference>ObjectTypeId</parameterReference>]<legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyBold>String</legacyBold> value that specifies the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> of the <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink> or <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink> that owns the object.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ObjectName</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> value that specifies the name of the object for which to return the owner.</para>
        </definition>
        <definedTerm> <legacyItalic>ObjectType</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Long</legacyBold> value which can be one of the <legacyLink xlink:href="3fdecfca-aa91-4596-ad98-610f1b7f840b">ObjectTypeEnum</legacyLink> constants, that specifies the type of the object for which to get the owner.</para>
        </definition>
        <definedTerm> <legacyItalic>ObjectTypeId</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Variant</legacyBold> value that specifies the GUID for a provider object type not defined by the OLE DB specification. This parameter is required if <legacyItalic>ObjectType</legacyItalic> is set to <legacyBold>adPermObjProviderSpecific</legacyBold>; otherwise, it is not used.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>An error will occur if the provider does not support returning object owners.</para>
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
<link xlink:href="e5170a37-9d6e-43db-bfb6-9b6631fa3048">SetObjectOwner Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>