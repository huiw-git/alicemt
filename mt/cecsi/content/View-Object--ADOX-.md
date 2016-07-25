---
title: "View Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: 8
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
# View Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a filtered set of records or a virtual table. When used in conjunction with the ADO <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object, the <legacyBold>View</legacyBold> object can be used for adding, deleting, or modifying views.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A view is a virtual table, created from other database tables or views. The <legacyBold>View</legacyBold> object allows you to create a view without having to know or use the provider's "CREATE VIEW" syntax.</para>
      <para>With the properties of a <legacyBold>View</legacyBold> object, you can:

</para>
      <list class="bullet">
        <listItem>
          <para>Identify the view with the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Specify the ADO <legacyBold>Command</legacyBold> object that can be used to add, delete, or modify views with the <legacyLink xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return date information with the <legacyLink xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated</legacyLink> and <legacyLink xlink:href="fed09266-1547-4bda-9088-c254d81cc738">DateModified</legacyLink> properties.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="02b5ba88-cacd-4a68-881b-974824ea4a04">View Object Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="d8304849-3f80-4cf3-9425-529d2a8ebedd">Views and Fields Collections Example (VB)</link>
<link xlink:href="b5b4c082-ac29-4f49-a8b8-e21b554c9b0d">Views Append Method Example (VB)</link>
<link xlink:href="a05a0190-352d-44ff-9488-0c94e9fb656e">Views Collection, CommandText Property Example (VB)</link>
<link xlink:href="17df2a83-4166-4df8-8c17-0a33aaac8582">Views Delete Method Example (VB)</link>
<link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>