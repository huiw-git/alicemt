---
title: "Microsoft OLE DB Provider for Internet Publishing"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
caps.latest.revision: 9
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
# Microsoft OLE DB Provider for Internet Publishing
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft OLE DB Provider for Internet Publishing allows ADO to access resources served by Microsoft FrontPage or Microsoft Internet Information Server. Resources include web source files such as HTML files, or Windows 2000 web folders.</para>
  </introduction>
  <section>
    <title>Connection String Parameters</title>
    <content>
      <para>To connect to this provider, set the <legacyItalic>Provider</legacyItalic> argument of the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to:</para>
      <code>MSDAIPP.DSO</code>
      <para>This value can also be set or read using the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property.</para>
    </content>
  </section>
  <section>
    <title>Typical Connection String</title>
    <content>
      <para>A typical connection string for this provider is:</para>
      <code>"Provider=MSDAIPP.DSO;Data Source=<legacyItalic>ResourceURL</legacyItalic>;User ID=<legacyItalic>MyUserID</legacyItalic>;Password=<legacyItalic>MyPassword</legacyItalic>;"</code>
      <para>-or-</para>
      <code>"URL=<legacyItalic>ResourceURL</legacyItalic>;User ID=<legacyItalic>MyUserID</legacyItalic>;Password=<legacyItalic>MyPassword</legacyItalic>;"</code>
      <para>The string consists of these keywords:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Keyword</para>
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
                <legacyBold>Provider</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the OLE DB Provider for Internet Publishing.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Data Source</legacyBold> -or- <legacyBold>URL</legacyBold></para>
            </TD>
            <TD>
              <para>Specifies the URL of a file or directory published in a Web Folder.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>User ID</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Password</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user password.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
      </alert>
      <para>If you set the <legacyItalic>ResourceURL</legacyItalic> value from the "URL=" in the connection string to an invalid value, by default the Internet Publishing Provider raises a dialog box to prompt for a valid value. This is undesirable behavior for a component in the middle tier of an application, because it suspends program execution until the dialog box is cleared and the client appears to freeze because it has not received a response from the component.</para>
      <alert class="note">
        <para>If MSDAIPP.DSO is explicitly specified as the value of the provider, either with the <legacyItalic>Provider</legacyItalic> connection string keyword or the <legacyBold>Provider</legacyBold> property, you cannot use "URL=" in the connection string. If you do, an error will occur. Instead, simply specify the URL as shown in the topic <legacyLink xlink:href="4869aafa-7401-4ce1-93ce-45406a60274f">Using ADO with the OLE DB Provider for Internet Publishing</legacyLink>.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2f551969-0fd9-41ee-b81d-100975a4bdc2">Internet Publishing Scenario</link>
<link xlink:href="4869aafa-7401-4ce1-93ce-45406a60274f">Using ADO with the OLE DB Provider for Internet Publishing</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>