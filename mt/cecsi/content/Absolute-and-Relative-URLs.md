---
title: "Absolute and Relative URLs"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf
caps.latest.revision: 11
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
# Absolute and Relative URLs
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A URL specifies the location of a target stored on a local or networked computer. The target can be a file, directory, HTML page, image, program, and so on<legacyItalic>.</legacyItalic> </para>
    <para>An <legacyItalic>absolute URL</legacyItalic> contains all the information necessary to locate a resource.</para>
    <para>A <legacyItalic>relative URL</legacyItalic> locates a resource using an absolute URL as a starting point. In effect, the "complete URL" of the target is specified by concatenating the absolute and relative URLs. </para>
    <para>An <legacyItalic>absolute URL</legacyItalic> uses the following format: <legacyItalic>scheme://server/path/resource</legacyItalic></para>
    <para>A relative URL typically consists only of the <legacyItalic>path</legacyItalic>, and optionally, the <legacyItalic>resource</legacyItalic>, but no <legacyItalic>scheme</legacyItalic> or <legacyItalic>server</legacyItalic>. The following tables define the individual parts of the complete URL format.</para>
    <definitionTable>
      <definedTerm> <legacyItalic>scheme</legacyItalic> </definedTerm>
      <definition>
        <para>Specifies how the <legacyItalic>resource</legacyItalic> is to be accessed.</para>
      </definition>
      <definedTerm> <legacyItalic>server</legacyItalic> </definedTerm>
      <definition>
        <para>Specifies the name of the computer where the <legacyItalic>resource</legacyItalic> is located.</para>
      </definition>
      <definedTerm> <legacyItalic>path</legacyItalic> </definedTerm>
      <definition>
        <para>Specifies the sequence of directories leading to the target. If <legacyItalic>resource</legacyItalic> is omitted, the target is the last directory in <legacyItalic>path</legacyItalic>.</para>
      </definition>
      <definedTerm> <legacyItalic>resource</legacyItalic> </definedTerm>
      <definition>
        <para>If included, <legacyItalic>resource</legacyItalic> is the target, and is typically the name of a file. It may be a <legacyItalic>simple file,</legacyItalic> containing a single binary stream of bytes, or a <legacyItalic>structured document,</legacyItalic> containing one or more storages and binary streams of bytes.</para>
      </definition>
    </definitionTable>
  </introduction>
  <section>
    <title>URL Scheme Registration</title>
    <content>
      <para>If a provider supports URLs, the provider will register one or more URL schemes. Registration means that any URLs using the scheme will automatically invoke the registered provider. For example, the <legacyItalic>http</legacyItalic> scheme is registered to the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. ADO assumes all URLs prefixed with "http" represent Web folders or files to be used with the Internet Publishing Provider. For information about the schemes registered by your provider, see your provider documentation.</para>
    </content>
  </section>
  <section>
    <title>Defining Context with a URL</title>
    <content>
      <para>One function of an open connection, represented by a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object, is to restrict subsequent operations to the data source represented by that connection. That is, the connection defines the context for subsequent operations.</para>
      <para>With ADO 2.7 or later, an absolute URL can also define a context. For example, when a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object is opened with an absolute URL, a <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object is implicitly created to represent the resource specified by the URL.</para>
      <para>An absolute URL that defines a context can be specified in the <parameterReference>ActiveConnection</parameterReference> parameter of the <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open</legacyLink> method. An absolute URL can also be specified as the value of the "URL<legacyBold>=</legacyBold>" keyword in the <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method <parameterReference>ConnectionString</parameterReference> parameter, and the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method <legacyItalic>ActiveConnection</legacyItalic> parameter.</para>
      <para>Context can also be defined by opening a <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object that represents a directory, because these objects already have an implicitly or explicitly declared <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object that specifies context.</para>
    </content>
  </section>
  <section>
    <title>Scoped Operations</title>
    <content>
      <para>The context also defines scope—that is, the directory and its subdirectories that can participate in subsequent operations. The <unmanagedCodeEntityReference>Record</unmanagedCodeEntityReference> object has several scoped methods that operate on a directory and all its subdirectories. These methods include <legacyLink xlink:href="b9bcf272-3c74-479f-95dd-0229a32e98fc">CopyRecord</legacyLink>, <legacyLink xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord</legacyLink>, and <legacyLink xlink:href="2726498c-dbd8-4266-983b-ae7d62c39142">DeleteRecord</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Relative URLs as Command Text</title>
    <content>
      <para>You can specify a command to be executed on the data source by typing a string in the <legacyItalic>CommandText</legacyItalic> parameter of the <legacyBold>Connection</legacyBold> object's <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink> method, and in the <parameterReference>Source</parameterReference> parameter of the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object's <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method.</para>
      <para>A relative URL can be specified in the <parameterReference>CommandText</parameterReference> or <parameterReference>Source</parameterReference> parameter. The relative URL does not actually represent a command, such as an SQL command; it merely specifies the parameters. The context of the active connection must be an absolute URL, and the <parameterReference>Option</parameterReference> parameter must be set to <legacyBold>adCmdTableDirect</legacyBold>.</para>
      <para>For example, the following code sample shows how to open a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> on the Readme25.txt file of the Winnt/system32 directory:</para>
      <code>recordset.Open "system32/Readme25.txt", "URL=http://YourServer/Winnt/",,,adCmdTableDirect</code>
      <para>The absolute URL in the connection string specifies the server (<codeInline>YourServer</codeInline>) and the path (<codeInline>Winnt</codeInline>). This URL also defines the context.</para>
      <para>The relative URL in the command text uses the absolute URL as a starting point and specifies the remainder of the path (<codeInline>system32</codeInline>) and the file to open (<codeInline>Readme25.txt</codeInline>).</para>
      <para>The options field (<codeInline>adCmdTableDirect</codeInline>) indicates that the command type is a relative URL.</para>
      <para>As another example, the following code will open a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> on the contents of the <codeInline>Winnt</codeInline> directory:</para>
      <code>recordset.Open "", "URL=http://YourServer/Winnt/",,,adCmdTableDirect</code>
    </content>
  </section>
  <section>
    <title>OLE DB Provider-Supplied URL Schemes</title>
    <content>
      <para>The leading part of a fully-qualified URL is the <newTerm>scheme</newTerm> that is used to access the resource identified by the remainder of the URL. Examples are HTTP (Hypertext Transfer Protocol) and FTP (File Transfer Protocol).</para>
      <para>ADO supports OLE DB providers that recognize their own URL schemes. For example, the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink><legacyItalic>,</legacyItalic> which accesses "published" Windows 2000 files, recognizes the existing HTTP scheme.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>