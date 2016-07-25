---
title: "Provider Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
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
# Provider Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the name of the provider for a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value that indicates the provider name.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Provider</unmanagedCodeEntityReference> property to set or return the name of the provider for a connection. This property can also be set by the contents of the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property or the <legacyItalic>ConnectionString</legacyItalic> argument of the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method; however, specifying a provider in more than one place while calling the <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> method can have unpredictable results. If no provider is specified, the property will default to MSDASQL (<legacyLink xlink:href="2dc0372d-e74d-4d0f-9c8c-04e5a168c148">Microsoft OLE DB Provider for ODBC</legacyLink>).</para>
      <para>The <unmanagedCodeEntityReference>Provider</unmanagedCodeEntityReference> property is read/write when the connection is closed and read-only when it is open. The setting does not take effect until you either open the <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object or access the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection of the <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object. If the setting is not valid, an error occurs.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="677e1dbe-bcf6-4028-a62c-e99b1c88bf7b">Visual Basic Example</link>
<link xlink:href="677e1dbe-bcf6-4028-a62c-e99b1c88bf7b">Visual C++ Example</link>
<link xlink:href="fdc26576-37d0-4fa1-9afa-75d0e7133675">Visual J++ Example</link>
<link xlink:href="2dc0372d-e74d-4d0f-9c8c-04e5a168c148">Microsoft OLE DB Provider for ODBC</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>