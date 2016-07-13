---
title: SQLGetStmtOption (Cursor Library)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 986170b3-fba8-4323-9224-60b381c7effb
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetStmtOption (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLGetStmtOption</legacyBold> function in the cursor library. For general information about <legacyBold>SQLGetStmtOption</legacyBold>, see <legacyLink xlink:href="d69c2668-4260-4722-8c34-1c51caac307f">SQLGetStmtOption Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library supports the following statement options with <legacyBold>SQLGetStmtOption</legacyBold>:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_BIND_TYPE</para>
            </TD>
            <TD>
              <para>SQL_ROW_NUMBER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONCURRENCY</para>
            </TD>
            <TD>
              <para>SQL_ROWSET_SIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_TYPE</para>
            </TD>
            <TD>
              <para>SQL_SIMULATE_CURSOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_GET_BOOKMARK</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>