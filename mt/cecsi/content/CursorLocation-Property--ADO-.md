---
title: "CursorLocation Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
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
# CursorLocation Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the location of the cursor service.</para>
  </introduction>
  <section>
    <title>Settings And Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Long</languageKeyword> value that can be set to one of the <legacyLink xlink:href="acb255ff-1734-4b70-89bb-aef862b4c63b">CursorLocationEnum</legacyLink> values.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>This property allows you to choose between various cursor libraries accessible to the provider. Usually, you can choose between using a client-side cursor library or one that is located on the server.</para>
      <para>This property setting affects connections established only after the property has been set. Changing the <legacyBold>CursorLocation</legacyBold> property has no effect on existing connections.</para>
      <para>Cursors returned by the <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink> method inherit this setting. <legacyBold>Recordset</legacyBold> objects will automatically inherit this setting from their associated connections.</para>
      <para>This property is read/write on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> or a closed <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, and read-only on an open <legacyBold>Recordset</legacyBold>.</para>
      <alert class="note">
        <para> <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Recordset</legacyBold> or <legacyBold>Connection</legacyBold> object, the <legacyBold>CursorLocation</legacyBold> property can only be set to <legacyBold>adUseClient</legacyBold>.</para>
      </alert>
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
                <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>