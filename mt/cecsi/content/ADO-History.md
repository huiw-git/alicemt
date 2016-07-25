---
title: "ADO History"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 667673f2-3151-432b-894a-3fc60b704ea4
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
# ADO History
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This topic lists the new features introduced by each release of ADO, ADO MD, and ADOX.</para>
  </introduction>
  <section>
    <title>ADO 6.0</title>
    <content>
      <para>ADO 6.0 is included in Windows Vista, as a part of the Windows Data Access Components (Windows DAC) 6.0. ADO 6.0 is functionally equivalent to ADO 2.8.</para>
    </content>
  </section>
  <section>
    <title>ADO 2.8</title>
    <content>
      <para>ADO 2.8 was included in Windows XP and Windows Server 2003, as part of the Microsoft Data Access Components (MDAC) 2.8. A redistributable version of MDAC 2.8 is also available; note that this redistributable version should only be installed on Windows 2000. ADO 2.8 addresses several security-related concerns:  </para>
      <definitionTable>
        <definedTerm> <legacyItalic>Hard drive access is not allowed outside a trusted zone.</legacyItalic> </definedTerm>
        <definition>
          <para>In cross-domain scripting involving nontrusted sites, the following operations are disabled: <legacyBold>Stream.SaveToFile</legacyBold>, <legacyBold>Stream.LoadFromFile</legacyBold>, <legacyBold>Recordset.Save</legacyBold>, and <legacyBold>Recordset.Open</legacyBold>, used in conjunction with the <legacyBold>adCmdFile</legacyBold> flag or with the Microsoft OLE DB Persistence Provider (MSPersist).</para>
        </definition>
        <definedTerm>
          <legacyBold>Recordset.Open</legacyBold>
          <legacyItalic>, </legacyItalic>
          <legacyBold>Recordset.Save</legacyBold>
          <legacyItalic>, </legacyItalic>
          <legacyBold>Stream.SaveToFile</legacyBold>
          <legacyItalic>, and </legacyItalic>
          <legacyBold>Stream.LoadFromFile</legacyBold>
          <legacyItalic> operate on physical files only.</legacyItalic> </definedTerm>
        <definition>
          <para>These methods now verify that file handles point to physical files only.</para>
        </definition>
        <definedTerm>
          <legacyBold>Recordset.ActiveCommand</legacyBold>
          <legacyItalic> returns an error when invoked from an HTML/ASP page.</legacyItalic> </definedTerm>
        <definition>
          <para>This prevents the <legacyBold>Command</legacyBold> object from being misused.</para>
        </definition>
        <definedTerm> <legacyItalic>The number of </legacyItalic><legacyBold>Recordsets</legacyBold><legacyItalic> returned by a nested </legacyItalic><legacyBold>Shape</legacyBold><legacyItalic> command has an upper bound.</legacyItalic> </definedTerm>
        <definition>
          <para>A nested shape command now returns a maximum of 512 <legacyBold>Recordsets</legacyBold>. This means that a <legacyBold>Shape</legacyBold> command can no longer be nested at any depth. Instead, the maximum level depth is 512, if each command results in a single (child) <legacyBold>Recordset</legacyBold>. If, at any level, a <legacyBold>Shape</legacyBold> command returns multiple <legacyBold>Recordsets</legacyBold>, the maximum level of depth will be less than 512.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>ADO 2.7</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>64-bit platform support</legacyItalic> </definedTerm>
        <definition>
          <para>ADO 2.7 introduces support for 64-bit processors.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>ADO 2.6</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyBold>CubDef.GetSchemaObject</legacyBold>
          <legacyItalic> Method</legacyItalic> </definedTerm>
        <definition>
          <para>Starting with ADO 2.6, ADO MD objects can be retrieved using unique names, as specified by the <legacyLink xlink:href="5b977956-e252-4861-8425-f1aaf6b80130">UniqueName property (ADO MD)</legacyLink>. The names of parent objects do not need to be known, and parent collections do not need to be populated to retrieve a schema object. See <legacyLink xlink:href="36b754b4-6b17-4dd1-a925-bca46938b7c4">GetSchemaObject method (ADO MD)</legacyLink>.</para>
        </definition>
        <definedTerm> <legacyItalic>Command streams</legacyItalic> </definedTerm>
        <definition>
          <para>The <legacyBold>Command</legacyBold> object supports commands in stream format as an alternative to using the <legacyBold>CommandText</legacyBold> property. The <legacyLink xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream property (ADO)</legacyLink> can be used to specify XML Templates or updategrams as the <legacyBold>Command</legacyBold> input with the Microsoft OLE DB Provider for SQL Server.</para>
        </definition>
        <definedTerm>
          <legacyBold>Dialect</legacyBold>
          <legacyItalic> property</legacyItalic> </definedTerm>
        <definition>
          <para>
            <legacyLink xlink:href="329c3a71-ba88-4009-b04f-2f52195a5957">Dialect</legacyLink> is a new property that defines the syntax and general rules that the provider uses to parse the string or stream.</para>
        </definition>
        <definedTerm>
          <legacyBold>Command.Execute</legacyBold>
          <legacyItalic> method</legacyItalic> </definedTerm>
        <definition>
          <para>The <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute method</legacyLink> of the ADO <legacyBold>Command</legacyBold> object has been enhanced to use streams for input and output.</para>
        </definition>
        <definedTerm> <legacyItalic>Field statusvalues</legacyItalic> </definedTerm>
        <definition>
          <para>If the user encounters a DB_E_ERRORSOCCURRED error when modifying a <legacyBold>Field</legacyBold> of a <legacyBold>Recordset</legacyBold>, ADO will now fill the <legacyBold>Field.Status</legacyBold> property with the appropriate status information so that the user will have more information about what went wrong. See <legacyLink xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">Status Property (ADO Field)</legacyLink>.</para>
        </definition>
        <definedTerm>
          <legacyBold>NamedParameters</legacyBold>
          <legacyItalic> property</legacyItalic> </definedTerm>
        <definition>
          <para>
            <legacyLink xlink:href="42409387-026c-435f-a9b1-bf4167095875">NamedParameters</legacyLink> is a new property of the <legacyBold>Command</legacyBold> object that indicates that the provider should use named parameters.</para>
        </definition>
        <definedTerm> <legacyItalic>Resultsets in streams</legacyItalic> </definedTerm>
        <definition>
          <para>ADO can return resultsets from a data source in a <legacyBold>Stream</legacyBold>, rather than a <legacyBold>Recordset</legacyBold> object. Using the latest version of the Microsoft OLE DB Provider for SQL Server, you can get XML results from the provider by executing a "For XML" query. A <legacyBold>Stream </legacyBold>that receives the resultset can be opened with a "For XML" command as the source. See <legacyLink xlink:href="996c1321-c926-4f57-8297-85c8c20de974">Retrieving Resultsets into Streams</legacyLink>.</para>
        </definition>
        <definedTerm> <legacyItalic>Single row resultset</legacyItalic> </definedTerm>
        <definition>
          <para>The ADO <legacyBold>Record</legacyBold> object can now be opened on a command string or <legacyBold>Command</legacyBold> object that returns one row of data from the provider. This results in improved performance with MDAC 2.6 providers. See <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</legacyLink>.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>ADO 2.5</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyBold>Record</legacyBold> <legacyItalic>object</legacyItalic> </definedTerm>
        <definition>
          <para>ADO 2.5 introduces the <legacyBold>Record</legacyBold> object to represent and manage a row from a <legacyBold>Recordset</legacyBold> or a data provider, or an object encapsulating a semi-structured data, such as a file or directory. </para>
        </definition>
        <definedTerm> <legacyBold>Stream</legacyBold> <legacyItalic>object</legacyItalic> </definedTerm>
        <definition>
          <para>ADO 2.5 also introduces the <legacyBold>Stream</legacyBold> object to represent a stream of binary or text data.</para>
        </definition>
        <definedTerm> <legacyItalic>URL binding</legacyItalic> </definedTerm>
        <definition>
          <para>ADO 2.5 introduces the use of a URL, as an alternative to a connection string and command text, to name data store objects. A URL can be used with the existing <legacyBold>Connection</legacyBold> and <legacyBold>Recordset</legacyBold> objects, as well as with the new <legacyBold>Record</legacyBold> and <legacyBold>Stream</legacyBold> objects.</para>
        </definition>
        <definedTerm> <legacyItalic>Data providers supporting URL binding</legacyItalic> </definedTerm>
        <definition>
          <para>ADO 2.5 supports OLE DB providers that recognize the URL schemes. This includes OLE DB Provider for Internet Publishing, which accesses the Windows 2000 file system and recognizes the existing HTTP scheme.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>