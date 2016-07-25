---
title: "ReadyState Property (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 5be75bc7-1171-4440-a37e-c8cc6b5cd865
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
# ReadyState Property (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the progress of a <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl</legacyLink> object as it retrieves data into its <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
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
                <legacyBold>adcReadyStateLoaded</legacyBold>
              </para>
            </TD>
            <TD>
              <para>The current query is still executing and no rows have been fetched. The <legacyBold>DataControl </legacyBold>object's <legacyBold>Recordset</legacyBold> is not available for use.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adcReadyStateInteractive</legacyBold>
              </para>
            </TD>
            <TD>
              <para>An initial set of rows retrieved by the current query has been stored in the <legacyBold>DataControl</legacyBold> object's <legacyBold>Recordset</legacyBold> and are available for use. The remaining rows are still being fetched.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adcReadyStateComplete</legacyBold>
              </para>
            </TD>
            <TD>
              <para>All rows retrieved by the current query have been stored in the <legacyBold>DataControl</legacyBold> object's <legacyBold>Recordset</legacyBold> and are available for use.</para>
              <para>This state will also exist if an operation aborted due to an error, or if the <legacyBold>Recordset</legacyBold> object is not initialized.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>Each client-side executable file that uses these constants must provide declarations for them. You can cut and paste the constant declarations you want from the file Adcvbs.inc, located in the default installation folder for the RDS library.</para>
      </alert>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyLink xlink:href="bf2ae3ac-bfe4-4709-b50a-ea7c282c3164">onReadyStateChange</legacyLink> event to monitor changes in the <legacyBold>ReadyState</legacyBold> property during an asynchronous query operation. This is more efficient than periodically checking the value of the property.</para>
      <para>If an error occurs during an asynchronous operation, the <legacyBold>ReadyState</legacyBold> property changes to <legacyBold>adcReadyStateComplete</legacyBold>, the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property changes from <legacyBold>adStateExecuting</legacyBold> to <legacyBold>adStateClosed</legacyBold>, and the <legacyBold>Recordset</legacyBold> object <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property remains <legacyItalic>Nothing</legacyItalic>.</para>
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
<link xlink:href="e3e18da4-0511-4ece-a35d-699978bc28c6">VBScript Example</link>
<link xlink:href="560b5b3d-fba9-4275-8920-9c3e186134f7">Cancel Method (RDS)</link>
<link xlink:href="62a4fd88-afc3-4f1f-b978-40710a30c4e9">ExecuteOptions Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>