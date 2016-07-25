---
title: "Procedure Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
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
# Procedure Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a stored procedure. When used in conjunction with the ADO <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object, the <legacyBold>Procedure</legacyBold> object can be used for adding, deleting, or modifying stored procedures.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyBold>Procedure</legacyBold> object allows you to create a stored procedure without having to know or use the provider's "CREATE PROCEDURE" syntax.</para>
      <para>With the properties of a <legacyBold>Procedure</legacyBold> object, you can:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the procedure with the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Specify the ADO <legacyBold>Command</legacyBold> object that can be used to create or execute the procedure with the <legacyLink xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return date information with the <legacyLink xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated</legacyLink> and <legacyLink xlink:href="fed09266-1547-4bda-9088-c254d81cc738">DateModified</legacyLink> properties.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="522f6447-ba9e-45f5-a185-37b312e126d4">Procedure Object Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="413263a8-05c0-4404-929d-69f82b987ba3">Command and CommandText Properties Example (VB)</link>
<link xlink:href="7df1089e-69b7-476e-9244-19947c087351">Parameters Collection, Command Property Example (VB)</link>
<link xlink:href="ce83b966-474b-4f57-8eb9-370996dfc5c0">Procedures Append Method Example (VB)</link>
<link xlink:href="94f1ac93-e778-4a40-a85e-94bce5316ac7">Procedures Delete Method Example (VB)</link>
<link xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>