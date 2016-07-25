---
title: "Users Collection (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
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
# Users Collection (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains all stored <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink> objects of a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">catalog</legacyLink> or <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">group</legacyLink>.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <unmanagedCodeEntityReference>Users</unmanagedCodeEntityReference> collection of a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink> represents all the catalog's users. The <unmanagedCodeEntityReference>Users</unmanagedCodeEntityReference> collection for a <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink> represents only the users that have a membership in the specific group.</para>
      <para>The <legacyLink xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append</legacyLink> method for a <unmanagedCodeEntityReference>Users</unmanagedCodeEntityReference> collection is unique for ADOX. You can:  </para>
      <list class="bullet">
        <listItem>
          <para>Add a new user to the collection by using the <unmanagedCodeEntityReference>Append</unmanagedCodeEntityReference> method.</para>
        </listItem>
      </list>
      <para>The remaining properties and methods are standard to ADO collections. You can:  </para>
      <list class="bullet">
        <listItem>
          <para>Access a user in the collection with the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the number of users contained in the collection with the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Remove a user from the collection with the <legacyLink xlink:href="e6b6e3a4-8952-4d79-81f4-51019c338374">Delete</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Update the objects in the collection to reflect the current database's schema with the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>Before appending a <legacyBold>User</legacyBold> object to the <legacyBold>Users</legacyBold> collection of a <legacyBold>Group</legacyBold> object, a <legacyBold>User</legacyBold> object with the same <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> as the one to be appended must already exist in the <legacyBold>Users</legacyBold> collection of the <legacyBold>Catalog</legacyBold>.</para>
      </alert>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="1b89a12f-96bc-48b3-a88d-4da74780ea40">Users Collection Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="aa366d98-8c7a-4189-bdd8-1d663b243d33">GetPermissions and SetPermissions Methods Example (VB)</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>