---
title: "DefaultDatabase Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
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
# DefaultDatabase Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the default database for a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value that evaluates to the name of a database available from the provider.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>DefaultDatabase</legacyBold> property to set or return the name of the default database on a specific <legacyBold>Connection</legacyBold> object.</para>
      <para>If there is a default database, SQL strings may use an unqualified syntax to access objects in that database. To access objects in a database other than the one specified in the <legacyBold>DefaultDatabase</legacyBold> property, you must qualify object names with the desired database name. Upon connection, the provider will write default database information to the <legacyBold>DefaultDatabase</legacyBold> property. Some providers allow only one database per connection, in which case you cannot change the <legacyBold>DefaultDatabase</legacyBold> property.</para>
      <para>Some data sources and providers may not support this feature, and may return an error or an empty string.</para>
      <alert class="note">
        <para> <legacyBold>Remote Data Service Usage</legacyBold>   This property is not available on a client-side <legacyBold>Connection</legacyBold> object.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="677e1dbe-bcf6-4028-a62c-e99b1c88bf7b">Visual Basic Example</link>
<link xlink:href="d9868c99-425a-4b10-af67-1929ed513fda">Visual C++ Example</link>
<link xlink:href="fdc26576-37d0-4fa1-9afa-75d0e7133675">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>