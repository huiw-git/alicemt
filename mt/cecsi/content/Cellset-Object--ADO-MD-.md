---
title: "Cellset Object (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
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
# Cellset Object (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents the results of a multidimensional query. It is a collection of cells selected from cubes or other cellsets.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Data within a <legacyBold>Cellset</legacyBold> is retrieved using direct, array-like access. You can drill down to a specific member to obtain data about that member. For example, the following code returns the caption of the first member in the first position on the first axis of a cellset named <codeInline>cst</codeInline>:</para>
      <code>cst.Axes(0).Positions(0).Members(0).Caption</code>
    </content>
  </languageReferenceRemarks>
  <languageReferenceRemarks>
    <content>
      <para>There is no notion of a current cell within a cellset. Instead, the <legacyLink xlink:href="0e93d79b-b12e-4e98-889e-c2dfcca20fd0">Item</legacyLink> property retrieves a specific <legacyLink xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell</legacyLink> object from the cellset. The arguments of the <legacyBold>Item</legacyBold> property determine which cell is retrieved. You can specify the unique ordinal value of a cell. You can also retrieve cells by using their position numbers along each axis of the cellset. For more information about retrieving cells, see the <legacyLink xlink:href="0e93d79b-b12e-4e98-889e-c2dfcca20fd0">Item</legacyLink> property.</para>
      <para>With the collections, methods, and properties of a <legacyBold>Cellset</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Associate an open connection with a <legacyBold>Cellset</legacyBold> object by setting its <legacyLink xlink:href="2509b32c-a995-4364-9152-d8c83129bdd8">ActiveConnection</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Execute and retrieve the results of a multidimensional query with the <legacyLink xlink:href="a87d8080-a238-45e5-bc80-9a8625b3810f">Open</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Retrieve a <legacyBold>Cell</legacyBold> from the <legacyBold>Cellset</legacyBold> with the <legacyLink xlink:href="0e93d79b-b12e-4e98-889e-c2dfcca20fd0">Item</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink> objects that define the <legacyBold>Cellset</legacyBold> with the <legacyLink xlink:href="072fb21a-ec0f-4b02-9022-1cef3ad4bfff">Axes</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Retrieve information about the dimensions used to filter the data in the <legacyBold>Cellset</legacyBold> with the <legacyLink xlink:href="9c656963-531e-4cd1-b698-d5f42a9b7ba3">FilterAxis</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return or specify the query used to define the <legacyBold>Cellset</legacyBold> with the <legacyLink xlink:href="875a99ea-7f1a-4570-87b1-5ecbebbcf845">Source</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the current state of the <legacyBold>Cellset</legacyBold> (open, closed, executing, or connecting) with the <legacyLink xlink:href="06d480ca-9eb6-4570-a45d-a73539bddd32">State</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Close an open <legacyBold>Cellset</legacyBold> with the <legacyLink xlink:href="a3aa594d-f9d4-4654-8625-ec20153ff5d9">Close</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Retrieve provider-specific information about the <legacyBold>Cellset</legacyBold> with the standard ADO <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="fb303e33-5a85-4e4e-81db-acaaa6f53799">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="2666ad1c-b48e-4b2c-b269-5a9f4e4a7810">Visual Basic Example</link>
<link xlink:href="072fb21a-ec0f-4b02-9022-1cef3ad4bfff">Axes Collection</link>
<link xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>