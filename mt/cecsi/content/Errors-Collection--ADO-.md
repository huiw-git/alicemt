---
title: "Errors Collection (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 290819e1-7b39-4e1e-a93b-801257138b00
caps.latest.revision: 9
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
# Errors Collection (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains all the <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> objects created in response to a single provider-related failure.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Any operation involving ADO objects can generate one or more provider errors. As each error occurs, one or more <legacyBold>Error</legacyBold> objects can be placed in the <legacyBold>Errors</legacyBold> collection of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. When another ADO operation generates an error, the <legacyBold>Errors</legacyBold> collection is cleared, and the new set of <legacyBold>Error</legacyBold> objects can be placed in the <legacyBold>Errors</legacyBold> collection.</para>
      <para>Each <legacyBold>Error</legacyBold> object represents a specific provider error, not an ADO error. ADO errors are exposed to the run-time exception-handling mechanism. For example, in Microsoft Visual Basic, the occurrence of an ADO-specific error will trigger an <legacyLink xlink:href="b01cbc62-fbd7-4068-b16c-8b0f80a05887">onError</legacyLink> event and appear in the <legacyBold>Err</legacyBold> object.</para>
      <para>ADO operations that don't generate an error have no effect on the <legacyBold>Errors</legacyBold> collection. Use the <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink> method to manually clear the <legacyBold>Errors</legacyBold> collection.</para>
      <para>The set of <legacyBold>Error</legacyBold> objects in the <legacyBold>Errors</legacyBold> collection describes all errors that occurred in response to a single statement. Enumerating the specific errors in the <legacyBold>Errors</legacyBold> collection enables your error-handling routines to more precisely determine the cause and origin of an error, and take appropriate steps to recover.</para>
      <para>Some properties and methods return warnings that appear as <legacyBold>Error</legacyBold> objects in the <legacyBold>Errors</legacyBold> collection but do not halt a program's execution. Before you call the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>, <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>, or <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> methods on a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method on a <legacyBold>Connection</legacyBold> object, or set the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property on a <legacyBold>Recordset</legacyBold> object, call the <legacyBold>Clear</legacyBold> method on the <legacyBold>Errors</legacyBold> collection. That way you can read the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property of the <legacyBold>Errors</legacyBold> collection to test for returned warnings.</para>
      <alert class="note">
        <para>See the <legacyBold>Error</legacyBold> object topic for a more detailed explanation of the way a single ADO operation can generate multiple errors.</para>
      </alert>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="606f2b92-3821-4d11-a207-4c22f6f35619">Errors Collection Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error Object</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>