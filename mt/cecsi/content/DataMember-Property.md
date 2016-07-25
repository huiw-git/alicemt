---
title: "DataMember Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
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
# DataMember Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the name of the data member that will be retrieved from the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> referenced by the <legacyLink xlink:href="300a702a-3544-48c5-b759-83b511fe97e0">DataSource</legacyLink> property.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value. The name is not case sensitive.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>This property is used to create data-bound controls with the Data Environment. The Data Environment maintains collections of data (data sources) containing named objects (data members) that will be represented as a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
      <para>The <unmanagedCodeEntityReference>DataMember</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>DataSource</unmanagedCodeEntityReference> properties must be used together.</para>
      <para>The <unmanagedCodeEntityReference>DataMember</unmanagedCodeEntityReference> property determines which object specified by the <unmanagedCodeEntityReference>DataSource</unmanagedCodeEntityReference> property will be represented as a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object. The <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object must be closed before this property is set. An error is generated if the <unmanagedCodeEntityReference>DataMember</unmanagedCodeEntityReference> property is not set before the <unmanagedCodeEntityReference>DataSource</unmanagedCodeEntityReference> property, or if the <unmanagedCodeEntityReference>DataMember</unmanagedCodeEntityReference> name is not recognized by the object specified in the <unmanagedCodeEntityReference>DataSource</unmanagedCodeEntityReference> property.</para>
    </content>
    <sections>
      <section>
        <title>Usage</title>
        <content>
          <code>Dim rs as New ADODB.Recordset
rs.DataMember = "Command"     'Name of the rowset to bind to
Set rs.DataSource = myDE      'Name of the object containing an IRowset</code>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="300a702a-3544-48c5-b759-83b511fe97e0">DataSource Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>