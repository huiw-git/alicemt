---
title: "HelloData: A Simple ADO Application"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de4bcd56-dac2-45e6-95ab-9fd7f25878fc
caps.latest.revision: 15
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
# HelloData: A Simple ADO Application
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This simple application steps through each of the four major ADO operations: getting, examining, editing, and updating data. These operations are performed against the Northwind sample database included with Microsoft® SQL Server. To focus on the fundamentals of ADO and to prevent code clutter, error handling in the example is minimal. </para>
    <procedure>
      <title>To run HelloData</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Create a new Standard EXE Visual Basic project that references the ADO library. For more information, see <legacyLink xlink:href="573f8f27-babd-4e2f-bf9a-270ee7024975">Referencing the ADO Libraries</legacyLink>. </para>
          </content>
        </step>
        <step>
          <content>
            <para>Create four command buttons at the top of the form, setting the <legacyBold>Name</legacyBold> and <legacyBold>Caption</legacyBold> properties to the values shown in the table at the end of this topic. </para>
          </content>
        </step>
        <step>
          <content>
            <para>Below the buttons, add a <legacyBold>Microsoft DataGrid Control</legacyBold> (Msdatgrd.ocx). The Msdatgrd.ocx file is included with Visual Basic and is located in your \windows\system32 or \winnt\system32 directory. To add the DataGrid control to your Visual Basic toolbox pane, select <legacyBold>Components...</legacyBold> from the <legacyBold>Project</legacyBold> menu. Then check the box next to "Microsoft DataGrid Control 6.0 (SP3) (OLEDB)" and then click <legacyBold>OK</legacyBold>. To add the control to the project, drag the DataGrid control from the Toolbox to the Visual Basic form.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Create a <legacyBold>TextBox</legacyBold> on the form below the grid and set its properties as shown in the table. The form should resemble the following figure when you are finished. </para>
          </content>
        </step>
        <step>
          <content>
            <para>Finally, copy the code listed in <legacyLink xlink:href="6da136c5-fa93-4fe6-9bf5-90f4d92441fb">HelloData Code</legacyLink>, and paste it into the code editor window of the form. Press <legacyBold>F5</legacyBold> to run the code. </para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <alert class="note">
            <para>In the following example, and throughout the guide, the user id "MyId" with a password of "123aBc" is used to authenticate against the server. You should substitute these values with valid logon credentials for your server. Also, substitute the "MySQLServer" value with the name of your server.</para>
          </alert>
          <para>For a detailed description of the code, see <legacyLink xlink:href="a2831d77-7040-4b73-bbae-fe0bf78107ed">Comments on HelloData</legacyLink>.</para>
        </content>
      </conclusion>
    </procedure>
    <mediaLink>
      <image xlink:href="7053f5d1-7f7b-495f-9dbc-591e9bbf15a8" />
    </mediaLink>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Control Type</para>
          </TD>
          <TD>
            <para>Property</para>
          </TD>
          <TD>
            <para>Value</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Form</para>
          </TD>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>Form1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Height</para>
          </TD>
          <TD>
            <para>6500</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Width</para>
          </TD>
          <TD>
            <para>6500</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MS DataGrid</para>
          </TD>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>grdDisplay1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TextBox</para>
          </TD>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>txtDisplay1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Multiline</para>
          </TD>
          <TD>
            <para>true</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Command Button</para>
          </TD>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>cmdGetData</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Caption</para>
          </TD>
          <TD>
            <para>Get Data</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Command Button</para>
          </TD>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>cmdExamineData</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Caption</para>
          </TD>
          <TD>
            <para>Examine Data</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Command Button</para>
          </TD>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>cmdEditData</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Caption</para>
          </TD>
          <TD>
            <para>Edit Data</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Command Button</para>
          </TD>
          <TD>
            <para>Name</para>
          </TD>
          <TD>
            <para>cmdUpdateData</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Caption</para>
          </TD>
          <TD>
            <para>Update Data</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>