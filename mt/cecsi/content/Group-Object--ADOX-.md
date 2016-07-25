---
title: "Group Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
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
# Group Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a group account that has access permissions within a secured database.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups</legacyLink> collection of a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink> represents all the catalog's group accounts. The <legacyBold>Groups</legacyBold> collection for a <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink> represents only the group to which the user belongs.</para>
      <para>With the properties, collections, and methods of a <legacyBold>Group</legacyBold> object, you can:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the group with the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Determine whether a group has read, write, or delete permissions with the <legacyLink xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions</legacyLink> and <legacyLink xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions</legacyLink> methods.</para>
        </listItem>
        <listItem>
          <para>Access the user accounts that have memberships in the group with the <legacyLink xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Access provider-specific properties with the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="ba9642d0-9025-4eff-8885-e6e7f8154c73">Group Object Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups Collection</link>
<link xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>