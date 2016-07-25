---
title: "LoadFromFile Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
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
# LoadFromFile Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Loads the contents of an existing file into a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Stream</parameterReference><legacyBold>.LoadFromFile</legacyBold><parameterReference>FileName</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>FileName</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains the name of a file to be loaded into the <legacyBold>Stream</legacyBold>. <legacyItalic>FileName</legacyItalic> can contain any valid path and name in UNC format. If the specified file does not exist, a run-time error occurs.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>This method can be used to load the contents of a local file into a <legacyBold>Stream</legacyBold> object. This can be used to upload the contents of a local file to a server.</para>
      <para>The <legacyBold>Stream</legacyBold> object must be already open before calling <legacyBold>LoadFromFile</legacyBold>. This method does not change the binding of the <legacyBold>Stream</legacyBold> object; it will still be bound to the object specified by the URL or <legacyBold>Record</legacyBold> with which the <legacyBold>Stream</legacyBold> was originally opened.</para>
      <para>
        <legacyBold>LoadFromFile</legacyBold> overwrites the current contents of the <legacyBold>Stream</legacyBold> object with data read from the file. Any existing bytes in the <legacyBold>Stream</legacyBold> are overwritten by the contents of the file. Any previously existing and remaining bytes following the <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink> created by <legacyBold>LoadFromFile</legacyBold>, are truncated.</para>
      <para>After a call to <legacyBold>LoadFromFile</legacyBold>, the current position is set to the beginning of the <legacyBold>Stream</legacyBold> (<legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> is 0).</para>
      <para>Because 2 bytes may be added to the beginning of the stream for encoding, the size of the stream may not exactly match the size of the file from which it was loaded.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>