---
title: SQLGetStmtAttr (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c34e1ef-4273-4afb-a7d3-f9017ab69c5e
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetStmtAttr (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLGetStmtAttr</legacyBold> function in the cursor library. For general information about <legacyBold>SQLGetStmtAttr</legacyBold>, see <legacyLink xlink:href="e321d460-e997-4527-aee6-207cf5a498e9">SQLGetStmtAttr Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library supports the following statement attributes with <legacyBold>SQLGetStmtAttr</legacyBold>:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SQL_ATTR_CONCURRENCY</para>
            </TD>
            <TD>
              <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_CURSOR_TYPE</para>
            </TD>
            <TD>
              <para>SQL_ATTR_ROW_BIND_TYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_FETCH_BOOKMARK_PTR</para>
            </TD>
            <TD>
              <para>SQL_ATTR_ROW_NUMBER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
            </TD>
            <TD>
              <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ATTR_PARAM_BIND_TYPE</para>
            </TD>
            <TD>
              <para>SQL_ATTR_SIMULATE_CURSOR</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>