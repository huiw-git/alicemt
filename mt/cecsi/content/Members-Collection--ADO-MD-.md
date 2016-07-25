---
title: "Members Collection (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
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
# Members Collection (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains the <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> objects from a level or a position along an axis.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>Members</legacyBold> collection is used to contain the following types of members:  </para>
      <list class="bullet">
        <listItem>
          <para>The members that make up a level in a cube. These are contained in the <legacyBold>Members</legacyBold> collection of a <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink> object. For example, using the sample from <legacyLink xlink:href="ce37fa06-c581-4d80-9a9b-c3aa66408909">Overview of Multidimensional Schemas and Data</legacyLink>, the four members of the Countries level are Canada, USA, UK, and Germany.</para>
        </listItem>
        <listItem>
          <para>The members that are the children of a specific member within a hierarchy. These members are returned by the <legacyLink xlink:href="61d36468-1ccd-467a-9cb5-17d0bfacc766">Children</legacyLink> property of the parent <legacyBold>Member</legacyBold> object. For example, again using the same sample, the two children of the Canada member are Canada-East and Canada-West.</para>
        </listItem>
        <listItem>
          <para>The members that define a specific position along an axis of a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">cellset</legacyLink>. Using the cellset from <legacyLink xlink:href="84387746-aa3e-44fd-ad6c-a8214a6966dc">Working with Multidimensional Data</legacyLink> as an example, the two members of the first position on the x-axis are Valentine and Seattle. These members are contained by the <legacyBold>Members</legacyBold> collection of a <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink> object.</para>
        </listItem>
      </list>
      <para>
        <legacyBold>Members</legacyBold> is a standard ADO collection. With the properties and methods of a collection, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Obtain the number of objects in the collection with the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return an object from the collection with the default <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Update the objects in the collection from the provider with the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="da2c0761-fe23-421b-acbf-d97dfa02d2b9">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="87bbd4ad-bb1a-4123-93ef-99ef47fd970b">VBScript Example</link>
<link xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>