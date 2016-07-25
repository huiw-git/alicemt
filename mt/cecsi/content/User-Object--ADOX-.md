---
title: "User Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f68e32ce-ef7c-407d-bdb5-d280947ae0e2
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
# User Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a user account that has access permissions within a secured database.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users</legacyLink> collection of a <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink> represents all the catalog's users. The <unmanagedCodeEntityReference>Users</unmanagedCodeEntityReference> collection for a <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink> represents only the users of the specific group.</para>
      <para>With the properties, collections, and methods of a <unmanagedCodeEntityReference>User</unmanagedCodeEntityReference> object, you can:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the user with the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Change the password for a user with the <legacyLink xlink:href="d187fbc6-5fac-4abb-803d-bf344dcf0302">ChangePassword</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Determine whether a user has read, write, or delete permissions with the <legacyLink xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions</legacyLink> and <legacyLink xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions</legacyLink> methods.</para>
        </listItem>
        <listItem>
          <para>Access the groups to which a user belongs with the <legacyLink xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Access provider-specific properties with the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Determine the <legacyLink xlink:href="a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273">ParentCatalog</legacyLink> for a user.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="becd590c-0db7-485c-8bf4-fa3456e4ba20">User Object Properties, Methods, and Events</legacyLink> </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="aa366d98-8c7a-4189-bdd8-1d663b243d33">GetPermissions and SetPermissions Methods Example (VB)</link>
<link xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups Collection</link>
<link xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>