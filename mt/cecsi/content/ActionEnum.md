---
title: "ActionEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f948febd-c885-4621-823b-421e116fec4e
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
# ActionEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the type of action to be performed when <legacyLink xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions</legacyLink> is called.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
            <TD>
              <para>Value</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>adAccessDeny</legacyBold> </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>The group or user will be denied the specified permissions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adAccessGrant</legacyBold> </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>The group or user will have at least the requested permissions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adAccessRevoke</legacyBold> </para>
            </TD>
            <TD>
              <para>4</para>
            </TD>
            <TD>
              <para>Any explicit access rights of the group or user will be revoked.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adAccessSet</legacyBold> </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>The group or user will have exactly the requested permissions.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>