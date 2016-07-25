---
title: "RDS Tutorial"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e3305a0-7bc7-40d1-9122-235c15d23ab2
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
# RDS Tutorial
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This tutorial illustrates using the RDS programming model to query and update a data source. First, it describes the steps necessary to accomplish this task. Then the tutorial is repeated in Microsoft® Visual Basic Scripting Edition and Microsoft® Visual J++®, featuring ADO for Windows Foundation Classes (ADO/WFC).</para>
    <para>This tutorial is coded in different languages for two reasons:  </para>
    <list class="bullet">
      <listItem>
        <para>The documentation for RDS assumes the reader codes in Visual Basic. This makes the documentation convenient for Visual Basic programmers, but less useful for programmers who use other languages.</para>
      </listItem>
      <listItem>
        <para>If you are uncertain about a particular RDS feature and you know a little of another language, you might be able to resolve your question by looking for the same feature expressed in another language.</para>
      </listItem>
    </list>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>How the Tutorial is Presented</title>
    <content>
      <para>This tutorial is based on the RDS programming model. It discusses each step of the programming model individually. In addition, it illustrates each step with a fragment of Visual Basic code.</para>
      <para>The code example is repeated in other languages with minimal discussion. Each step in a given programming language tutorial is marked with the corresponding step in the programming model and descriptive tutorial. Use the number of the step to refer to the discussion in the descriptive tutorial.</para>
      <para>The RDS programming model is stated in the following section. Use it as a roadmap as you proceed through the tutorial.</para>
    </content>
  </section>
  <section>
    <title>RDS Programming Model with Objects</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>Specify the program to be invoked on the server, and obtain a way (proxy) to refer to it from the client.</para>
        </listItem>
        <listItem>
          <para>Invoke the server program. Pass parameters to the server program that identifies the data source and the command to issue.</para>
        </listItem>
        <listItem>
          <para>The server program obtains a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object from the data source, typically by using ADO. Optionally, the <legacyBold>Recordset</legacyBold> object is processed on the server.</para>
        </listItem>
        <listItem>
          <para>The server program returns the final <legacyBold>Recordset</legacyBold> object to the client application.</para>
        </listItem>
        <listItem>
          <para>On the client, the <legacyBold>Recordset</legacyBold> object is optionally put into a form that can be easily used by visual controls.</para>
        </listItem>
        <listItem>
          <para>Changes to the <legacyBold>Recordset</legacyBold> object are sent back to the server and used to update the data source.</para>
        </listItem>
      </list>
      <para>This tutorial contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="d8bb35b1-c02a-4231-8d55-016e56e53b95">Step 1: Specify a Server Program (RDS Tutorial)</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="5e74c2da-65ee-4de4-8b41-6eac45c3632e">Step 2: Invoke the Server Program (RDS Tutorial)</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="9c6779c9-1208-4696-ac51-c39f3a6d9240">Step 3: Server Obtains a Recordset (RDS Tutorial)</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="3d1855c4-419c-4810-b5ea-6c874b5e2905">Step 4: Server Returns the Recordset (RDS Tutorial)</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="ed5c4a24-9804-4c85-817e-317652acb9b4">Step 5: DataControl is Made Usable (RDS Tutorial)</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="b1e927d6-7d50-4978-9eef-045043cdce7a">Step 6: Changes are Sent to the Server (RDS Tutorial)</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="e2a48c4d-88b1-43ff-a202-9cdec54997d2">RDS Tutorial (VBScript)</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="d0d735e0-669a-41e7-ada2-8dd80924e349">RDS Tutorial (Visual J++)</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <?Comment jrs: Are these redundant? 2006-02-10T12:50:00Z  Id='1?>
  <relatedTopics>
<link xlink:href="d8bb35b1-c02a-4231-8d55-016e56e53b95">Step 1: Specify a Server Program (RDS Tutorial)</link>
<link xlink:href="e2a48c4d-88b1-43ff-a202-9cdec54997d2">RDS Tutorial (VBScript)</link>
<link xlink:href="d0d735e0-669a-41e7-ada2-8dd80924e349">RDS Tutorial (Visual J++)</link>
</relatedTopics>
  <?CommentEnd Id='1'
    ?>
</developerConceptualDocument>