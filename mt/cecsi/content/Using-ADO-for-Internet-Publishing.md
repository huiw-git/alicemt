---
title: "Using ADO for Internet Publishing"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
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
# Using ADO for Internet Publishing
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyLink xlink:href="4869aafa-7401-4ce1-93ce-45406a60274f">The OLE DB Provider for Internet Publishing</legacyLink> shows a specific example of accessing heterogeneous data with ADO. Although the examples in this section will be specific to using the Internet Publishing Provider, the principles demonstrated should be similar when using ADO with other providers to heterogeneous data, such as a provider to an e-mail store.</para>
  </introduction>
  <section>
    <title>URLs</title>
    <content>
      <para>Uniform Resource Locators (URLs) can be used as an alternative to connection strings and command text to specify data sources and the location of files and directories. You can use URLs with the existing <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> and <legacyBold>Recordset</legacyBold> objects and with the <legacyBold>Record</legacyBold> and <legacyBold>Stream</legacyBold> objects.</para>
      <para>For more information about how to use URLs, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Record Fields</title>
    <content>
      <para>The distinguishing difference between heterogeneous data and homogeneous data is that for the former, each row of data, or <legacyBold>Record</legacyBold>, can have a different set of columns, or <legacyBold>Fields</legacyBold>. For homogeneous data, each row has the same set of columns. For more information about the fields specific to the Internet Publishing Provider, see <legacyLink xlink:href="77f95e0a-0cf2-411a-a792-593f77330fbd">Records and Provider-Supplied Extra Fields</legacyLink>.</para>
    </content>
    <sections>
      <section>
        <title>Appending New Fields</title>
        <content>
          <para>Several ADO objects have been enhanced to work together with <legacyBold>Record</legacyBold> and <legacyBold>Stream</legacyBold> objects.  </para>
          <list class="bullet">
            <listItem>
              <para>The <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> method, which creates and adds a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object to the collection, can also specify the value of the <legacyBold>Field</legacyBold>.</para>
            </listItem>
            <listItem>
              <para>The <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method finalizes the addition or deletion of fields to the collection.</para>
            </listItem>
            <listItem>
              <para>As a shortcut and alternative to the <legacyBold>Append</legacyBold> method, you can create fields by assigning a value to an undefined or previously deleted field.</para>
            </listItem>
          </list>
          <para>This section contains the following topics.  </para>
          <list class="bullet">
            <listItem>
              <para>                 <legacyLink xlink:href="4869aafa-7401-4ce1-93ce-45406a60274f">The OLE DB Provider for Internet Publishing</legacyLink>               </para>
            </listItem>
            <listItem>
              <para>                 <legacyLink xlink:href="2f551969-0fd9-41ee-b81d-100975a4bdc2">Internet Publishing Scenario</legacyLink>               </para>
            </listItem>
            <listItem>
              <para>                 <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>               </para>
            </listItem>
            <listItem>
              <para>                 <legacyLink xlink:href="77f95e0a-0cf2-411a-a792-593f77330fbd">Records and Provider-Supplied Fields</legacyLink>               </para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
<link xlink:href="667673f2-3151-432b-894a-3fc60b704ea4">What's New in ADO</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>