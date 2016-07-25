---
title: "ADO Dynamic Property Index"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80d389dd-46ef-459f-b0d4-6f712fc4f32d
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
# ADO Dynamic Property Index
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data providers, service providers, and service components can add dynamic properties to the <legacyBold>Properties</legacyBold> collections of the unopened <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> and <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects. A given provider may also insert additional properties when these objects are opened. Some of these properties are listed in the <legacyLink xlink:href="d7b06d72-f792-4328-93a2-5006b9e2c581">ADO Dynamic Properties</legacyLink> section. More are listed under the specific providers in the <legacyLink xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</legacyLink> section.</para>
    <para>The following tables are cross-indexes of the ADO and OLE DB names for each standard OLE DB provider dynamic property. Your providers may add more properties than listed here. For the specific information about provider-specific dynamic properties, see your provider documentation.</para>
    <para>The OLE DB Programmer's Reference refers to an ADO property name by the term "Description." For more information about these standard properties, search or browse the index in the <externalLink><linkText>OLE DB documentation</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx</linkUri></externalLink>for the OLE DB property by its name.</para>
  </introduction>
  <section>
    <title>Connection Dynamic Properties</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ADO Property Name</para>
            </TD>
            <TD>
              <para>OLE DB Property Name</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Active Sessions</para>
            </TD>
            <TD>
              <para>DBPROP_ACTIVESESSIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Asynchable Abort</para>
            </TD>
            <TD>
              <para>DBPROP_ASYNCTXNABORT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Asynchable Commit</para>
            </TD>
            <TD>
              <para>DBPROP_ASYNCTNXCOMMIT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Autocommit Isolation Levels</para>
            </TD>
            <TD>
              <para>DBPROP_SESS_AUTOCOMMITISOLEVELS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Catalog Location</para>
            </TD>
            <TD>
              <para>DBPROP_CATALOGLOCATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Catalog Term</para>
            </TD>
            <TD>
              <para>DBPROP_CATALOGTERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Definition</para>
            </TD>
            <TD>
              <para>DBPROP_COLUMNDEFINITION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connect Timeout</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_TIMEOUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Current Catalog</para>
            </TD>
            <TD>
              <para>DBPROP_CURRENTCATALOG</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data Source</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_DATASOURCE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data Source Name</para>
            </TD>
            <TD>
              <para>DBPROP_DATASOURCENAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data Source Object Threading Model</para>
            </TD>
            <TD>
              <para>DBPROP_DSOTHREADMODEL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DBMS Name</para>
            </TD>
            <TD>
              <para>DBPROP_DBMSNAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DBMS Version</para>
            </TD>
            <TD>
              <para>DBPROP_DBMSVER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Extended Properties</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_PROVIDERSTRING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>GROUP BY Support</para>
            </TD>
            <TD>
              <para>DBPROP_GROUPBY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Heterogeneous Table Support</para>
            </TD>
            <TD>
              <para>DBPROP_HETEROGENEOUSTABLES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Identifier Case Sensitivity</para>
            </TD>
            <TD>
              <para>DBPROP_IDENTIFIERCASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Initial Catalog</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_CATALOG</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Isolation Levels</para>
            </TD>
            <TD>
              <para>DBPROP_SUPPORTEDTXNISOLEVELS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Isolation Retention</para>
            </TD>
            <TD>
              <para>DBPROP_SUPPORTEDTXNISORETAIN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Locale Identifier</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_LCID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Location</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_LOCATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Index Size</para>
            </TD>
            <TD>
              <para>DBPROP_MAXINDEXSIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Row Size</para>
            </TD>
            <TD>
              <para>DBPROP_MAXROWSIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Row Size Includes BLOB</para>
            </TD>
            <TD>
              <para>DBPROP_MAXROWSIZEINCLUDESBLOB</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Tables in SELECT</para>
            </TD>
            <TD>
              <para>DBPROP_MAXTABLESINSELECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Mode</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_MODE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multiple Parameter Sets</para>
            </TD>
            <TD>
              <para>DBPROP_MULTIPLEPARAMSETS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multiple Results</para>
            </TD>
            <TD>
              <para>DBPROP_MULTIPLERESULTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multiple Storage Objects</para>
            </TD>
            <TD>
              <para>DBPROP_MULTIPLESTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multi-Table Update</para>
            </TD>
            <TD>
              <para>DBPROP_MULTITABLEUPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NULL Collation Order</para>
            </TD>
            <TD>
              <para>DBPROP_NULLCOLLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NULL Concatenation Behavior</para>
            </TD>
            <TD>
              <para>DBPROP_CONCATNULLBEHAVIOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OLE DB Services</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_OLEDBSERVICES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OLE DB Version</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDEROLEDBVER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OLE Object Support</para>
            </TD>
            <TD>
              <para>DBPROP_OLEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Open Rowset Support</para>
            </TD>
            <TD>
              <para>DBPROP_OPENROWSETSUPPORT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ORDER BY Columns in Select List</para>
            </TD>
            <TD>
              <para>DBPROP_ORDERBYCOLUMNSINSELECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Output Parameter Availability</para>
            </TD>
            <TD>
              <para>DBPROP_OUTPUTPARAMETERAVAILABILITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Pass By Ref Accessors</para>
            </TD>
            <TD>
              <para>DBPROP_BYREFACCESSORS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Password</para>
            </TD>
            <TD>
              <para>DBPROP_AUTH_PASSWORD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Persist Security Info</para>
            </TD>
            <TD>
              <para>DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Persistent ID Type</para>
            </TD>
            <TD>
              <para>DBPROP_PERSISTENTIDTYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Prepare Abort Behavior</para>
            </TD>
            <TD>
              <para>DBPROP_PREPAREABORTBEHAVIOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Prepare Commit Behavior</para>
            </TD>
            <TD>
              <para>DBPROP_PREPARECOMMITBEHAVIOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Procedure Term</para>
            </TD>
            <TD>
              <para>DBPROP_PROCEDURETERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Prompt</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_PROMPT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Provider Friendly Name</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDERFRIENDLYNAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Provider Name</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDERFILENAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Provider Version</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDERVER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Read-Only Data Source</para>
            </TD>
            <TD>
              <para>DBPROP_DATASOURCEREADONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Conversions on Command</para>
            </TD>
            <TD>
              <para>DBPROP_ROWSETCONVERSIONSONCOMMAND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Schema Term</para>
            </TD>
            <TD>
              <para>DBPROP_SCHEMATERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Schema Usage</para>
            </TD>
            <TD>
              <para>DBPROP_SCHEMAUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL Support</para>
            </TD>
            <TD>
              <para>DBPROP_SQLSUPPORT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Structured Storage</para>
            </TD>
            <TD>
              <para>DBPROP_STRUCTUREDSTORAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Subquery Support</para>
            </TD>
            <TD>
              <para>DBPROP_SUBQUERIES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Table Term</para>
            </TD>
            <TD>
              <para>DBPROP_TABLETERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Transaction DDL</para>
            </TD>
            <TD>
              <para>DBPROP_SUPPORTEDTXNDDL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>User ID</para>
            </TD>
            <TD>
              <para>DBPROP_AUTH_USERID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>User Name</para>
            </TD>
            <TD>
              <para>DBPROP_USERNAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Window Handle</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_HWND</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Recordset Dynamic Properties</title>
    <content>
      <para>Note that the <legacyBold>Dynamic Properties</legacyBold> of the <legacyBold>Recordset</legacyBold> object go out of scope (become unavailable) when the <legacyBold>Recordset</legacyBold> is closed.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ADO Property Name</para>
            </TD>
            <TD>
              <para>OLE DB Property Name</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>IAccessor</para>
            </TD>
            <TD>
              <para>DBPROP_IACCESSOR </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IChapteredRowset</para>
            </TD>
            <TD>
              <para>               </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IColumnsInfo</para>
            </TD>
            <TD>
              <para>DBPROP_ICOLUMNSINFO </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IColumnsRowset</para>
            </TD>
            <TD>
              <para>DBPROP_ICOLUMNSROWSET </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IConnectionPointContainer</para>
            </TD>
            <TD>
              <para>DBPROP_ICONNECTIONPOINTCONTAINER </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IConvertType</para>
            </TD>
            <TD>
              <para>               </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ILockBytes</para>
            </TD>
            <TD>
              <para>DBPROP_ILOCKBYTES </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowset</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSET </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IDBAsynchStatus</para>
            </TD>
            <TD>
              <para>DBPROP_IDBASYNCHSTATUS </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IParentRowset</para>
            </TD>
            <TD>
              <para>               </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetChange</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETCHANGE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetExactScroll</para>
            </TD>
            <TD>
              <para>               </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetFind</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETFIND </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetIdentity</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETIDENTITY </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetInfo</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETINFO </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetLocate</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETLOCATE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetRefresh</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETREFRESH </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetResynch</para>
            </TD>
            <TD>
              <para>               </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetScroll</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETSCROLL </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetUpdate</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETUPDATE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetView</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETVIEW </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetIndex</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETINDEX </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISequentialStream</para>
            </TD>
            <TD>
              <para>DBPROP_ISEQUENTIALSTREAM </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IStorage</para>
            </TD>
            <TD>
              <para>DBPROP_ISTORAGE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IStream</para>
            </TD>
            <TD>
              <para>DBPROP_ISTREAM </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISupportErrorInfo</para>
            </TD>
            <TD>
              <para>DBPROP_ISUPPORTERRORINFO </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Access Order</para>
            </TD>
            <TD>
              <para>DBPROP_ACCESSORDER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Append-Only Rowset</para>
            </TD>
            <TD>
              <para>DBPROP_APPENDONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Asynchronous Rowset Processing</para>
            </TD>
            <TD>
              <para>DBPROP_ROWSET_ASYNCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Auto Recalc</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_AUTORECALC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Background Fetch Size</para>
            </TD>
            <TD>
              <para>DBPROP_ASYNCHFETCHSIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Background Thread Priority</para>
            </TD>
            <TD>
              <para>DBPROP_ASYNCHTHREADPRIORITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Batch Size</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_BATCHSIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Blocking Storage Objects</para>
            </TD>
            <TD>
              <para>DBPROP_BLOCKINGSTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Bookmark Type</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKTYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Bookmarkable</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETLOCATE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Bookmarks Ordered</para>
            </TD>
            <TD>
              <para>DBPROP_ORDEREDBOOKMARKS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cache Child Rows</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_CACHECHILDROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cache Deferred Columns</para>
            </TD>
            <TD>
              <para>DBPROP_CACHEDEFERRED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Change Inserted Rows</para>
            </TD>
            <TD>
              <para>DBPROP_CHANGEINSERTEDROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Privileges</para>
            </TD>
            <TD>
              <para>DBPROP_COLUMNRESTRICT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Set Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYCOLUMNSET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Writable</para>
            </TD>
            <TD>
              <para>DBPROP_MAYWRITECOLUMN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Command Time Out</para>
            </TD>
            <TD>
              <para>DBPROP_COMMANDTIMEOUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cursor Engine Version</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_CEVER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Defer Column</para>
            </TD>
            <TD>
              <para>DBPROP_DEFERRED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delay Storage Object Updates</para>
            </TD>
            <TD>
              <para>DBPROP_DELAYSTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetch Backwards</para>
            </TD>
            <TD>
              <para>DBPROP_CANFETCHBACKWARDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Filter Operations</para>
            </TD>
            <TD>
              <para>DBPROP_FILTERCOMPAREOPS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Find Operations</para>
            </TD>
            <TD>
              <para>DBPROP_FINDCOMPAREOPS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Hidden Columns (Count)</para>
            </TD>
            <TD>
              <para>DBPROP_HIDDENCOLUMNS </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Hold Rows</para>
            </TD>
            <TD>
              <para>DBPROP_CANHOLDROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Immobile Rows</para>
            </TD>
            <TD>
              <para>DBPROP_IMMOBILEROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Initial Fetch Size</para>
            </TD>
            <TD>
              <para>DBPROP_ASYNCHPREFETCHSIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Literal Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_LITERALBOOKMARKS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Literal Row Identity</para>
            </TD>
            <TD>
              <para>DBPROP_LITERALIDENTITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maintain Change Status</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_MAINTAINCHANGESTATUS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Open Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXOPENROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Pending Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXPENDINGROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXROWS </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Memory Usage</para>
            </TD>
            <TD>
              <para>DBPROP_MEMORYUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Notification Granularity</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFICATIONGRANULARITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Notification Phases</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFICATIONPHASES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Objects Transacted</para>
            </TD>
            <TD>
              <para>DBPROP_TRANSACTEDOBJECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Others' Changes Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OTHERUPDATEDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Others' Inserts Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OTHERINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Own Changes Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OWNUPDATEDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Own Inserts Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OWNINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preserve on Abort</para>
            </TD>
            <TD>
              <para>DBPROP_ABORTPRESERVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preserve on Commit</para>
            </TD>
            <TD>
              <para>DBPROP_COMMITPRESERVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Private1</para>
            </TD>
            <TD>
              <para>               </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Quick Restart</para>
            </TD>
            <TD>
              <para>DBPROP_QUICKRESTART</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reentrant Events</para>
            </TD>
            <TD>
              <para>DBPROP_REENTRANTEVENTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Remove Deleted Rows</para>
            </TD>
            <TD>
              <para>DBPROP_REMOVEDELETED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Report Multiple Changes</para>
            </TD>
            <TD>
              <para>DBPROP_REPORTMULTIPLECHANGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reshape Name</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_RESHAPENAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Resync Command</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_CUSTOMRESYNCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Return Pending Inserts</para>
            </TD>
            <TD>
              <para>DBPROP_RETURNPENDINGINSERTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Delete Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row First Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWFIRSTCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Insert Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Privileges</para>
            </TD>
            <TD>
              <para>DBPROP_ROWRESTRICT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Resynchronization Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWRESYNCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Threading Model</para>
            </TD>
            <TD>
              <para>DBPROP_ROWTHREADMODEL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDOCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Delete Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDODELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Insert Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDOINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Update Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Fetch Position Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Release Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWSETRELEASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Scroll Backwards</para>
            </TD>
            <TD>
              <para>DBPROP_CANSCROLLBACKWARDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Server Cursor</para>
            </TD>
            <TD>
              <para>DBPROP_SERVERCURSOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Skip Deleted Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKSKIPPED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Strong Row Identity</para>
            </TD>
            <TD>
              <para>DBPROP_STRONGIDENTITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Unique Catalog</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_UNIQUECATALOG</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Unique Rows</para>
            </TD>
            <TD>
              <para>DBPROP_UNIQUEROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Unique Schema</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_UNIQUESCHEMA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Unique Table</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_UNIQUETABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Updatability</para>
            </TD>
            <TD>
              <para>DBPROP_UPDATABILITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Update Criteria</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_UPDATECRITERIA</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Update Resync</para>
            </TD>
            <TD>
              <para>DBPROP_ADC_UPDATERESYNC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Use Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKS</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>