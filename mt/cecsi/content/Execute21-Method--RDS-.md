---
title: "Execute21 Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9f131c8d-1497-416d-8209-abb481c38f7b
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
# Execute21 Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Executes the request and creates an ADO recordset for use in ADO 2.1.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>object</parameterReference>.<legacyBold>Execute21(</legacyBold><parameterReference>ConnectionString As String, HandlerString As String, QueryString As String, lMarshalOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ConnectionString</legacyItalic> </definedTerm>
        <definition>
          <para>A string used to connect to the OLE DB provider where the request will be sent for execution. If a handler is specified by using <legacyItalic>HandlerString</legacyItalic>, it can edit or replace the connection string. </para>
        </definition>
        <definedTerm> <legacyItalic>HandlerString</legacyItalic> </definedTerm>
        <definition>
          <para>The string identifies the handler to be used with this execution. The string contains two parts. The first part contains the name (ProgID) of the handler to be used. The second part of the string contains arguments to be passed to the handler. How the arguments string is interpreted is handler specific. The two parts are separated by the first instance of a comma in the string (although the arguments string can contain additional commas). The arguments are optional.</para>
        </definition>
        <definedTerm> <legacyItalic>QueryString</legacyItalic> </definedTerm>
        <definition>
          <para>A command in the command language supported by the OLE DB provider identified in the connection string. For SQL-based providers, it might contain a <token>tsql</token> command statement, but for non-SQL providers (for example, MSDataShape) this may not be a <token>tsql</token> query statement. </para>
          <para>Also, if a handler is being used (and it is highly recommended that a handler be used), the handler can alter or replace the value specified here. For example, the handler typically replaces <legacyItalic>QueryString</legacyItalic> with a query string from its .ini file. By default, the Msdfmap.ini file is used.  </para>
        </definition>
        <definedTerm> <legacyItalic>lMarshalOptions</legacyItalic> </definedTerm>
        <definition>
          <para>Used to set the marshaling options on the rowset/recordset being returned.</para>
        </definition>
        <definedTerm> <legacyItalic>TableID</legacyItalic> </definedTerm>
        <definition>
          <para>A variant of type either VT_EMPTY or VT_BSTR. If this value is of type VT_EMPTY, it is ignored. If it is of type VT_BSTR, the recordset is created by using <legacyBold>adCmdTableDirect</legacyBold> using the value specified here and the <legacyItalic>QueryString</legacyItalic> parameter is ignored.</para>
        </definition>
        <definedTerm> <legacyItalic>lExecuteOptions</legacyItalic> </definedTerm>
        <definition>
          <para>A bitmask of execution options:</para>
          <para>1=<legacyItalic>ReadOnly</legacyItalic>     The recordset will be opened by using <legacyBold>adLockReadOnly</legacyBold>.   </para>
          <para>2=<legacyItalic>NoBatch</legacyItalic>     The recordset will be opened by using <legacyBold>adLockOptimistic</legacyBold>.   </para>
          <para>4=<legacyItalic>AllParamInfoSupplied</legacyItalic>     The caller guarantees that parameter information for all parameters is supplied in <legacyItalic>pParameters</legacyItalic>.   </para>
          <para>8=<legacyItalic>GetInfo</legacyItalic>     Parameter information for the query will be obtained from the OLE DB provider and returned in the <legacyItalic>pParameters</legacyItalic> parameter. The query is not executed and no recordset is returned.   </para>
          <para>16=GetHiddenColumns     The recordset will be opened by using <legacyBold>adLockBatchOptimistic</legacyBold> and any hidden columns will be included in the recordset.   </para>
          <para>Although <legacyItalic>ReadOnly</legacyItalic>, <legacyItalic>NoBatch</legacyItalic> and <legacyItalic>GetHiddenColumns</legacyItalic> are mutually exclusive options, it is not an error to set more than one of them. If multiple options are set, <legacyItalic>GetHiddenColumns</legacyItalic> takes precedence over all other options, followed by <legacyItalic>ReadOnly</legacyItalic>. If no options are specified, by default, the recordset is opened by using <legacyBold>adLockBatchOptimistic</legacyBold> but hidden columns are not included in the recordset. </para>
        </definition>
        <definedTerm> <legacyItalic>pParameters</legacyItalic> </definedTerm>
        <definition>
          <para>A variant that contains a safe array of parameter definitions. If the <legacyItalic>GetInfo</legacyItalic> option was specified in <legacyItalic>lExecuteOptions</legacyItalic>, this parameter is used to return the parameter definitions obtained from the OLE DB provider. Otherwise, this parameter may be empty.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyItalic>HandlerString</legacyItalic> parameter may be null. What occurs in this case depends on how the RDS server is configured. A handler string of "MSDFMAP.handler" indicates that the Microsoft supplied handler (Msdfmap.dll) should be used. A handler string of "MASDFMAP.handler,sample.ini" indicates that the Msdfmap.dll handler should be used and that the argument "sample.ini" should be passed to the handler. MSDFMAP.dll will interpret the argument as a direction to use the sample.ini to check the connection and query strings.</para>
      <alert class="note">
        <para>The <legacyBold>Execute21</legacyBold> method is a version of the <legacyLink xlink:href="2d9c30e9-ab5b-4920-91b8-48454c2fb5d8">Execute method (RDS)</legacyLink>. Where you need to use the <legacyBold>Execute</legacyBold> method to communicate with ADO 2.1, the <legacyBold>Execute21</legacyBold> method can be called instead. The capabilities of the <legacyBold>Execute</legacyBold> method in ADO 2.5 and later are a superset of the capabilities provided for the same method in ADO 2.1.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>