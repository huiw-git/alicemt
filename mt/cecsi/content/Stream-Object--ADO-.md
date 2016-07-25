---
title: "Stream Object (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
caps.latest.revision: 6
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
# Stream Object (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a stream of binary data or text.</para>
    <para>In tree-structured hierarchies such as a file system or an e-mail system, a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> may have a default binary stream of bits associated with it that contains the contents of the file or the e-mail. A <legacyBold>Stream</legacyBold> object can be used to manipulate fields or records containing these streams of data. A <legacyBold>Stream</legacyBold> object can be obtained in these ways:  </para>
    <list class="bullet">
      <listItem>
        <para>From a URL pointing to an object (typically a file) containing binary or text data. This object can be a simple document, a <legacyBold>Record</legacyBold> object representing a structured document, or a folder.</para>
      </listItem>
      <listItem>
        <para>By opening the default <legacyBold>Stream</legacyBold> object associated with a <legacyBold>Record</legacyBold> object. You can obtain the default stream associated with a <legacyBold>Record</legacyBold> object when the <legacyBold>Record</legacyBold> is opened, to eliminate a round-trip just to open the stream.</para>
      </listItem>
      <listItem>
        <para>By instantiating a <legacyBold>Stream</legacyBold> object. These <legacyBold>Stream</legacyBold> objects can be used to store data for the purposes of your application. Unlike a <legacyBold>Stream</legacyBold> associated with a URL, or the default <legacyBold>Stream</legacyBold> of a <legacyBold>Record</legacyBold>, an instantiated <legacyBold>Stream</legacyBold> has no association with an underlying source by default.</para>
      </listItem>
    </list>
    <para>With the methods and properties of a <legacyBold>Stream</legacyBold> object, you can do the following:  </para>
    <list class="bullet">
      <listItem>
        <para>Open a <legacyBold>Stream</legacyBold> object from a <legacyBold>Record</legacyBold> or URL with the <legacyLink xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open</legacyLink> method.</para>
      </listItem>
      <listItem>
        <para>Close a <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> method.</para>
      </listItem>
      <listItem>
        <para>Input bytes or text to a <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write</legacyLink> and <legacyLink xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText</legacyLink> methods.</para>
      </listItem>
      <listItem>
        <para>Read bytes from the <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="838502de-80f1-4eeb-8838-dd3d9403e567">Read</legacyLink> and <legacyLink xlink:href="be5a409e-cf87-4859-9ea5-713401755a77">ReadText</legacyLink> methods.</para>
      </listItem>
      <listItem>
        <para>Write any <legacyBold>Stream</legacyBold> data still in the ADO buffer to the underlying object with the <legacyLink xlink:href="938522b4-f836-4c80-8d27-a598a000f0ee">Flush</legacyLink> method.</para>
      </listItem>
      <listItem>
        <para>Copy the contents of a <legacyBold>Stream</legacyBold> to another <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="b4aa5714-916b-48b8-8b09-cc2708379602">CopyTo</legacyLink> method.</para>
      </listItem>
      <listItem>
        <para>Control how lines are read from the source file with the <legacyLink xlink:href="0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329">SkipLine</legacyLink>method and the <legacyLink xlink:href="0b20fbb8-6b83-48ec-b442-f96c8a4bafbb">LineSeparator</legacyLink> property.</para>
      </listItem>
      <listItem>
        <para>Determine the end of stream position with the <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink>property and <legacyLink xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS</legacyLink> method.</para>
      </listItem>
      <listItem>
        <para>Save and restore data in files with the <legacyLink xlink:href="8a8594f2-422b-4d2e-94f8-7fe337445900">SaveToFile</legacyLink>and <legacyLink xlink:href="b18d8d38-7354-4a94-b637-6ac035faa433">LoadFromFile</legacyLink> methods.</para>
      </listItem>
      <listItem>
        <para>Specify the character set used for storing the <legacyBold>Stream </legacyBold>with the <legacyLink xlink:href="e42507cb-9b46-4ce4-8191-2948eaf14ca2">Charset</legacyLink> property.</para>
      </listItem>
      <listItem>
        <para>Halt an asynchronous <legacyBold>Stream</legacyBold> operation with the <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink> method.</para>
      </listItem>
      <listItem>
        <para>Determine the number of bytes in a <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="a487c241-d953-4c31-ae7e-6358d5cf6733">Size</legacyLink> property.</para>
      </listItem>
      <listItem>
        <para>Control the current position within a <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink> property.</para>
      </listItem>
      <listItem>
        <para>Determine the type of data in a <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> property.</para>
      </listItem>
      <listItem>
        <para>Determine the current state of the <legacyBold>Stream</legacyBold> (closed, open, or executing) with the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property.</para>
      </listItem>
      <listItem>
        <para>Specify the access mode for the <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property.</para>
      </listItem>
    </list>
    <alert class="note">
      <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
    </alert>
    <para>The <legacyBold>Stream</legacyBold> object is safe for scripting.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="9b0eed90-c38c-4aa6-9040-5827f8c46b94">Stream Object Properties, Methods, and Events</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="4d68868e-2611-4b5c-9a89-7caa5f753151">Records and Streams</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>