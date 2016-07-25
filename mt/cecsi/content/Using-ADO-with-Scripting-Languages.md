---
title: "Using ADO with Scripting Languages"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
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
# Using ADO with Scripting Languages
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Within a scripting environment, ADO allows you to expose data by way of server-side scripting. In this scenario, ADO, the underlying OLE DB provider that it uses, and any other components needed to reference a given data store are installed on a server running Internet Information Services (IIS). Using Active Server Pages (ASP), ADO is a component referenced in a script that can generate HTML, for example. This HTML content can be passed via HTTP to a client Web browser. By using scripting, the Web page can send actions back to the server-side script, allowing you to update, traverse, or view specific data.</para>
    <para>Before you use an ActiveX object in a Web page, it is important to know whether the object is safe for scripting. When an object is considered safe for scripting, it means that the control cannot take any harmful action on the user's computer and therefore can be executed without requesting the user's approval. The following table lists the ADO objects and indicates whether they are safe for scripting.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Object</para>
          </TD>
          <TD>
            <para>Safe for Scripting?</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>ADO Connection</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADO Command</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADO Parameter</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADO Recordset</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADO Record</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADO Stream</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADO Error</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADOX Catalog</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ADOX CellSet</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>RDS DataControl</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>RDS DataSpace</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>RDS DataFactory</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following table lists the providers included with Windows DAC/MDAC, and indicates whether they are safe for scripting.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Provider</para>
          </TD>
          <TD>
            <para>Safe for Scripting?</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Shape</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Persist</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Remote</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>OLE DB Provider for SQL Server (SQLOLEDB)</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>OLE DB Provider for ODBC (MSDASQL)</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ODBC Data Sources</title>
    <content>
      <para>One notable difference between scripting and non-scripting ADO code is the ODBC Data Source, if used. For non-scripting applications, you can create a User DSN in the ODBC Data Source Administrator. For scripts that are running under IIS, you must create a System DSN; otherwise your scripts will not recognize the data source you created. This applies to any ADO scripting application using the Microsoft OLE DB Provider for ODBC through Microsoft IIS.</para>
    </content>
  </section>
  <section>
    <title>Referencing the ADO Library</title>
    <content>
      <para>Not applicable with scripting languages.</para>
    </content>
  </section>
  <section>
    <title>Handling events</title>
    <content>
      <para>Not applicable with scripting languages.</para>
      <para>The following topics contain more specific information about using ADO with scripting languages:  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="6aaaf6d0-1376-4473-bea6-b81f2645a9ac">VBScript ADO Programming</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="62273658-0fe7-4aac-b4d8-f725e6baf043">JScript ADO Programming</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2fa6237b-44b8-4b6c-9952-5acd80a54e20">ActiveX Data Objects Start Page</link>
<link xlink:href="9dfb6784-037d-4f9d-bb7f-b506b4498573">Using ADO with Microsoft Visual Basic</link>
<link xlink:href="07d25fc0-4958-4e12-b616-36257ead812b">Using ADO with Microsoft Visual C++</link>
<link xlink:href="15542c35-3bf7-4d5f-a3b2-3a5cff286987">Using ADO with Microsoft Visual J++</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>