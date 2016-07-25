---
title: "Close Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3cdf27d1-a180-4cff-8e42-95dec5fb1b55
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
# Close Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Closes an open object and any dependent objects.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>object</parameterReference>.<legacyBold>Close</legacyBold></legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Close</legacyBold> method to close a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>, a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, or a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object to free any associated system resources. Closing an object does not remove it from memory; you can change its property settings and open it again later. To completely eliminate an object from memory, close the object and then set the object variable to <legacyItalic>Nothing</legacyItalic> (in Visual Basic).</para>
    </content>
    <sections>
      <section>
        <title>Connection</title>
        <content>
          <para>Using the <legacyBold>Close</legacyBold> method to close a <legacyBold>Connection</legacyBold> object also closes any active <legacyBold>Recordset</legacyBold> objects associated with the connection. A <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object associated with the <legacyBold>Connection</legacyBold> object you are closing will persist, but it will no longer be associated with a <legacyBold>Connection</legacyBold> object; that is, its <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property will be set to <legacyBold>Nothing</legacyBold>. Also, the <legacyBold>Command</legacyBold> object's <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection will be cleared of any provider-defined parameters.</para>
          <para>You can later call the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method to re-establish the connection to the same, or another, data source. While the <legacyBold>Connection</legacyBold> object is closed, calling any methods that require an open connection to the data source generates an error.</para>
          <para>Closing a <legacyBold>Connection</legacyBold> object while there are open <legacyBold>Recordset</legacyBold> objects on the connection rolls back any pending changes in all of the <legacyBold>Recordset</legacyBold> objects. Explicitly closing a <legacyBold>Connection</legacyBold> object (calling the <legacyBold>Close</legacyBold> method) while a transaction is in progress generates an error. If a <legacyBold>Connection</legacyBold> object falls out of scope while a transaction is in progress, ADO automatically rolls back the transaction.</para>
        </content>
      </section>
      <section>
        <title>Recordset, Record, Stream</title>
        <content>
          <para>Using the <legacyBold>Close</legacyBold> method to close a <legacyBold>Recordset</legacyBold>, <legacyBold>Record</legacyBold>, or <legacyBold>Stream</legacyBold> object releases the associated data and any exclusive access you may have had to the data through this particular object. You can later call the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method to reopen the object with the same, or modified, attributes.</para>
          <para>While a <legacyBold>Recordset</legacyBold> object is closed, calling any methods that require a live cursor generates an error.</para>
          <para>If an edit is in progress while in immediate update mode, calling the <legacyBold>Close</legacyBold> method generates an error; instead, call the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> or <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method first. If you close the <legacyBold>Recordset</legacyBold> object while in batch update mode, all changes since the last <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> call are lost.</para>
          <para>If you use the <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink> method to create copies of an open <legacyBold>Recordset</legacyBold> object, closing the original or a clone does not affect any of the other copies.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="1311d561-0e86-40f5-8cbc-ad8f13e626d1">Visual Basic Example</link>
<link xlink:href="66eca011-e258-4d8f-bd67-e017bcf0871b">VBScript Example</link>
<link xlink:href="f74a81fd-cbcc-4143-b9f8-774c88dd4fad">Visual C++ Example</link>
<link xlink:href="0b7dd9f8-4751-48fb-a75d-c6f75d80d928">Visual J++ Example</link>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>