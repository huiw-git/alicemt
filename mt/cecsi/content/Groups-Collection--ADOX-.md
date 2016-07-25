---
title: "Groups Collection (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
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
# Groups Collection (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains all stored <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink> objects of a catalog or user.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>Groups</legacyBold> collection of a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink> represents all of the catalog's group accounts. The <legacyBold>Groups</legacyBold> collection for a <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink> represents only the group to which the user belongs.</para>
      <para>The <legacyLink xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append</legacyLink> method for a <legacyBold>Groups</legacyBold> collection is unique for ADOX. You can:  </para>
      <list class="bullet">
        <listItem>
          <para>Add a new security group to the collection with the <unmanagedCodeEntityReference>Append</unmanagedCodeEntityReference> method.</para>
        </listItem>
      </list>
      <para>The remaining properties and methods are standard to ADO collections. You can:  </para>
      <list class="bullet">
        <listItem>
          <para>Access a group in the collection with the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the number of groups contained in the collection with the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Remove a group from the collection with the <legacyLink xlink:href="e6b6e3a4-8952-4d79-81f4-51019c338374">Delete</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Update the objects in the collection to reflect the current database schema with the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>Before appending a <unmanagedCodeEntityReference>Group</unmanagedCodeEntityReference> object to the <legacyBold>Groups</legacyBold> collection of a <unmanagedCodeEntityReference>User</unmanagedCodeEntityReference> object, a <unmanagedCodeEntityReference>Group</unmanagedCodeEntityReference> object with the same <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> as the one to be appended must already exist in the <legacyBold>Groups</legacyBold> collection of the <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference>.</para>
      </alert>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="0776457f-bf78-4a79-96bf-a17136d45811">Groups Collection Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>