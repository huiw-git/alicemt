---
title: "Name Property (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 4a04380b-51dc-4aaf-8d25-123cdd589641
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
# Name Property (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the name of an object.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <para>Returns a <languageKeyword>String</languageKeyword> and is read-only.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>You can retrieve the <unmanagedCodeEntityReference>Name</unmanagedCodeEntityReference> property of an object by an ordinal reference, after which you can refer to the object directly by name. For example, if <codeInline>cdf.CubeDefs(0).Name</codeInline> yields "Bobs Video Store", you can refer to this <legacyLink xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef</legacyLink> as <codeInline>cdf.CubeDefs("Bobs Video Store")</codeInline>.</para>
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
                <link xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="11f6f896-d69c-44a4-94cd-d54c93140e4a">Catalog Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef Object</link>
              </para>
            </TD>
          </tr>
          <tr>
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
            <TD>
              <para>
                <link xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level Object</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member Object</link>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="3aae1107-2f81-413c-8eda-ef96c3df1b8a">Visual Basic Example</link>
<link xlink:href="d90763b8-ba3f-48f8-95b2-e6a0e52296e1">Caption Property</link>
<link xlink:href="6d626d35-0bf3-4f24-9934-ad9c9c91273a">Description Property</link>
<link xlink:href="5b977956-e252-4861-8425-f1aaf6b80130">UniqueName Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>