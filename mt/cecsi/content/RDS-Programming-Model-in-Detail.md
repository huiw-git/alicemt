---
title: "RDS Programming Model in Detail"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e57af8d-519b-4467-a0bd-af468534cefd
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
# RDS Programming Model in Detail
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following are key elements of the RDS programming model:  </para>
    <list class="bullet">
      <listItem>
        <para>RDS.DataSpace</para>
      </listItem>
      <listItem>
        <para>RDSServer.DataFactory</para>
      </listItem>
      <listItem>
        <para>RDS.DataControl</para>
      </listItem>
      <listItem>
        <para>Event</para>
      </listItem>
    </list>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>RDS.DataSpace</title>
    <content>
      <para>Your client application must specify the server and the server program to invoke. In return, your application receives a reference to the server program and can treat the reference as if it were the server program itself.</para>
      <para>The RDS object model embodies this functionality with the <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink> object.</para>
      <para>The server program is specified with a program identifier, or <legacyItalic>ProgID</legacyItalic>. The server uses the <legacyItalic>ProgID</legacyItalic> and the server machine's registry to locate information about the actual program to initiate.</para>
      <para>RDS makes a distinction internally depending on whether the server program is on a remote server across the Internet or an intranet; a server on a local area network; or not on a server at all, but instead on a local dynamic-link library (DLL). This distinction determines how information is exchanged between the client and the server, and makes a tangible difference in the type of reference returned to your client application. However, from your point of view, this distinction has no special meaning. All that matters is that you receive a usable program reference.</para>
    </content>
  </section>
  <section>
    <title>RDSServer.DataFactory</title>
    <content>
      <para>RDS provides a default server program that can either perform a SQL query against the data source and return a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object or take a <legacyBold>Recordset</legacyBold> object and update the data source.</para>
      <para>The RDS object model embodies this functionality with the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object.</para>
      <para>In addition, this object has a method for creating an empty <legacyBold>Recordset</legacyBold> object that you can fill programmatically (<legacyLink xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset</legacyLink>), and another method for converting a <legacyBold>Recordset</legacyBold> object into a text string to build a Web page (<legacyLink xlink:href="b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe">ConvertToString</legacyLink>).</para>
      <para>With ADO, you can override some of the standard connection and command behavior of the <legacyBold>RDSServer.DataFactory</legacyBold> with a <legacyBold>DataFactory</legacyBold> handler and a customization file that contains connection, command, and security parameters.</para>
      <para>The server program is sometimes called a <legacyItalic>business object</legacyItalic>. You can write your own custom business object that can perform complicated data access, validity checks, and so on. Even when writing a custom business object, you can create an instance of an <legacyBold>RDSServer.DataFactory</legacyBold> object and use some of its methods to accomplish your own tasks.</para>
    </content>
  </section>
  <section>
    <title>RDS.DataControl</title>
    <content>
      <para>RDS provides a means to combine the functionality of the <legacyBold>RDS.DataSpace</legacyBold> and <legacyBold>RDSServer.DataFactory</legacyBold>, and also enable visual controls to easily use the <legacyBold>Recordset</legacyBold> object returned by a query from a data source. RDS attempts, for the most common case, to do as much as possible to automatically gain access to information on a server and display it in a visual control.</para>
      <para>The RDS object model embodies this functionality with the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
      <para>The <legacyBold>RDS.DataControl</legacyBold> has two aspects. One aspect pertains to the data source. If you set the command and connection information using the <legacyBold>Connect</legacyBold> and <legacyBold>SQL</legacyBold> properties of the <legacyBold>RDS.DataControl</legacyBold>, it will automatically use the <legacyBold>RDS.DataSpace</legacyBold> to create a reference to the default <legacyBold>RDSServer.DataFactory</legacyBold> object. Then the <legacyBold>RDSServer.DataFactory</legacyBold> will use the <legacyBold>Connect</legacyBold> property value to connect to the data source, use the <legacyBold>SQL</legacyBold> property value to obtain a <legacyBold>Recordset</legacyBold> from the data source, and return the <legacyBold>Recordset</legacyBold> object to the <legacyBold>RDS.DataControl</legacyBold>.</para>
      <para>The second aspect pertains to the display of returned <legacyBold>Recordset</legacyBold> information in a visual control. You can associate a visual control with the <legacyBold>RDS.DataControl</legacyBold> (in a process called binding) and gain access to the information in the associated <legacyBold>Recordset</legacyBold> object, displaying query results on a Web page in Microsoft® Internet Explorer. Each <legacyBold>RDS.DataControl</legacyBold> object binds one <legacyBold>Recordset</legacyBold> object, representing the results of a single query, to one or more visual controls (for example, a text box, combo box, grid control, and so forth). There may be more than one <legacyBold>RDS.DataControl</legacyBold> object on each page. Each <legacyBold>RDS.DataControl</legacyBold> object can be connected to a different data source and contain the results of a separate query.</para>
      <para>The <legacyBold>RDS.DataControl</legacyBold> object also has its own methods for navigating, sorting, and filtering the rows of the associated <legacyBold>Recordset</legacyBold> object. These methods are similar, but not the same as the methods on the ADO <legacyBold>Recordset</legacyBold> object.</para>
    </content>
  </section>
  <section>
    <title>Events</title>
    <content>
      <para>RDS supports two of its own events, which are independent of the ADO event model. The <legacyLink xlink:href="bf2ae3ac-bfe4-4709-b50a-ea7c282c3164">onReadyStateChange</legacyLink> event is called whenever the <legacyBold>RDS.DataControl</legacyBold> <legacyLink xlink:href="5be75bc7-1171-4440-a37e-c8cc6b5cd865">ReadyState</legacyLink> property changes, thus notifying you when an asynchronous operation has successfully completed, terminated, or experienced an error. The <legacyLink xlink:href="b01cbc62-fbd7-4068-b16c-8b0f80a05887">onError</legacyLink> event is called whenever an error occurs, even if the error occurs during an asynchronous operation.</para>
      <alert class="note">
        <para>Microsoft Internet Explorer provides two additional events to RDS: <legacyBold>onDataSetChanged</legacyBold>, which indicates that the <legacyBold>Recordset</legacyBold> is functional but still retrieving rows, and <legacyBold>onDataSetComplete</legacyBold>, which indicates that the <legacyBold>Recordset</legacyBold> has finished retrieving rows.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="07ce0ef0-72f1-48f4-823d-1b65d28c0926">RDS Programming Model with Objects</link>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
<link xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace Object (RDS)</link>
<link xlink:href="a7dcad87-aaf0-4b02-9660-472f8469761c">RDS Scenario</link>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
<link xlink:href="b8ac3739-05d3-4818-8201-a763795fb8b4">Using RDS</link>
</relatedTopics>
</developerConceptualDocument>