---
title: "CacheSize Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
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
# CacheSize Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the number of records from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object that are cached locally in memory.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Long</languageKeyword> value that must be greater than 0. Default is 1.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>CacheSize</legacyBold> property to control how many records to retrieve at one time into local memory from the provider. For example, if the <legacyBold>CacheSize</legacyBold> is 10, after first opening the <legacyBold>Recordset</legacyBold> object, the provider retrieves the first 10 records into local memory. As you move through the <legacyBold>Recordset</legacyBold> object, the provider returns the data from the local memory buffer. As soon as you move past the last record in the cache, the provider retrieves the next 10 records from the data source into the cache.</para>
      <alert class="note">
        <para> <legacyBold>CacheSize</legacyBold> is based on the <legacyBold>Maximum Open Rows</legacyBold> provider-specific property (in the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Recordset</legacyBold> object). You cannot set <legacyBold>CacheSize</legacyBold> to a value greater than <legacyBold>Maximum Open Rows</legacyBold>. To modify the number of rows which can be opened by the provider, set <legacyBold>Maximum Open Rows</legacyBold>.</para>
      </alert>
      <para>The value of <legacyBold>CacheSize</legacyBold> can be adjusted during the life of the <legacyBold>Recordset</legacyBold> object, but changing this value only affects the number of records in the cache after subsequent retrievals from the data source. Changing the property value alone will not change the current contents of the cache.</para>
      <para>If there are fewer records to retrieve than <legacyBold>CacheSize</legacyBold> specifies, the provider returns the remaining records and no error occurs.</para>
      <para>A <legacyBold>CacheSize</legacyBold> setting of zero is not allowed and returns an error.</para>
      <para>Records retrieved from the cache don't reflect concurrent changes that other users made to the source data. To force an update of all the cached data, use the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method.</para>
      <para>If <legacyBold>CacheSize</legacyBold> is set to a value greater than one, the navigation methods (<legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious</legacyLink>) may result in navigation to a deleted record, if deletion occurs after the records were retrieved. After the initial fetch, subsequent deletions will not be reflected in your data cache until you attempt to access a data value from a deleted row. However, setting <legacyBold>CacheSize</legacyBold> to one eliminates this issue since deleted rows cannot be fetched.</para>
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
<link xlink:href="a237ffdb-6e5b-47c6-9901-d5cdbe8625f3">Visual Basic Example</link>
<link xlink:href="e0e7b7ba-3943-43cb-a2cd-0e4667187973">Visual C++ Example</link>
<link xlink:href="d6fe482a-6951-438b-be58-e08f64efd1e2">Visual J++ Example</link>
<link xlink:href="3675f641-b4b1-48ff-ba33-8d9ea064cd04">Jscript Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>