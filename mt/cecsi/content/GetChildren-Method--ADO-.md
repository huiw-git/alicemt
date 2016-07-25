---
title: "GetChildren Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
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
# GetChildren Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> whose rows represent the children of a collection <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set</legacyBold><parameterReference> recordset = record.</parameterReference><legacyBold>GetChildren</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>A <legacyBold>Recordset</legacyBold> object for which each row represents a child of the current <legacyBold>Record</legacyBold> object. For example, the children of a <legacyBold>Record</legacyBold> that represents a directory would be the files and subdirectories contained within the parent directory.</para>
    </content>
  </returnValue>
  <languageReferenceRemarks>
    <content>
      <para>The provider determines what columns exist in the returned <legacyBold>Recordset</legacyBold>. For example, a document source provider always returns a resource <legacyBold>Recordset</legacyBold>.</para>
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
                <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>