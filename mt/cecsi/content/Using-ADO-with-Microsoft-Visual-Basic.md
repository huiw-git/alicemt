---
title: "Using ADO with Microsoft Visual Basic"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9dfb6784-037d-4f9d-bb7f-b506b4498573
caps.latest.revision: 10
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
# Using ADO with Microsoft Visual Basic
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Setting up an ADO project and writing ADO code is similar whether you use Visual Basic or Visual Basic for Applications. This topic addresses using ADO with both Visual Basic and Visual Basic for Applications and notes any differences.</para>
  </introduction>
  <section>
    <title>Referencing the ADO Library</title>
    <content>
      <para>The ADO library must be referenced by your project.</para>
      <procedure>
        <title>To reference ADO from Microsoft Visual Basic</title>
        <steps class="ordered">
          <step>
            <content>
              <para>In Visual Basic, from the <legacyBold>Project</legacyBold> menu, select <legacyBold>References...</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select <legacyBold>Microsoft ActiveX Data Objects x.x Library</legacyBold> from the list. Verify that at least the following libraries are also selected: </para>
              <list class="bullet">
                <listItem>
                  <para>Visual Basic for Applications</para>
                </listItem>
                <listItem>
                  <para>Visual Basic runtime objects and procedures</para>
                </listItem>
                <listItem>
                  <para>Visual Basic objects and procedures</para>
                </listItem>
                <listItem>
                  <para>OLE Automation</para>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>Click <legacyBold>OK</legacyBold>.</para>
            </content>
          </step>
        </steps>
      </procedure>
      <para>You can use ADO just as easily with Visual Basic for Applications, by using Microsoft Access, for example.</para>
      <procedure>
        <title>To reference ADO from Microsoft Access</title>
        <steps class="ordered">
          <step>
            <content>
              <para>In Microsoft Access, select or create a module from the <legacyBold>Modules</legacyBold> tab in the <legacyBold>Database</legacyBold> window.</para>
            </content>
          </step>
          <step>
            <content>
              <para>On the <legacyBold>Tools</legacyBold> menu, select <legacyBold>References...</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select <legacyBold>Microsoft ActiveX Data Objects x.x Library</legacyBold> from the list. Verify that at least the following libraries are also selected: </para>
              <list class="bullet">
                <listItem>
                  <para>Visual Basic for Applications</para>
                </listItem>
                <listItem>
                  <para>Microsoft Access 8.0 Object Library (or later)</para>
                </listItem>
                <listItem>
                  <para>Microsoft DAO 3.5 Object Library (or later)</para>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>Click <legacyBold>OK</legacyBold>.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <section>
    <title>Creating ADO Objects in Visual Basic</title>
    <content>
      <para>To create an automation variable and an instance of an object for that variable, you can use two methods: <legacyBold>Dim</legacyBold> or <legacyBold>CreateObject</legacyBold>.</para>
    </content>
    <sections>
      <section>
        <title>Dim</title>
        <content>
          <para>You can use the <legacyBold>New</legacyBold> keyword with <legacyBold>Dim</legacyBold> to declare and create instances of ADO objects in one step:</para>
          <code>Dim conn As New ADODB.Connection</code>
          <para>Alternatively, the <legacyBold>Dim </legacyBold>statement declaration and object instantiation can also be two steps:</para>
          <code>Dim conn As ADODB.Connection
Set conn = New ADODB.Connection</code>
          <alert class="note">
            <para>It is not required to explicitly use the <codeInline>ADODB</codeInline> progid with the <legacyBold>Dim</legacyBold> statement, assuming you have correctly referenced the ADO library in your project. However, using it ensures that you will not have naming conflicts with other libraries.</para>
          </alert>
          <alert class="note">
            <para>For example, if you include references to both ADO and DAO in the same project, you should include a qualifier to specify which object model to use when instantiating <legacyBold>Recordset</legacyBold> objects, as in the following code:</para>
          </alert>
          <code>Dim adoRS As ADODB.Recordset
Dim daoRS As DAO.Recordset</code>
        </content>
      </section>
      <section>
        <title>CreateObject</title>
        <content>
          <para>With the <legacyBold>CreateObject</legacyBold> method, the declaration and object instantiation must be two discrete steps:</para>
          <code>Dim conn1
Set conn1 = CreateObject("ADODB.Connection") As Object</code>
          <para>Objects instantiated with <legacyBold>CreateObject</legacyBold> are late-bound, which means that they are not strongly typed and command-line completion is disabled. However, it does allow you to skip referencing the ADO library from your project, and enables you to instantiate specific versions of objects. For example:</para>
          <code>Set conn1 = CreateObject("ADODB.Connection.2.0") As Object</code>
          <para>You could also accomplish this by specifically creating a reference to the ADO version 2.0 type library and creating the object.</para>
          <para>Instantiating objects by using the <legacyBold>CreateObject</legacyBold> method is typically slower than using the <legacyBold>Dim</legacyBold> statement.</para>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Handling Events</title>
    <content>
      <para>In order to handle ADO events in Microsoft Visual Basic, you must declare a module-level variable using the <legacyBold>WithEvents</legacyBold> keyword. The variable can be declared only as part of a class module and must be declared at the module level. For a more thorough discussion of handling ADO events, see <legacyLink xlink:href="e9003457-0762-48b3-942f-0820266b158f">Handling ADO Events</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Visual Basic Examples</title>
    <content>
      <para>Many Visual Basic examples are included with the ADO documentation. For more information, see <legacyLink xlink:href="1152893e-b617-40f1-88b6-81e82e2234f1">ADO Code Examples in Microsoft Visual Basic</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2fa6237b-44b8-4b6c-9952-5acd80a54e20">ActiveX Data Objects Start Page</link>
<link xlink:href="07d25fc0-4958-4e12-b616-36257ead812b">Using ADO with Microsoft Visual C++</link>
<link xlink:href="15542c35-3bf7-4d5f-a3b2-3a5cff286987">Using ADO with Microsoft Visual J++</link>
<link xlink:href="76fc4d00-0c9f-422b-af5c-af6ed8fb29d8">Using ADO with Scripting Languages</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>