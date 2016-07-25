---
title: "Error Object"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a175d453-fa55-4f49-9ede-a26d83177919
caps.latest.revision: 8
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
# Error Object
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains details about data access errors that pertain to a single operation involving the provider.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Any operation involving ADO objects can generate one or more provider errors. As each error occurs, one or more <legacyBold>Error</legacyBold> objects are placed in the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. When another ADO operation generates an error, the <legacyBold>Errors</legacyBold> collection is cleared, and the new set of <legacyBold>Error</legacyBold> objects is placed in the <legacyBold>Errors</legacyBold> collection.</para>
      <alert class="note">
        <para>Each <legacyBold>Error</legacyBold> object represents a specific provider error, not an ADO error. ADO errors are exposed to the run-time exception-handling mechanism. For example, in Microsoft Visual Basic, the occurrence of an ADO-specific error will trigger an <legacyBold>On Error</legacyBold> event and appear in the <legacyBold>Error</legacyBold> object. For a complete list of ADO errors, see the <legacyLink xlink:href="9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea">ErrorValueEnum</legacyLink> topic.</para>
      </alert>
      <para>You can read an <legacyBold>Error</legacyBold> object's properties to obtain specific details about each error, including the following:

</para>
      <list class="bullet">
        <listItem>
          <para>The <legacyLink xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description</legacyLink> property, which contains the text of the error. This is the default property.</para>
        </listItem>
        <listItem>
          <para>The <legacyLink xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number</legacyLink> property, which contains the <legacyBold>Long</legacyBold> integer value of the error constant.</para>
        </listItem>
        <listItem>
          <para>The <legacyLink xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source</legacyLink> property, which identifies the object that raised the error. This is particularly useful when you have several <legacyBold>Error</legacyBold> objects in the <legacyBold>Errors</legacyBold> collection following a request to a data source.</para>
        </listItem>
        <listItem>
          <para>The <legacyLink xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState</legacyLink> and <legacyLink xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError</legacyLink> properties, which provide information from SQL data sources.</para>
        </listItem>
      </list>
      <para>When a provider error occurs, it is placed in the <legacyBold>Errors</legacyBold> collection of the <legacyBold>Connection</legacyBold> object. ADO supports the return of multiple errors by a single ADO operation to allow for error information specific to the provider. To obtain this rich error information in an error handler, use the appropriate error-trapping features of the language or environment you are working with, then use nested loops to enumerate the properties of each <legacyBold>Error</legacyBold> object in the <legacyBold>Errors</legacyBold> collection.</para>
      <alert class="note">
        <para>
          <legacyBold>Microsoft Visual Basic and VBScript Users</legacyBold>   If there is no valid <legacyBold>Connection</legacyBold> object, you will need to retrieve error information from the <legacyBold>Error</legacyBold> object.</para>
      </alert>
      <para>Just as providers do, ADO clears the <legacyBold>OLE Error Info</legacyBold> object before making a call that could potentially generate a new provider error. However, the <legacyBold>Errors</legacyBold> collection on the <legacyBold>Connection</legacyBold> object is cleared and populated only when the provider generates a new error, or when the <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink> method is called.</para>
      <para>Some properties and methods return warnings that appear as <legacyBold>Error</legacyBold> objects in the <legacyBold>Errors</legacyBold> collection but do not halt a program's execution. Before you call the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>, <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>, or <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> methods on a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object; the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method on a <legacyBold>Connection</legacyBold> object; or set the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property on a <legacyBold>Recordset</legacyBold> object, call the <legacyBold>Clear</legacyBold> method on the <legacyBold>Errors</legacyBold> collection. That way, you can read the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property of the <legacyBold>Errors</legacyBold> collection to test for returned warnings.</para>
      <para>The <legacyBold>Error</legacyBold> object is not safe for scripting.</para>
      <para>This section contains the following topic.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="cd69e4b7-82bf-4ffc-bc53-c535ba20161f">Error Object Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="5c728458-d85c-497c-afcf-2cfa36c3342a">Visual Basic Example</link>
<link xlink:href="5321fc0f-cd0c-4e2a-a5bc-0008fba86b59">Visual C++ Example</link>
<link xlink:href="7fd0eebc-99f4-490e-9b62-0b62b1884d6b">Visual J++ Example</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>