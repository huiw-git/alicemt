---
title: ODBC Functions and the Cursor Library
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c609d0fb-787a-4b39-9673-332d411b3d63
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Functions and the Cursor Library
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>When the ODBC cursor library is enabled for a connection, the Driver Manager calls functions in the cursor library instead of in the driver. The cursor library either executes the function or calls it in the specified driver.</para>
  </introduction>
  <section>
    <content>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="2f1d3386-7e59-4d55-a5b4-3440b61343a3">ODBC Functions Executed by the Cursor Library</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="f2941522-75eb-4db9-9468-4800b884dac2">ODBC Functions Not Executed by the Cursor Library</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="f4dd546a-0a6c-4397-8ee7-fafa6b9da543">SQLBindCol (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="04c53e4c-cd1d-40b2-9997-684ebe43499f">SQLBindParameter (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="f6c55be1-f020-4ae2-a423-ef8a0d877e20">SQLBulkOperations (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="5e47e3f7-e1b8-451f-bf75-daa19b7c7271">SQLCloseCursor (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="92340b87-9084-4838-a509-e9ca22d5fd5c">SQLEndTran (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="06fbf06f-127b-475c-b636-7b784918475d">SQLExtendedFetch (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="35a0d493-778b-4fb1-84ee-a13540e2fe0e">SQLFetch (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="4417e57c-31dd-475e-8fe9-eab00a459c80">SQLFetchScroll (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="47bfbd4d-9453-4609-958d-1e05794cb223">SQLFreeStmt (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="ff40c9c0-b847-4426-a099-1bff47e6e872">SQLGetData (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="1a801f22-6fea-48aa-a723-3187a2ad852b">SQLGetDescField and SQLGetDescRec (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="931acd12-4eb6-4a78-9a77-157a18a9a2d0">SQLGetFunctions (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="1b4d220d-2c07-4f56-987e-36813bb1a6ce">SQLGetInfo (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6c34e1ef-4273-4afb-a7d3-f9017ab69c5e">SQLGetStmtAttr (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>  <legacyLink xlink:href="986170b3-fba8-4323-9224-60b381c7effb">SQLGetStmtOption (Cursor Library)</legacyLink></para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="c4459092-1177-4b2a-b7f5-e0083d3bf2b2">SQLNativeSql (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="781cf5a5-325e-4523-8633-d96d9e98277c">SQLRowCount (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6f70bbd0-a057-49ef-8b05-4c80b58fc6e6">SQLSetConnectAttr (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="4ccff067-85cd-4bfa-a6cd-7f28051fb5b9">SQLSetDescField and SQLSetDescRec (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="59cc8eae-09ae-4796-869a-c5806488ae83">SQLSetEnvAttr (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="574399c3-2bb2-4d19-829c-7c77bd82858d">SQLSetPos (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="c5c0ac6d-a6c1-4077-8186-1644df1944f8">SQLSetScrollOptions (Cursor Library)</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="6018a733-c2c8-4047-92ec-92cf85031767">SQLSetStmtAttr (Cursor Library)</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>