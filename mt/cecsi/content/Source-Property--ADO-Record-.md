---
title: "Source Property (ADO Record)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
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
# Source Property (ADO Record)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the data source or object represented by the <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Variant</languageKeyword> value that indicates the entity represented by the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The <unmanagedCodeEntityReference>Source</unmanagedCodeEntityReference> property returns the <parameterReference>Source</parameterReference> argument of the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open</legacyLink> method. It can contain an absolute or relative URL string. An absolute URL can be used without setting the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property to directly open the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object. An implicit <legacyBold>Connection</legacyBold> object is created in this case.</para>
      <para>The <unmanagedCodeEntityReference>Source</unmanagedCodeEntityReference> property can also contain a reference to an already open <legacyBold>Recordset</legacyBold>, which opens a <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object representing the current row in the <legacyBold>Recordset</legacyBold>.</para>
      <para>The <unmanagedCodeEntityReference>Source</unmanagedCodeEntityReference> property could also contain a reference to a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object which returns a single row of data from the provider.</para>
      <para>If the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property is also set, then the <unmanagedCodeEntityReference>Source</unmanagedCodeEntityReference> property must point to some object that exists within the scope of that connection. For example, in tree-structured namespaces, if the <unmanagedCodeEntityReference>Source</unmanagedCodeEntityReference> property contains an absolute URL, it must point to a node that exists inside the scope of the node identified by the URL in the connection string. If the <unmanagedCodeEntityReference>Source</unmanagedCodeEntityReference> property contains a relative URL, then it is validated within the context set by the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property.</para>
      <para>The <unmanagedCodeEntityReference>Source</unmanagedCodeEntityReference> property is read/write while the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object is closed, and is read-only while the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object is open.</para>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source Property (ADO Error)</link>
<link xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source Property (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>