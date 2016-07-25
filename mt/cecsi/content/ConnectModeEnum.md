---
title: "ConnectModeEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
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
# ConnectModeEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the available permissions for modifying data in a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, opening a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>, or specifying values for the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property of the <legacyBold>Record</legacyBold> and <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> objects.</para>
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
              <legacyBold>adModeRead</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Indicates read-only permissions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeReadWrite</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Indicates read/write permissions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeRecursive</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x400000</para>
          </TD>
          <TD>
            <para>Used in conjunction with the other <legacyItalic>*ShareDeny*</legacyItalic> values (<legacyBold>adModeShareDenyNone</legacyBold>, <legacyBold>adModeShareDenyWrite</legacyBold>, or <legacyBold>adModeShareDenyRead</legacyBold>) to propagate sharing restrictions to all sub-records of the current <legacyBold>Record</legacyBold>. It has no affect if the <legacyBold>Record</legacyBold> does not have any children. A run-time error is generated if it is used with <legacyBold>adModeShareDenyNone</legacyBold> only. However, it can be used with <legacyBold>adModeShareDenyNone</legacyBold> when combined with other values. For example, you can use "<legacyBold>adModeRead</legacyBold> Or <legacyBold>adModeShareDenyNone</legacyBold> Or <legacyBold>adModeRecursive</legacyBold>".</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeShareDenyNone</legacyBold>
            </para>
          </TD>
          <TD>
            <para>16</para>
          </TD>
          <TD>
            <para>Allows others to open a connection with any permissions. Neither read nor write access can be denied to others.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeShareDenyRead</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Prevents others from opening a connection with read permissions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeShareDenyWrite</legacyBold>
            </para>
          </TD>
          <TD>
            <para>8</para>
          </TD>
          <TD>
            <para>Prevents others from opening a connection with write permissions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeShareExclusive</legacyBold>
            </para>
          </TD>
          <TD>
            <para>12</para>
          </TD>
          <TD>
            <para>Prevents others from opening a connection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeUnknown</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Default. Indicates that the permissions have not yet been set or cannot be determined.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adModeWrite</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates write-only permissions.</para>
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
              <para>AdoEnums.ConnectMode.READ</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectMode.READWRITE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(There is no equivalent of AdoEnums.ConnectMode.RECURSIVE)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectMode.SHAREDENYNONE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectMode.SHAREDENYREAD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectMode.SHAREDENYWRITE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectMode.SHAREEXCLUSIVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectMode.UNKNOWN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectMode.WRITE</para>
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
                <link xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode Property</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>