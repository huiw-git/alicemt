---
title: "Record Object (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: db83ed2c-a8e3-460c-8682-64667e4d5d01
caps.latest.revision: 5
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
# Record Object (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a row from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> or the data provider, or an object returned by a semi-structured data provider, such as a file or directory.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>Record</legacyBold> object represents one row of data, and has some conceptual similarities with a one-row <legacyBold>Recordset</legacyBold>. Depending on the capabilities of your provider, <legacyBold>Record</legacyBold> objects may be returned directly from your provider instead of a one-row <legacyBold>Recordset</legacyBold>, for example when an SQL query that selects only one row is executed. Or, a <legacyBold>Record</legacyBold> object can be obtained directly from a <legacyBold>Recordset</legacyBold> object. Or, a <legacyBold>Record</legacyBold> can be returned directly from a provider to semi-structured data, such as the Microsoft Exchange OLE DB provider.</para>
      <para>You can view the fields associated with the <legacyBold>Record</legacyBold> object by way of the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection on the <legacyBold>Record</legacyBold> object. ADO allows object-valued columns including <legacyBold>Recordset</legacyBold>, <legacyBold>SafeArray</legacyBold>, and scalar values in the <legacyBold>Fields</legacyBold> collection of <legacyBold>Record</legacyBold> objects.</para>
      <para>If the <legacyBold>Record</legacyBold> object represents a row in a <legacyBold>Recordset</legacyBold>, it is possible to return to that original <legacyBold>Recordset</legacyBold> with the <legacyLink xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source</legacyLink> property.</para>
      <para>The <legacyBold>Record</legacyBold> object can also be used by semi-structured data providers such as the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>, to model tree-structured namespaces. Each node in the tree is a <legacyBold>Record</legacyBold> object with associated columns. The columns can represent the attributes of that node and other relevant information. The <legacyBold>Record</legacyBold> object can represent both a leaf node and a non-leaf node in the tree structure. Non-leaf nodes have other nodes as their contents, but leaf nodes do not have such contents. Leaf nodes typically contain binary streams of data and non-leaf nodes may also have a default binary stream associated with them. Properties on the <legacyBold>Record</legacyBold> object identify the type of node.</para>
      <para>The <legacyBold>Record</legacyBold> object also represents an alternative way for navigating hierarchically organized data. A <legacyBold>Record</legacyBold> object may be created to represent the root of a specific sub-tree in a large tree structure and new <legacyBold>Record</legacyBold> objects may be opened to represent child nodes.</para>
      <para>A resource (for example, a file or directory) can be uniquely identified by an absolute URL. A <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object is implicitly created and set to the <legacyBold>Record</legacyBold> object when the <legacyBold>Record</legacyBold> is opened by using an absolute URL. A <legacyBold>Connection</legacyBold> object may explicitly be set to the <legacyBold>Record</legacyBold> object via the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property. The files and directories that can be accessed by using the <legacyBold>Connection</legacyBold> object define the <legacyItalic>context</legacyItalic> in which <legacyBold>Record</legacyBold> operations may occur.</para>
      <para>Data modification and navigation methods on the <legacyBold>Record</legacyBold> object also accept a relative URL, which locates a resource using an absolute URL or the <legacyBold>Connection</legacyBold> object context as a starting point.</para>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
      <para>A <legacyBold>Connection</legacyBold> object is associated with each <legacyBold>Record</legacyBold> object. Therefore, <legacyBold>Record</legacyBold> object operations can be part of a transaction by invoking <legacyBold>Connection</legacyBold> object transaction methods.</para>
      <para>The <legacyBold>Record</legacyBold> object does not support ADO events, and therefore will not respond to notifications.</para>
      <para>With the methods and properties of a <legacyBold>Record</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Set or return the associated <legacyBold>Connection</legacyBold> object with the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Indicate access permissions with the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the URL of the directory, if any, that contains the resource represented by the <legacyBold>Record</legacyBold> with the <legacyLink xlink:href="65120ce6-3900-4cd4-b322-3b9816d74737">ParentURL</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Indicate the absolute URL, relative URL, or <legacyBold>Recordset</legacyBold> from which the <legacyBold>Record</legacyBold> is derived with the <legacyLink xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Indicate the current status of the <legacyBold>Record</legacyBold> with the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Indicate the type of <legacyBold>Record</legacyBold> — <legacyItalic>simple</legacyItalic>, <legacyItalic>collection</legacyItalic>, or <legacyItalic>structured document</legacyItalic> — with the <legacyLink xlink:href="790e46a2-13d2-451e-a8be-130bd9a206a4">RecordType</legacyLink>property.</para>
        </listItem>
        <listItem>
          <para>Stop execution of an asynchronous operation with the <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Disassociate the <legacyBold>Record</legacyBold> from a data source with the <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Copy the file or directory represented by a <legacyBold>Record</legacyBold> to another location with the <legacyLink xlink:href="b9bcf272-3c74-479f-95dd-0229a32e98fc">CopyRecord</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Delete the file, or directory and subdirectories, represented by a <legacyBold>Record</legacyBold> with the <legacyLink xlink:href="2726498c-dbd8-4266-983b-ae7d62c39142">DeleteRecord</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Open a <legacyBold>Recordset</legacyBold> that contains rows that represent the subdirectories and files of the entity represented by the <legacyBold>Record</legacyBold> with the <legacyLink xlink:href="b3f09bac-4f66-49f6-aa5a-6fbb4fb28338">GetChildren</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Move (rename) the file, or directory and subdirectories, represented by a <legacyBold>Record</legacyBold> to another location with the <legacyLink xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Associate the <legacyBold>Record</legacyBold> with an existing data source, or create a new file or directory with the <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open</legacyLink> method.</para>
        </listItem>
      </list>
      <para>The <legacyBold>Record</legacyBold> object is safe for scripting.</para>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="dadde268-bd0f-4ba0-8775-83a5cd3e258a">Record Object Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="4d68868e-2611-4b5c-9a89-7caa5f753151">Records and Streams</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>