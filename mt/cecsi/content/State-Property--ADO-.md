---
title: "State Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
caps.latest.revision: 7
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
# State Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates for all applicable objects whether the state of the object is open or closed. If the object is executing an asynchronous method, indicates whether the current state of the object is connecting, executing, or retrieving.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <languageKeyword>Long</languageKeyword> value that can be an <legacyLink xlink:href="32746558-097b-4749-989e-519aadf7e3f4">ObjectStateEnum</legacyLink> value. The default value is <legacyBold>adStateClosed</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>You can use the <unmanagedCodeEntityReference>State</unmanagedCodeEntityReference> property to determine the current state of a given object at any time.</para>
      <para>The object's <unmanagedCodeEntityReference>State</unmanagedCodeEntityReference> property can have a combination of values. For example, if a statement is executing, this property will have a combined value of <legacyBold>adStateOpen</legacyBold> and <legacyBold>adStateExecuting</legacyBold>.</para>
      <para>The <unmanagedCodeEntityReference>State</unmanagedCodeEntityReference> property is read-only.</para>
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
                <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
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
  <relatedTopics>
<link xlink:href="4de7336a-b5ea-43f1-b750-5fa302b5b756">Visual Basic Example</link>
<link xlink:href="c6bd2609-4c49-462f-a1aa-7bee0f615adb">Visual C++ Example</link>
<link xlink:href="4c1e61ed-6569-44a9-b0c8-75b820a64cb6">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>