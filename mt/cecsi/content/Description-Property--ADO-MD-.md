---
title: "Description Property (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6d626d35-0bf3-4f24-9934-ad9c9c91273a
caps.latest.revision: 10
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
# Description Property (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns a text explanation of the current object.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <legacyBold>String </legacyBold>and is read-only.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>For <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> objects, <unmanagedCodeEntityReference>Description</unmanagedCodeEntityReference> applies only to measure and formula members. <unmanagedCodeEntityReference>Description</unmanagedCodeEntityReference> returns an empty string ("") for all other types of members. For more information about the various types of members, see the <legacyLink xlink:href="34698910-64b9-41d8-8531-9de12f2b1e32">Type</legacyLink> property.</para>
      <para>This property is only supported on <unmanagedCodeEntityReference>Member</unmanagedCodeEntityReference> objects that belong to a <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink> object. An error occurs when this property is referenced from <unmanagedCodeEntityReference>Member</unmanagedCodeEntityReference> objects belonging to a <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink> object.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">Dimension Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="034af340-ac79-494e-ba5e-2b57da1cb9de">Hierarchy Object</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member Object</link>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>