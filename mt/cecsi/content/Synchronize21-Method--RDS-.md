---
title: "Synchronize21 Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6b35f136-9d9a-4bdd-8144-67decfd3c4e9
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
# Synchronize21 Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Synchronize the given recordset with the database specified by the connection string for use with ADO 2.1.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>object</parameterReference>.<legacyBold>Synchronize21(</legacyBold><parameterReference>ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ConnectionString</legacyItalic> </definedTerm>
        <definition>
          <para>A string used to connect to the OLE DB provider where the request will be sent. If a handler is used, the handler can edit or replace the connection string. </para>
        </definition>
        <definedTerm> <legacyItalic>HandlerString</legacyItalic> </definedTerm>
        <definition>
          <para>The string identifies the handler to be used with this execution. The string contains two parts. The first part contains the name (ProgID) of the handler to be used. The second part of the string contains arguments to be passed to the handler. How the arguments string is interpreted is handler specific. The two parts are separated by the first instance of a comma in the string. The arguments string can contain additional commas. The arguments are optional.</para>
        </definition>
        <definedTerm> <legacyItalic>lSynchronizeOptions</legacyItalic> </definedTerm>
        <definition>
          <para>A bit mask of synchronization options.</para>
          <para>1=<legacyItalic>UpdateTransact</legacyItalic>    Updates to the database are wrapped in a transaction. The transaction is aborted if any of the updates fail.    </para>
          <para>2=<legacyItalic>RefreshWithUpdate</legacyItalic>     Causes row statuses to be returned when neither <legacyItalic>Refresh</legacyItalic> nor <legacyItalic>RefreshConflicts</legacyItalic> is set.   </para>
          <para>4=<legacyItalic>Refresh</legacyItalic>     The recordset is refreshed with current data from the database. Pending updates are not pushed to the database. If this bit is not set, the recordset is not refreshed and any pending updates are pushed to the database.   </para>
          <para>8=<legacyItalic>RefreshConflicts</legacyItalic>     Any rows with pending changes fail to update. The rows which failed to update are refreshed with current data from the database. </para>
        </definition>
        <definedTerm> <legacyItalic>ppRecordset</legacyItalic> </definedTerm>
        <definition>
          <para>A pointer to a pointer to the recordset to be synchronized.</para>
        </definition>
        <definedTerm> <legacyItalic>pStatusArray</legacyItalic> </definedTerm>
        <definition>
          <para>A variant used to return a safe array of row statuses for the rows affected by synchronize. Not set if none of the following synchronization options are set: <legacyItalic>RefreshWithUpdate</legacyItalic>, <legacyItalic>Refresh</legacyItalic> and <legacyItalic>RefreshConflicts</legacyItalic>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyItalic>HandlerString</legacyItalic> parameter can be null. What happens in this case depends on how the RDS server is configured. A handler string of "MSDFMAP.handler" indicates that the Microsoft supplied handler (Msdfmap.dll) should be used. A handler string of "MASDFMAP.handler,sample.ini" indicates that the Msdfmap.dll handler should be used and that the argument "sample.ini" should be passed to the handler. Msdfmap.dll will then interpret the argument as a direction to use the sample.ini to check the connection and query strings.</para>
      <alert class="note">
        <para>The <legacyBold>Synchronize21</legacyBold> method is simply a version of the <legacyLink xlink:href="7af42866-7db2-4174-8251-388a2cf741f2">Synchronize Method (RDS)</legacyLink>. Where you need to use the <legacyBold>Synchronize</legacyBold> method to communicate with ADO 2.1, the <legacyBold>Synchronize21</legacyBold> method can be called instead. The capabilities of the <legacyBold>Synchronize</legacyBold> method in ADO 2.5 and later are a superset of the capabilities provided for the same method in ADO 2.1.</para>
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