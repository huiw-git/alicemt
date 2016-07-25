---
title: "ConnectionString Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3be75b75-4d36-4479-ab64-9a456869252a
caps.latest.revision: 17
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
# ConnectionString Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the information used to establish a connection to a data source.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>ConnectionString</legacyBold> property to specify a data source by passing a detailed connection string containing a series of <legacyItalic>argument</legacyItalic> <legacyItalic>= value</legacyItalic> statements separated by semicolons.</para>
      <para>ADO supports five arguments for the <legacyBold>ConnectionString</legacyBold> property; any other arguments pass directly to the provider without any processing by ADO. The arguments ADO supports are as follows.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Argument</para>
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
                <legacyItalic>Provider=</legacyItalic> </para>
            </TD>
            <TD>
              <para>Specifies the name of a provider to use for the connection.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>File Name=</legacyItalic> </para>
            </TD>
            <TD>
              <para>Specifies the name of a provider-specific file (for example, a persisted data source object) containing preset connection information.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Remote Provider=</legacyItalic> </para>
            </TD>
            <TD>
              <para>Specifies the name of a provider to use when opening a client-side connection. (Remote Data Service only.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Remote Server=</legacyItalic> </para>
            </TD>
            <TD>
              <para>Specifies the path name of the server to use when opening a client-side connection. (Remote Data Service only.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>URL=</legacyItalic> </para>
            </TD>
            <TD>
              <para>Specifies the connection string as an absolute URL identifying a resource, such as a file or directory.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>After you set the <legacyBold>ConnectionString</legacyBold> property and open the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object, the provider may alter the contents of the property, for example, by mapping the ADO-defined argument names to their equivalents for the specific provider.</para>
      <para>The <legacyBold>ConnectionString</legacyBold> property automatically inherits the value used for the <legacyItalic>ConnectionString</legacyItalic> argument of the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method, so you can override the current <legacyBold>ConnectionString</legacyBold> property during the <legacyBold>Open</legacyBold> method call.</para>
      <para>Because the <legacyItalic>File Name</legacyItalic> argument causes ADO to load the associated provider, you cannot pass both the <legacyItalic>Provider</legacyItalic> and <legacyItalic>File Name</legacyItalic> arguments.</para>
      <para>The <legacyBold>ConnectionString</legacyBold> property is read/write when the connection is closed and read-only when it is open.</para>
      <para>Duplicates of an argument in the <legacyBold>ConnectionString</legacyBold> property are ignored. The last instance of any argument is used.</para>
      <alert class="note">
        <para> <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Connection</legacyBold> object, the <legacyBold>ConnectionString</legacyBold> property can include only the <legacyItalic>Remote Provider</legacyItalic> and <legacyItalic>Remote Server</legacyItalic> parameters.</para>
      </alert>
      <para>The following table lists the default ADO provider for each Windows operating system:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Default ADO provider</para>
            </TD>
            <TD>
              <para>Windows operating system </para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>MSDASQL</para>
              <para>(To improve the readability of source code, explicitly specify the provider name in the connection string.)</para>
            </TD>
            <TD>
              <para>Windows 2000 (32-bit)</para>
              <para>Windows XP (32-bit)</para>
              <para>Windows 2003 Server (32-bit)</para>
              <para>Windows Vista (32-bit)</para>
              <para>Windows Vista Service Pack 1 or later (32-bit and 64-bit)</para>
              <para>Windows versions after Windows Vista (32-bit and 64-bit)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>No default.</para>
              <para>When an ADO application runs on the following operating systems and does not specify the provider explicitly, ADO returns the following error: "ADODB.Connection: provider is not specified and there is no designated default provider"</para>
            </TD>
            <TD>
              <para>Windows 2000 (64-bit)</para>
              <para>Windows XP (64-bit)</para>
              <para>Windows 2003 Server (64-bit)</para>
              <para>Windows Vista (64-bit)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="4de7336a-b5ea-43f1-b750-5fa302b5b756">Visual Basic Example</link>
<link xlink:href="c6bd2609-4c49-462f-a1aa-7bee0f615adb">Visual C++ Example</link>
<link xlink:href="4c1e61ed-6569-44a9-b0c8-75b820a64cb6">Visual J++ Example</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>