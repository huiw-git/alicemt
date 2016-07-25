---
title: "Execute Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
caps.latest.revision: 18
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
# Execute Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Executes the request and creates an ADO recordset for use in ADO 2.5 and later.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>object</parameterReference>.<legacyBold>Execute(</legacyBold><parameterReference>ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation]</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>ConnectionString </parameterReference>
        </definedTerm>
        <definition>
          <para>A string used to connect to the OLE DB provider where the request will be sent for execution. If a handler is specified by using <parameterReference>HandlerString</parameterReference> it can edit or replace the connection string. </para>
        </definition>
        <definedTerm>
          <parameterReference>HandlerString </parameterReference>
        </definedTerm>
        <definition>
          <para>A two-part string that identifies the handler to be used with this execution. The string contains two parts. The first part contains the name (ProgID) of the handler to be used. The second part contains arguments to be passed to the handler. The details of how the arguments string is interpreted are specific to each handler. The two parts are separated by the first instance of a comma in the string. The arguments string can contain additional commas. The arguments are optional.</para>
        </definition>
        <definedTerm>
          <parameterReference>QueryString </parameterReference>
        </definedTerm>
        <definition>
          <para>A command in the command language supported by the OLE DB provider identified in the connection string. For SQL-based providers, <parameterReference>QueryString</parameterReference> might contain a Transact-SQL command statement, but for non-SQL providers (for example, MSDataShape) this may not be a <token>tsql</token> query statement. </para>
          <para>If a handler is being used, the handler can alter or replace the value specified here. For example, the handler typically replaces <parameterReference>QueryString</parameterReference> with a query string from its .ini file. By default, the Msdfmap.ini file is used.  </para>
        </definition>
        <definedTerm>
          <parameterReference>lFetchOptions </parameterReference>
        </definedTerm>
        <definition>
          <para>Indicates the type of asynchronous fetching. </para>
          <para>For more information, see <link xlink:href="7b2e254a-9354-4541-bc98-bb185276388f">FetchOptions Property (RDS)</link>.</para>
        </definition>
        <definedTerm>
          <parameterReference>TableID </parameterReference>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>Variant</languageKeyword> of type either VT_EMPTY or VT_BSTR. If this value is of type VT_EMPTY, it is ignored. If it is of type VT_BSTR, the recordset is created by using <legacyBold>adCmdTableDirect</legacyBold> and the value specified here and the <parameterReference>QueryString</parameterReference> parameter is ignored.</para>
        </definition>
        <definedTerm>
          <parameterReference>lExecuteOptions </parameterReference>
        </definedTerm>
        <definition>
          <para>A bit mask of execution options:</para>
          <para>1=<parameterReference>ReadOnly</parameterReference>   The recordset will be opened by using <legacyBold>adLockReadOnly</legacyBold>.   </para>
          <para>2=<parameterReference>NoBatch</parameterReference>     The recordset will be opened by using <legacyBold>adLockOptimistic</legacyBold>.   </para>
          <para>4=<parameterReference>AllParamInfoSupplied</parameterReference>     The caller guarantees that parameter information for all parameters is supplied in <parameterReference>pParameters</parameterReference>.   </para>
          <para>8=<parameterReference>GetInfo</parameterReference>     Parameter information for the query will be obtained from the OLE DB provider and returned in the <parameterReference>pParameters</parameterReference> parameter. The query is not executed and no recordset is returned.   </para>
          <para>16=<parameterReference>GetHiddenColumns</parameterReference>     The recordset will be opened by using <legacyBold>adLockBatchOptimistic</legacyBold> and any hidden columns will be included in the recordset.   </para>
          <para>
            <parameterReference>ReadOnly</parameterReference>, <parameterReference>NoBatch</parameterReference> and <parameterReference>GetHiddenColumns</parameterReference> are mutually exclusive options; however, it does not generate an error to set more than one of them. If multiple options are set, <parameterReference>GetHiddenColumns</parameterReference> takes precedence over all others, followed by <parameterReference>ReadOnly</parameterReference>. If no options are specified, by default, the recordset is opened by using <legacyBold>adLockBatchOptimistic</legacyBold> and hidden columns are not included in the recordset. </para>
        </definition>
        <definedTerm> <parameterReference>pParameters </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>Variant</languageKeyword> that contains a safe array of parameter definitions. If the <parameterReference>GetInfo</parameterReference> option was specified in <parameterReference>lExecuteOptions</parameterReference>, this parameter is used to return the parameter definitions obtained from the OLE DB provider. Otherwise, this parameter can be empty.</para>
        </definition>
        <definedTerm> <parameterReference>lcid </parameterReference></definedTerm>
        <definition>
          <para>The LCID used to build any errors that are returned in <parameterReference>pInformation</parameterReference>.</para>
        </definition>
        <definedTerm> <parameterReference>pInformation </parameterReference></definedTerm>
        <definition>
          <para>A pointer to information error returned by Execute. If NULL, no error information is returned.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <parameterReference>HandlerString</parameterReference> parameter may be null. What happens in this case depends on how the RDS server is configured. A handler string of "MSDFMAP.handler" indicates that the Microsoft supplied handler (Msdfmap.dll) should be used. A handler string of "MASDFMAP.handler,sample.ini" indicates that the Msdfmap.dll handler should be used and that the argument "sample.ini" should be passed to the handler. MSDFMAP.dll will interpret the argument as a direction to use the sample.ini to check the connection and query strings.</para>
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