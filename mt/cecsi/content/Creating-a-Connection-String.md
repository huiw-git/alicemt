---
title: "Creating a Connection String"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
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
# Creating a Connection String
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A connection string consists of a list of argument/value pairs (that is, parameters), separated by semi-colons. For example: </para>
    <code>"arg1=val1; arg2=val2; ... argN=valN;"</code>
    <para>All the parameters must be recognized by either ADO or the specified provider. </para>
    <para>ADO recognizes the following five arguments in a connection string. </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Argument</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyItalic>Provider</legacyItalic>             </para>
          </TD>
          <TD>
            <para>Specifies the name of a provider to use for the connection.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>File Name</legacyItalic>             </para>
          </TD>
          <TD>
            <para>Specifies the name of a provider-specific file (for example, a persisted data source object) containing preset connection information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>URL</legacyItalic>             </para>
          </TD>
          <TD>
            <para>Specifies the connection string as an absolute URL identifying a resource, such as a file or directory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>Remote Provider</legacyItalic>             </para>
          </TD>
          <TD>
            <para>Specifies the name of a provider to use when opening a client-side connection. (Remote Data Service only.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>Remote Server</legacyItalic>             </para>
          </TD>
          <TD>
            <para>Specifies the path name of the server to use when opening a client-side connection. (Remote Data Service only.)</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Other arguments are passed to the provider named in the <legacyItalic>Provider</legacyItalic> argument, without any processing by ADO.</para>
    <para>The HelloData application in <legacyLink xlink:href="de4bcd56-dac2-45e6-95ab-9fd7f25878fc">HelloData: A Simple ADO Application</legacyLink> used the following connection string:</para>
    <code>m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" &amp; _
             "Initial Catalog=Northwind;Integrated Security='SSPI';"</code>
    <para>In this connection string, ADO recognizes only the <codeInline>"Provider=SQLOLEDB"</codeInline> parameter, which specifies the Microsoft OLE DB Provider for SQL Server as the ADO data source. The rest of the argument/value pairs, <codeInline>"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"</codeInline>, are passed verbatim to this provider. The type and validity of such parameters are provider-specific. For information about valid parameters that can be passed in the connection string, consult the individual provider's documentation. </para>
    <para>According to the OLE DB Provider for SQL Server documentation, you can substitute "Server" for the <legacyItalic>Data Source</legacyItalic> parameter and "Database" for the <legacyItalic>Initial Catalog</legacyItalic> parameter. Thus, the following connection string would produce results identical to the one above:</para>
    <code>m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" &amp; _
             "Database=Northwind;Integrated Security='SSPI';"</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>