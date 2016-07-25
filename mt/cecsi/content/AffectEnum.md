---
title: "AffectEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
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
# AffectEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies which records are affected by an operation.</para>
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
              <legacyBold>adAffectAll</legacyBold> </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>If there is not a <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> applied to the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>, affects all records.</para>
            <para>If the <unmanagedCodeEntityReference>Filter</unmanagedCodeEntityReference> property is set to a string criteria (such as "Author='Smith'"), then the operation affects visible records in the current chapter.</para>
            <para>If the <unmanagedCodeEntityReference>Filter</unmanagedCodeEntityReference> property is set to a member of the <legacyLink xlink:href="b22e725e-84bd-4286-a070-290c278c3783">FilterGroupEnum</legacyLink> or an array of bookmarks, then the operation will affect all rows of the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
            <alert class="note">
              <para> <legacyBold>adAffectAll</legacyBold> is hidden in the Visual Basic Object Browser.</para>
            </alert>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adAffectAllChapters</legacyBold>           </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Affects all records in all sibling chapters of the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>, including those not visible via any <unmanagedCodeEntityReference>Filter</unmanagedCodeEntityReference> that is currently applied.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adAffectCurrent</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Affects only the current record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adAffectGroup</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Affects only records that satisfy the current <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property setting. You must set the <unmanagedCodeEntityReference>Filter</unmanagedCodeEntityReference> property to a <unmanagedCodeEntityReference>FilterGroupEnum</unmanagedCodeEntityReference> value or an array of <unmanagedCodeEntityReference>Bookmarks</unmanagedCodeEntityReference> to use this option.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>AdoEnums.Affect.ALL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Affect.ALLCHAPTERS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Affect.CURRENT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Affect.GROUP</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete Method (ADO Recordset)</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>