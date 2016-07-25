---
title: "AbsolutePosition Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
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
# AbsolutePosition Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the ordinal position of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's current record.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>For 32-bit code, sets or returns a <legacyBold>Long</legacyBold> value from 1 to the number of records in the <legacyBold>Recordset</legacyBold> object (<legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink>), or returns one of the <legacyLink xlink:href="e69af0a5-3405-4b72-9c6e-6b188ff746fd">PositionEnum</legacyLink> values.</para>
      <para>For 64-bit code, use a data type that provides for storage of a 64-bit value. For example, you might use either Long or another value that is 64-bit length such as DBORDINAL. Do not use <legacyBold>PositionEnum</legacyBold> values since they are limited to 32-bit length.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>In order to set the <legacyBold>AbsolutePosition</legacyBold> property, ADO requires that the OLE DB provider you are using implement the <externalLink><linkText>IRowsetLocate:IRowset</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx</linkUri></externalLink> interface.</para>
      <para>Accessing the <legacyBold>AbsolutePosition</legacyBold> property of a <legacyBold>Recordset</legacyBold> that was opened with either a forward-only or dynamic cursor raises the error <legacyBold>adErrFeatureNotAvailable</legacyBold>. With other cursor types, the correct position will be returned as long as the OLE DB provider supports the <unmanagedCodeEntityReference>IRowsetScroll:IRowsetLocate</unmanagedCodeEntityReference> interface. If the provider does not support the <unmanagedCodeEntityReference>IRowsetScroll</unmanagedCodeEntityReference> interface, the property is set to <legacyBold>adPosUnknown</legacyBold>. See the documentation for your provider to determine whether it supports <unmanagedCodeEntityReference>IRowsetScroll</unmanagedCodeEntityReference>.</para>
      <para>Use the <unmanagedCodeEntityReference>AbsolutePosition</unmanagedCodeEntityReference> property to move to a record based on its ordinal position in the <legacyBold>Recordset</legacyBold> object, or to determine the ordinal position of the current record. The provider must support the appropriate functionality for this property to be available.</para>
      <para>Like the <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink> property, <legacyBold>AbsolutePosition</legacyBold> is 1-based and equals 1 when the current record is the first record in the <legacyBold>Recordset</legacyBold>. You can obtain the total number of records in the <legacyBold>Recordset</legacyBold> object from the <legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink> property.</para>
      <para>When you set the <legacyBold>AbsolutePosition</legacyBold> property, even if it is to a record in the current cache, ADO reloads the cache with a new group of records starting with the record you specified. The <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property determines the size of this group.</para>
      <alert class="note">
        <para>You should not use the <legacyBold>AbsolutePosition</legacyBold> property as a surrogate record number. The position of a given record changes when you delete a preceding record. There is also no assurance that a given record will have the same <legacyBold>AbsolutePosition</legacyBold> if the <legacyBold>Recordset</legacyBold> object is requeried or reopened. Bookmarks are still the recommended way of retaining and returning to a given position and are the only way of positioning across all types of <legacyBold>Recordset</legacyBold> objects.</para>
      </alert>
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
<link xlink:href="c4755799-c60a-4b5e-a01f-b85dd0e0a7f9">Visual Basic Example</link>
<link xlink:href="48c07216-d199-4822-89f8-ce928d3d2b74">Visual C++ Example</link>
<link xlink:href="74afb37a-92b5-4cab-be49-18fb866e4d53">Visual J++ Example</link>
<link xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage Property</link>
<link xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>