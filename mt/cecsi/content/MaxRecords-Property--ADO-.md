---
title: "MaxRecords Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
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
# MaxRecords Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the maximum number of records to return to a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> from a query.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Long</languageKeyword> value that indicates the maximum number of records to return. Default is zero (<legacyBold>0</legacyBold>), which means no limit.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>MaxRecords</unmanagedCodeEntityReference> property to limit the number of records that the provider returns from the data source. The default setting of this property is zero, which means the provider returns all requested records.</para>
      <para>The <unmanagedCodeEntityReference>MaxRecords</unmanagedCodeEntityReference> property is read/write when the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is closed and read-only when it is open.</para>
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
<link xlink:href="630a3be4-7a87-41cf-997e-8bb50d89db1e">Visual Basic Example</link>
<link xlink:href="af6b399b-e546-4de5-9cd1-5a6e0ec7ddc7">Visual C++ Example</link>
<link xlink:href="f5f12f3b-8f45-4bfa-b70e-971b758e1898">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>