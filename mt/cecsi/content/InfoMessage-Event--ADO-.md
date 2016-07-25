---
title: "InfoMessage Event (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 468c87dd-e3bc-4084-9941-94d10743d4e9
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
# InfoMessage Event (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>InfoMessage</legacyBold> event is called whenever a warning occurs during a <legacyBold>ConnectionEvent</legacyBold> operation.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>InfoMessage</legacyBold> <parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pConnection</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. This parameter contains any errors that are returned. If multiple errors are returned, enumerate the <legacyBold>Errors</legacyBold> collection to find them.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value. If a warning occurs, <legacyItalic>adStatus</legacyItalic> is set to <legacyBold>adStatusOK</legacyBold> and the <legacyItalic>pError</legacyItalic> contains the warning.</para>
          <para>Before this event returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
        </definition>
        <definedTerm> <legacyItalic>pConnection</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. The connection for which the warning occurred. For example, warnings can occur when opening a <legacyBold>Connection</legacyBold> object or executing a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> on a <legacyBold>Connection</legacyBold>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>