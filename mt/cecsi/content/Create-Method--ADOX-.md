---
title: "Create Method (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
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
# Create Method (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates a new catalog.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Catalog</parameterReference><legacyBold>.Create </legacyBold><parameterReference>ConnectString</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>ConnectString </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value used to connect to the data source.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>Create</legacyBold> method creates and opens a new ADO <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> to the data source specified in <legacyItalic>ConnectString</legacyItalic>. If successful, the new <legacyBold>Connection</legacyBold> object is assigned to the <legacyLink xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection</legacyLink> property.</para>
      <para>An error will occur if the provider does not support creating new catalogs.</para>
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
<link xlink:href="d7ea0244-596a-404e-8f30-71cadab8d8fc">Create Method Example (VB)</link>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>