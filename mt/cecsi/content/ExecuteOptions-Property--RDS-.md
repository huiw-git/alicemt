---
title: "ExecuteOptions Property (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 62a4fd88-afc3-4f1f-b978-40710a30c4e9
caps.latest.revision: 13
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
# ExecuteOptions Property (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates whether asynchronous execution is enabled.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns one of the following values.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
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
                <legacyBold>adcExecSync</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Executes the next refresh of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> synchronously.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adcExecAsync</legacyBold> </para>
            </TD>
            <TD>
              <para>Default. Executes the next refresh of the <legacyBold>Recordset</legacyBold> asynchronously.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>Each executable file that uses these constants must provide declarations for them. You can cut and paste the constant declarations that you want from the file Adcvbs.inc, located in the default installation folder for the RDS library.</para>
      </alert>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>If <legacyBold>ExecuteOptions</legacyBold> is set to <legacyBold>adcExecAsync</legacyBold>, then this asynchronously executes the next <legacyBold>Refresh</legacyBold> call on the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object's <legacyBold>Recordset</legacyBold>.</para>
      <para>If you try to call <legacyLink xlink:href="3957197a-f543-4d6b-9e11-67a77c2063b7">Reset</legacyLink>, <legacyLink xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh</legacyLink>, <legacyLink xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges</legacyLink>, <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink>, or <legacyLink xlink:href="a29e3fb9-306d-497a-9a59-1856a914e5e9">Recordset</legacyLink> while another asynchronous operation that might change the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object's <legacyBold>Recordset</legacyBold> is executing, an error occurs.</para>
      <para>If an error occurs during an asynchronous operation, the <legacyBold>RDS.DataControl</legacyBold> object's <legacyLink xlink:href="5be75bc7-1171-4440-a37e-c8cc6b5cd865">ReadyState</legacyLink> value changes from <legacyBold>adcReadyStateLoaded</legacyBold> to <legacyBold>adcReadyStateComplete</legacyBold>, and the <legacyBold>Recordset</legacyBold> property value remains <legacyItalic>Nothing</legacyItalic>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="753a4a3d-0fba-40b8-86e7-50b34182ca69">VBScript Example</link>
<link xlink:href="560b5b3d-fba9-4275-8920-9c3e186134f7">Cancel Method (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>