---
title: "Basic RDS Programming Model"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0bdd236b-edff-4aac-94c3-93e1465ca6c5
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
# Basic RDS Programming Model
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>RDS addresses applications that exist in the following environment: A client application specifies a program that will execute on a server and the parameters required to return the desired information. The program invoked on the server gains access to the specified data source, retrieves the information, optionally processes the data, and then returns the resulting information to your client application in a form that it can easily use. RDS provides the means for you to perform the following sequence of actions:  </para>
    <list class="bullet">
      <listItem>
        <para>Specify the program to be invoked on the server, and obtain a way to refer to it from the client. (This reference is sometimes called a <legacyItalic>proxy</legacyItalic>. It represents the remote server program. The client application will "call" the proxy as if it were a local program, but it actually invokes the remote server program.)</para>
      </listItem>
      <listItem>
        <para>Invoke the server program. Pass parameters to the server program that identify the data source and the command to issue. (The server program actually uses ADO to gain access to the data source. ADO makes a connection with one of the given parameters, and then issues the command specified in the other parameter.)</para>
      </listItem>
      <listItem>
        <para>The server program obtains a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object from the data source. Optionally, the <legacyBold>Recordset</legacyBold> object is processed on the server.</para>
      </listItem>
      <listItem>
        <para>The server program returns the final <legacyBold>Recordset</legacyBold> object to the client application.</para>
      </listItem>
      <listItem>
        <para>On the client, the <legacyBold>Recordset</legacyBold> object is put into a form that can be easily used by visual controls.</para>
      </listItem>
      <listItem>
        <para>Any modifications to the <legacyBold>Recordset</legacyBold> object are sent back to the server program, which uses them to update the data source.</para>
      </listItem>
    </list>
    <para>This programming model contains certain convenience features. If you do not need a complex server program to access the data source, and if you provide the required connection and command parameters, RDS will automatically retrieve the specified data with a simple, default server program.</para>
    <para>If you need more complex processing, you can specify your own custom server program. For example, because a custom server program has the full power of ADO at its disposal, it could connect to several different data sources, combine their data in some complex way, and then return a simple, processed result to the client application.</para>
    <para>Finally, if your needs are somewhere in between, ADO now supports customizing the behavior of the default server program.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="3e57af8d-519b-4467-a0bd-af468534cefd">RDS Programming Model in Detail</link>
<link xlink:href="a7dcad87-aaf0-4b02-9660-472f8469761c">RDS Scenario</link>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="b8ac3739-05d3-4818-8201-a763795fb8b4">Using RDS</link>
</relatedTopics>
</developerConceptualDocument>