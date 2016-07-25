---
title: "Cancel Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e0db4e15-6787-41e2-8f13-9e9b524d620a
caps.latest.revision: 12
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
# Cancel Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Cancels execution of a pending asynchronous method call.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>object</parameterReference><legacyBold>.Cancel</legacyBold></legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Cancel</legacyBold> method to terminate execution of an asynchronous method call: that is, a method invoked with the <legacyBold>adAsyncConnect</legacyBold>, <legacyBold>adAsyncExecute</legacyBold>, or <legacyBold>adAsyncFetch </legacyBold>option.</para>
      <para>The following table shows what task is terminated when you use the <unmanagedCodeEntityReference>Cancel</unmanagedCodeEntityReference> method on a particular type of object.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>If <legacyItalic>object</legacyItalic> is a</para>
            </TD>
            <TD>
              <para>The last asynchronous call to this method is terminated</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink>             </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>             </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink> or <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>             </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="b9bcf272-3c74-479f-95dd-0229a32e98fc">CopyRecord</legacyLink>, <legacyLink xlink:href="2726498c-dbd8-4266-983b-ae7d62c39142">DeleteRecord</legacyLink>, <legacyLink xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord</legacyLink>, or <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open</legacyLink></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>             </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink>             </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open</legacyLink>             </para>
            </TD>
          </tr>
        </tbody>
      </table>
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
<link xlink:href="5c0530ad-68d0-4cba-b1af-9386d566c7c5">Visual Basic Example</link>
<link xlink:href="4ade106d-063d-486e-bc4d-a1a6b6e0bea9">VBScript Example</link>
<link xlink:href="7e0eaa39-0c24-4d8c-87e8-f9c4fd3455e7">Visual C++ Example</link>
<link xlink:href="3e41ee6f-5138-4d32-98ac-05e30a2a6fd2">Visual J++ Example</link>
<link xlink:href="560b5b3d-fba9-4275-8920-9c3e186134f7">Cancel Method (RDS)</link>
<link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
<link xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate Method</link>
<link xlink:href="76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650">CancelUpdate Method (RDS)</link>
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
<link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>