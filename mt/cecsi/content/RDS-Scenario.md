---
title: "RDS Scenario"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
caps.latest.revision: 14
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
# RDS Scenario
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The Address Book application is a scenario that shows you how to use Remote Data Service (RDS) to build a simple, data-aware Web application — an online corporate address book. This scenario is useful for Microsoft Visual Basic Scripting Edition (VBScript) and COM programmers who want to learn how to use data-aware ActiveX Controls with RDS, and for more experienced software developers who want to build data-centric Web applications.</para>
    <para>This scenario assumes that you know how to use basic HTML layout tags, use DHTML data binding techniques, and program with ActiveX Controls.</para>
    <para>If you have installed the SDK, the complete source code for the Address Book sample application can be found in the SDK directory at samples\dataaccess\rds\AddressBook\AddressBook.asp. To view the Address Book scenario, in Internet Explorer 4.0 or later, type <legacyBold>http://</legacyBold><legacyBold><legacyItalic>webserver</legacyItalic></legacyBold><legacyBold>/RDS/AddressBook/AddressBook.asp</legacyBold> where <legacyItalic>webserver</legacyItalic> is the name given to your Windows NT 4.0 or Windows 2000 Web server computer that is running Internet Information Services (IIS) and ASP.</para>
  </introduction>
  <section>
    <title>Introduction to Address Book</title>
    <content>
      <para>The Address Book sample application provides a simple online address book that you can use to publish a searchable directory over an intranet. The address book is designed so that a user can enter a search string in one or more fields to request information about employees. To show you the basic features of Remote Data Service, the sample application is intentionally kept small, with a minimum number of objects and search fields.</para>
      <para>The application interface consists of the following parts:  </para>
      <list class="bullet">
        <listItem>
          <para>A non-visual <legacyBold>RDS.DataControl</legacyBold> data-binding object that is used by the client to connect to the database.</para>
        </listItem>
        <listItem>
          <para>HTML text boxes that act as input fields for employee attribute search criteria.</para>
        </listItem>
        <listItem>
          <para>HTML command buttons to build queries, clear search fields, update the database with employee information, cancel pending changes, and navigate the rows of data displayed in the grid.</para>
        </listItem>
        <listItem>
          <para>DHTML data binding to display data returned from queries against a back-end database (through the <legacyBold>RDS.DataControl</legacyBold> data-binding object) in a table.</para>
        </listItem>
        <listItem>
          <para>VBScript routines that connect each of the elements that were previously mentioned and allow them to interact. VBScript code is also used to initialize the <legacyBold>RDS.DataControl</legacyBold> object and dynamically create the column headings in the HTML table from the names of the <legacyBold>RDS.DataControl</legacyBold> recordset fields.</para>
        </listItem>
      </list>
      <para>Follow the links from step to step to set up and run the scenario and to learn more about how the scenario works.</para>
      <para>This scenario contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="da385405-1c9a-478b-9bf6-fba70015324c">System Requirements for the Address Book Application</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="409b3f8b-0ced-4867-acbe-b245dcdf6702">Running the Address Book SQL Script</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="3a2644e9-d634-4ae6-a5b7-13fb7b317ec7">Running the Address Book Sample Application</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="080c1925-d453-4b89-92ac-c93591490518">Address Book Data-Binding Object</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="80676831-6488-4dad-a558-c47c52256a22">Address Book Command Buttons</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277">Address Book Navigation Buttons</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="da385405-1c9a-478b-9bf6-fba70015324c">System Requirements for the Address Book Application</link>
<link xlink:href="2fa6237b-44b8-4b6c-9952-5acd80a54e20">ActiveX Data Objects Start Page</link>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
</relatedTopics>
</developerConceptualDocument>