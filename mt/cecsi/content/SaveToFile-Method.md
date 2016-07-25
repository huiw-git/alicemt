---
title: "SaveToFile Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
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
# SaveToFile Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Saves the binary contents of a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> to a file.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Stream</parameterReference><legacyBold>.SaveToFile</legacyBold> <parameterReference>FileName</parameterReference><legacyBold>,</legacyBold> <parameterReference>SaveOptions</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>FileName</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> value that contains the fully-qualified name of the file to which the contents of the <legacyBold>Stream</legacyBold> will be saved. You can save to any valid local location, or any location you have access to via a UNC value.</para>
        </definition>
        <definedTerm> <legacyItalic>SaveOptions</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="59339100-6e29-48d1-aea3-6873796d186b">SaveOptionsEnum</legacyLink> value that specifies whether a new file should be created by <legacyBold>SaveToFile</legacyBold>, if it does not already exist. Default value is <legacyBold>adSaveCreateNotExists</legacyBold>. With these options you can specify that an error occurs if the specified file does not exist. You can also specify that <legacyBold>SaveToFile</legacyBold> overwrites the current contents of an existing file.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>If you overwrite an existing file (when <legacyBold>adSaveCreateOverwrite</legacyBold> is set), <legacyBold>SaveToFile</legacyBold> truncates any bytes from the original existing file that follow the new <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink>.</para>
      </alert>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyBold>SaveToFile</legacyBold> may be used to copy the contents of a <legacyBold>Stream </legacyBold>object to a local file. There is no change in the contents or properties of the <legacyBold>Stream</legacyBold> object. The <legacyBold>Stream</legacyBold> object must be open before calling <legacyBold>SaveToFile</legacyBold>.</para>
      <para>This method does not change the association of the <legacyBold>Stream</legacyBold> object to its underlying source. The <legacyBold>Stream</legacyBold> object will still be associated with the original URL or <legacyBold>Record</legacyBold> that was its source when opened.</para>
      <para>After a <legacyBold>SaveToFile</legacyBold> operation, the current position (<legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink>) in the stream is set to the beginning of the stream (0).</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
<link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>