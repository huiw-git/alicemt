---
title: "Recordset Object (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ede1415f-c3df-4cc5-a05b-2576b2b84b60
caps.latest.revision: 5
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
# Recordset Object (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents the entire set of records from a base table or the results of an executed command. At any time, the <legacyBold>Recordset</legacyBold> object refers to only a single record within the set as the current record.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>You use <legacyBold>Recordset</legacyBold> objects to manipulate data from a provider. When you use ADO, you manipulate data almost entirely using <legacyBold>Recordset</legacyBold> objects. All <legacyBold>Recordset</legacyBold> objects consist of records (rows) and fields (columns). Depending on the functionality supported by the provider, some <legacyBold>Recordset</legacyBold> methods or properties may not be available.</para>
      <para>ADODB.Recordset is the ProgID that should be used to create a <legacyBold>Recordset</legacyBold> object. Existing applications that reference the outdated ADOR.Recordset ProgID will continue to work without recompiling, but new development should reference ADODB.Recordset.</para>
      <para>There are four different cursor types defined in ADO:  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Dynamic cursor</legacyBold>     Allows you to view additions, changes, and deletions by other users; allows all types of movement through the <legacyBold>Recordset</legacyBold> that doesn't rely on bookmarks; and allows bookmarks if the provider supports them.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Keyset cursor</legacyBold>     Behaves like a dynamic cursor, except that it prevents you from seeing records that other users add, and prevents access to records that other users delete. Data changes by other users will still be visible. It always supports bookmarks and therefore allows all types of movement through the <legacyBold>Recordset</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Static cursor</legacyBold>     Provides a static copy of a set of records for you to use to find data or generate reports; always allows bookmarks and therefore allows all types of movement through the <legacyBold>Recordset</legacyBold>. Additions, changes, or deletions by other users will not be visible. This is the only type of cursor allowed when you open a client-side <legacyBold>Recordset</legacyBold> object.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Forward-only cursor</legacyBold>     Allows you to only scroll forward through the <legacyBold>Recordset</legacyBold>. Additions, changes, or deletions by other users will not be visible. This improves performance in situations where you need to make only a single pass through a <legacyBold>Recordset</legacyBold>.</para>
        </listItem>
      </list>
      <para>Set the <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> property prior to opening the <legacyBold>Recordset</legacyBold> to choose the cursor type, or pass a <legacyItalic>CursorType</legacyItalic> argument with the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method. Some providers don't support all cursor types. Check the documentation for the provider. If you don't specify a cursor type, ADO opens a forward-only cursor by default.</para>
      <para>If the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient</legacyBold> to open a <legacyBold>Recordset</legacyBold>, the <legacyBold>UnderlyingValue</legacyBold> property on <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects is not available in the returned <legacyBold>Recordset</legacyBold> object. When used with some providers (such as the Microsoft ODBC Provider for OLE DB in conjunction with Microsoft SQL Server), you can create <legacyBold>Recordset</legacyBold> objects independently of a previously defined <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object by passing a connection string with the <legacyBold>Open</legacyBold> method. ADO still creates a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object, but it doesn't assign that object to an object variable. However, if you are opening multiple <legacyBold>Recordset</legacyBold> objects over the same connection, you should explicitly create and open a <legacyBold>Connection</legacyBold> object; this assigns the <legacyBold>Connection</legacyBold> object to an object variable. If you do not use this object variable when opening your <legacyBold>Recordset</legacyBold> objects, ADO creates a new <legacyBold>Connection</legacyBold> object for each new <legacyBold>Recordset</legacyBold>, even if you pass the same connection string.</para>
      <para>You can create as many <legacyBold>Recordset</legacyBold> objects as needed.</para>
      <para>When you open a <legacyBold>Recordset</legacyBold>, the current record is positioned to the first record (if any) and the <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF</legacyLink> and <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> properties are set to <legacyBold>False</legacyBold>. If there are no records, the <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> property settings are <legacyBold>True</legacyBold>.</para>
      <para>You can use the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>, <legacyBold>MoveLast</legacyBold>, <legacyBold>MoveNext</legacyBold>, and <legacyBold>MovePrevious</legacyBold> methods; the <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink> method; and the <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink>, <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink>, and <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> properties to reposition the current record, assuming the provider supports the relevant functionality. Forward-only <legacyBold>Recordset</legacyBold> objects support only the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink> method. When you use the <legacyBold>Move</legacyBold> methods to visit each record (or enumerate the <legacyBold>Recordset</legacyBold>), you can use the <legacyBold>BOF</legacyBold> and <legacyBold>EOF</legacyBold> properties to determine if you've moved beyond the beginning or end of the <legacyBold>Recordset</legacyBold>.</para>
      <para>Before using any functionality of a <legacyBold>Recordset</legacyBold> object, you must call the <legacyBold>Supports</legacyBold> method on the object to verify that the functionality is supported or available. You must not use the functionality when the <legacyBold>Supports</legacyBold> method returns false. For example, you can use the <legacyBold>MovePrevious</legacyBold> method only if <codeInline>Recordset.Supports(adMovePrevious)</codeInline> returns <languageKeyword>True</languageKeyword>. Otherwise, you will get an error, because the <legacyBold>Recordset</legacyBold> object might have been closed and the functionality rendered unavailable on the instance. If a feature you are interested in is not supported, <legacyBold>Supports</legacyBold> will return false as well. In this case, you should avoid calling the corresponding property or method on the <legacyBold>Recrodset</legacyBold> object.</para>
      <para>
        <legacyBold>Recordset</legacyBold> objects can support two types of updating: immediate and batched. In immediate updating, all changes to data are written immediately to the underlying data source once you call the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method. You can also pass arrays of values as parameters with the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> and <legacyBold>Update</legacyBold> methods and simultaneously update several fields in a record.</para>
      <para>If a provider supports batch updating, you can have the provider cache changes to more than one record and then transmit them in a single call to the database with the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method. This applies to changes made with the <legacyBold>AddNew</legacyBold>, <legacyBold>Update</legacyBold>, and <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink> methods. After you call the <legacyBold>UpdateBatch</legacyBold> method, you can use the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property to check for any data conflicts in order to resolve them.</para>
      <alert class="note">
        <para>To execute a query without using a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object, pass a query string to the <legacyBold>Open</legacyBold> method of a <legacyBold>Recordset</legacyBold> object. However, a <legacyBold>Command</legacyBold> object is required when you want to persist the command text and re-execute it, or use query parameters.</para>
      </alert>
      <para>The <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property governs access permissions.</para>
      <para>The <legacyBold>Fields</legacyBold> collection is the default member of the <legacyBold>Recordset</legacyBold> object. As a result, the following two code statements are equivalent.</para>
      <code>Debug.Print objRs.Fields.Item(0)  ' Both statements print 
Debug.Print objRs(0)              '  the Value of Item(0).</code>
      <para>When a <legacyBold>Recordset</legacyBold> object is passed across processes, only the <legacyBold>rowset</legacyBold> values are marshalled, and the properties of the <legacyBold>Recordset</legacyBold> object are ignored. During unmarshalling, the <legacyBold>rowset</legacyBold> is unpacked into a newly created <legacyBold>Recordset</legacyBold> object, which also sets its properties to the default values.</para>
      <para>The <legacyBold>Recordset</legacyBold> object is safe for scripting.</para>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="4295a6e5-112d-4595-b18a-57728893ac2d">Recordset Object Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>