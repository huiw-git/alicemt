---
title: "Requery Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
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
# Requery Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Updates the data in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object by re-executing the query on which the object is based.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference>.<legacyBold>Requery </legacyBold><parameterReference>Options</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A bitmask that contains <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink> and <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> values affecting this operation.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>If <legacyItalic>Options</legacyItalic> is set to <legacyBold>adAsyncExecute</legacyBold>, this operation will execute asynchronously and a <legacyLink xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">RecordsetChangeComplete</legacyLink> event will be issued when it concludes. The <legacyBold>ExecuteOpenEnum</legacyBold> values of <legacyBold>adExecuteNoRecords</legacyBold> or <legacyBold>adExecuteStream</legacyBold> should not be used with <legacyBold>Requery</legacyBold>.</para>
      </alert>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Requery</legacyBold> method to refresh the entire contents of a <legacyBold>Recordset</legacyBold> object from the data source by reissuing the original command and retrieving the data a second time. Calling this method is equivalent to calling the <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> and <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> methods in succession. If you are editing the current record or adding a new record, an error occurs.</para>
      <para>While the <legacyBold>Recordset</legacyBold> object is open, the properties that define the nature of the cursor (<legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink>, <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink>, <legacyLink xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords</legacyLink>, and so forth) are read-only. Thus, the <legacyBold>Requery</legacyBold> method can only refresh the current cursor. To change any of the cursor properties and view the results, you must use the <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> method so that the properties become read/write again. You can then change the property settings and call the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method to reopen the cursor.</para>
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
<link xlink:href="ed5e1b60-3769-4b26-a253-1d721e37941d">Visual Basic Example</link>
<link xlink:href="3a7bbf07-2fca-4892-95f4-eec93f2d5e91">VBScript Example</link>
<link xlink:href="ada6acc1-82eb-4cfa-8f2f-617a916ffd8d">Visual C++ Example</link>
<link xlink:href="3c92cb19-c13b-4bb3-b4cd-75dc8f42057c">Visual J++ Example</link>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>