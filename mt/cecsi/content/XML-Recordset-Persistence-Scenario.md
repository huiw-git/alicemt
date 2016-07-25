---
title: "XML Recordset Persistence Scenario"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 353d569a-043a-4397-9ee6-564c4af8d5f6
caps.latest.revision: 3
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
# XML Recordset Persistence Scenario
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In this scenario, you will create an Active Server Pages (ASP) application that saves the contents of a Recordset object directly to the ASP Response object.</para>
    <alert class="note">
      <para>This scenario requires that your server have Internet Information Server 5.0 (IIS) or later installed.</para>
    </alert>
    <para>The returned Recordset is displayed in Internet Explorer using a <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>.</para>
    <para>The following steps are necessary to create this scenario: </para>
    <list class="bullet">
      <listItem>
        <para>Set Up the Application </para>
      </listItem>
      <listItem>
        <para>Get the Data </para>
      </listItem>
      <listItem>
        <para>Send the Data </para>
      </listItem>
      <listItem>
        <para>Receive and Display the Data </para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Step 1: Set Up the Application</title>
    <content>
      <para>Create an IIS virtual directory named "XMLPersist" with script permissions. Create two new text files in the folder to which the virtual directory points, one named "XMLResponse.asp," the other named "Default.htm."</para>
    </content>
  </section>
  <section>
    <title>Step 2: Get the Data</title>
    <content>
      <para>In this step, you will write the code to open an ADO Recordset and prepare to send it to the client. Open the file XMLResponse.asp with a text editor, such as Notepad, and insert the following code.</para>
      <code>&lt;%@ language="VBScript" %&gt;

&lt;!-- #include file='adovbs.inc' --&gt;

&lt;%
  Dim strSQL, strCon
  Dim adoRec 
  Dim adoCon 
  Dim xmlDoc 

  ' You will need to change "MySQLServer" below to the name of the SQL 
  ' server machine to which you want to connect.
  strCon = "Provider=sqloledb;Data Source=MySQLServer;Initial Catalog=Pubs;Integrated Security=SSPI;"
  Set adoCon = server.createObject("ADODB.Connection")
  adoCon.Open strCon

  strSQL = "SELECT Title, Price FROM Titles ORDER BY Price"
  Set adoRec = Server.CreateObject("ADODB.Recordset")
  adoRec.Open strSQL, adoCon, adOpenStatic, adLockOptimistic, adCmdText</code>
      <para>Be sure to change the value of the<codeInline> Data Source </codeInline>parameter in<codeInline> strCon </codeInline>to the name of your Microsoft SQL Server computer. </para>
      <para>Keep the file open and go on to the next step.</para>
    </content>
  </section>
  <section>
    <title>Step 3: Send the Data</title>
    <content>
      <para>Now that you have a Recordset, you must send it to the client by saving it as XML to the ASP Response object. Add the following code to the bottom of XMLResponse.asp.</para>
      <code>  Response.ContentType = "text/xml"
  Response.Expires = 0
  Response.Buffer = False


  Response.Write "&lt;?xml version='1.0'?&gt;" &amp; vbNewLine
  adoRec.save Response, adPersistXML
  adoRec.Close
  Set adoRec=Nothing
%&gt;</code>
      <para>Notice that the ASP Response object is specified as the destination for the Recordset <link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link>. The destination of the Save method can be any object that supports the IStream interface, such as an ADO <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object (ADO)</link>, or a file name that includes the complete path to which the Recordset is to be saved.</para>
      <para>Save and close XMLResponse.asp before going to the next step. Also copy the adovbs.inc file from the default ADO library installation folder to the same folder where you saved the XMLResponse.asp file.</para>
    </content>
  </section>
  <section>
    <title>Step 4: Receive and Display the Data</title>
    <content>
      <para>In this step you will create an HTML file with an embedded <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link> object that points at the XMLResponse.asp file to get the Recordset. Open default.htm with a text editor, such as Notepad, and add the following code. Replace "sqlserver" in the URL with the name of your server.</para>
      <code>&lt;HTML&gt;
&lt;HEAD&gt;&lt;TITLE&gt;ADO Recordset Persistence Sample&lt;/TITLE&gt;&lt;/HEAD&gt;
&lt;BODY&gt;

&lt;TABLE DATASRC="#RDC1" border="1"&gt;
  &lt;TR&gt;
&lt;TD&gt;&lt;SPAN DATAFLD="title"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
&lt;TD&gt;&lt;SPAN DATAFLD="price"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
  &lt;/TR&gt;
&lt;/TABLE&gt;
&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="RDC1"&gt;
   &lt;PARAM NAME="URL" VALUE="XMLResponse.asp"&gt;
&lt;/OBJECT&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;</code>
      <para>Close the default.htm file and save it to the same folder where you saved XMLResponse.asp. Using Internet Explorer 4.0 or later, open the URL http://<placeholder>sqlserver</placeholder>/XMLPersist/default.htm and observe the results. The data is displayed in a bound DHTML table. Now open the URL http://<placeholder> sqlserver</placeholder> /XMLPersist/XMLResponse.asp and observe the results. The XML is displayed.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link>
<link xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</link>
</relatedTopics>
</developerConceptualDocument>