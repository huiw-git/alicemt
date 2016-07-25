---
title: "FetchOptions Property (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 7b2e254a-9354-4541-bc98-bb185276388f
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
# FetchOptions Property (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the type of asynchronous fetching.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Setting and Return Values</title>
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
                <legacyBold>adcFetchUpFront</legacyBold>
              </para>
            </TD>
            <TD>
              <para>All the records of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> are fetched before control is returned to the application. The complete <legacyBold>Recordset</legacyBold> is fetched before the application is allowed to do anything with it.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adcFetchBackground</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Control can return to the application as soon as the first batch of records has been fetched. A subsequent read of the <legacyBold>Recordset</legacyBold> that attempts to access a record not fetched in the first batch will be delayed until the sought record is actually fetched, at which time control returns to the application.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adcFetchAsync</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Default. Control returns immediately to the application while records are fetched in the background. If the application attempts to read a record that hasn't yet been fetched, the record closest to the sought record will be read and control will return immediately, indicating that the current end of the <legacyBold>Recordset</legacyBold> has been reached. For example, a call to <legacyLink xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveLast</legacyLink> will move the current record position to the last record actually fetched, even though more records will continue to populate the <legacyBold>Recordset</legacyBold>.</para>
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
      <para>In a Web application, you will usually want to use <legacyBold>adcFetchAsync</legacyBold> (the default value), because it provides better performance. In a compiled client application, you will usually want to use <legacyBold>adcFetchBackground</legacyBold>.</para>
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