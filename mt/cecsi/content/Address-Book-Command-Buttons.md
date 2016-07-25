---
title: "Address Book Command Buttons"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
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
# Address Book Command Buttons
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Address Book application includes the following command buttons:  </para>
    <list class="bullet">
      <listItem>
        <para>A <ui>Find</ui> button to submit a query to the database.</para>
      </listItem>
      <listItem>
        <para>A <ui>Clear</ui> button to clear the text boxes before starting a new search.</para>
      </listItem>
      <listItem>
        <para>An <ui>Update Profile</ui> button to save changes to an employee record.</para>
      </listItem>
      <listItem>
        <para>A <ui>Cancel Changes</ui> button to discard changes.</para>
      </listItem>
    </list>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Find Button</title>
    <content>
      <para>Clicking the <ui>Find</ui> button activates the VBScript Find_OnClick Sub procedure, which builds and sends the SQL query. Clicking this button populates the data grid.</para>
    </content>
  </section>
  <section>
    <title>Building the SQL Query</title>
    <content>
      <para>The first part of the Find_OnClick Sub procedure builds the SQL query, one phrase at a time, by appending text strings to a global SQL SELECT statement. It begins by setting the variable <codeInline>myQuery</codeInline> to a SQL SELECT statement that requests all rows of data from the data source table. Next, the Sub procedure scans each of the four input boxes on the page.</para>
      <para>Because the program uses the word <codeInline>like</codeInline> in building the SQL statements, the queries are substring searches rather than exact matches.</para>
      <para>For example, if the <legacyBold>Last Name</legacyBold> box contained the entry "Berge" and the <legacyBold>Title</legacyBold> box contained the entry "Program Manager", the SQL statement (value of <codeInline>myQuery</codeInline>) would read:</para>
      <code>Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'</code>
      <para>If the query was successful, all persons with a last name containing the text "Berge" (such as Berge and Berger) and with a title containing the words "Program Manager" (for example, Program Manager, Advanced Technologies) are displayed in the HTML data grid. </para>
    </content>
  </section>
  <section>
    <title>Preparing and Sending the Query</title>
    <content>
      <para>The last part of the Find_OnClick Sub procedure consists of two statements. The first statement assigns the <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink> property of the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object equal to the dynamically built SQL query. The second statement causes the <legacyBold>RDS.DataControl</legacyBold> object (<codeInline>DC1</codeInline>) to query the database, and then display the new results of the query in the grid.</para>
      <code>Sub Find_OnClick
   '...
   DC1.SQL = myQuery
   DC1.Refresh
End Sub</code>
    </content>
  </section>
  <section>
    <title>Update Profile Button</title>
    <content>
      <para>Clicking the <legacyBold>Update Profile</legacyBold> button activates the VBScript Update_OnClick Sub procedure, which executes the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object's (<codeInline>DC1</codeInline>) <legacyLink xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges</legacyLink> and <legacyLink xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh</legacyLink> methods.</para>
      <code>Sub Update_OnClick
   DC1.SubmitChanges
   DC1.Refresh
End Sub</code>
      <para>When <codeInline>DC1.SubmitChanges</codeInline> executes, the Remote Data Service packages all the update information and sends it to the server via HTTP. The update is all-or-nothing; if a part of the update is unsuccessful, none of the changes is made, and a status message is returned. <codeInline>DC1.Refresh </codeInline>isn't necessary after <legacyBold>SubmitChanges</legacyBold> with Remote Data Service, but it ensures fresh data.</para>
    </content>
  </section>
  <section>
    <title>Cancel Changes Button</title>
    <content>
      <para>Clicking <legacyBold>Cancel Changes</legacyBold> activates the VBScript Cancel_OnClick Sub procedure, which executes the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object's (<codeInline>DC1)</codeInline> <legacyLink xlink:href="76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650">CancelUpdate</legacyLink> method.</para>
      <code>Sub Cancel_OnClick
   DC1.CancelUpdate
End Sub</code>
      <para>When<codeInline> DC1.CancelUpdate</codeInline> executes, it discards any edits that a user has made to an employee record on the data grid since the last query or update. It restores the original values.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277">Address Book Navigation Buttons</link>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
</relatedTopics>
</developerConceptualDocument>