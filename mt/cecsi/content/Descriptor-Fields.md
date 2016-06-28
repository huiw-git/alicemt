---
title: Descriptor Fields
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f38623c8-fdd4-4601-b1f0-97c593d31177
translation.priority.ht: 
  - en-gb
---
# Descriptor Fields
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Descriptors contain <legacyItalic>header</legacyItalic> and <legacyItalic>record</legacyItalic> fields that completely describe columns or parameters. </para>
    <para>A descriptor contains a single copy of the following header fields. Changing a header field affects all columns or parameters. </para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>SQL_DESC_ALLOC_TYPE</para>
          </TD>
          <TD>
            <para>SQL_DESC_BIND_TYPE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_ARRAY_SIZE</para>
          </TD>
          <TD>
            <para>SQL_DESC_COUNT</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_ARRAY_STATUS_PTR</para>
          </TD>
          <TD>
            <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_BIND_OFFSET_PTR</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>A descriptor contains zero or more descriptor records. Each record describes a column or parameter, depending on the type of descriptor. When a new column or parameter is bound, a new record is added to the descriptor. When a column or parameter is unbound, a record is removed from the descriptor. Each record contains a single copy of the following fields:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>SQL_DESC_AUTO_UNIQUE_VALUE</para>
          </TD>
          <TD>
            <para>SQL_DESC_LOCAL_TYPE_NAME</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_BASE_COLUMN_NAME</para>
          </TD>
          <TD>
            <para>SQL_DESC_NAME</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_BASE_TABLE_NAME</para>
          </TD>
          <TD>
            <para>SQL_DESC_NULLABLE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_CASE_SENSITIVE</para>
          </TD>
          <TD>
            <para>SQL_DESC_OCTET_LENGTH</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_CATALOG_NAME</para>
          </TD>
          <TD>
            <para>SQL_DESC_OCTET_LENGTH_PTR</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_CONCISE_TYPE</para>
          </TD>
          <TD>
            <para>SQL_DESC_PARAMETER_TYPE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_DATA_PTR</para>
          </TD>
          <TD>
            <para>SQL_DESC_PRECISION</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_DATETIME_INTERVAL_CODE</para>
          </TD>
          <TD>
            <para>SQL_DESC_SCALE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_DATETIME_INTERVAL_PRECISION</para>
          </TD>
          <TD>
            <para>SQL_DESC_SCHEMA_NAME</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_DISPLAY_SIZE</para>
          </TD>
          <TD>
            <para>SQL_DESC_SEARCHABLE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_FIXED_PREC_SCALE</para>
          </TD>
          <TD>
            <para>SQL_DESC_TABLE_NAME</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_INDICATOR_PTR</para>
          </TD>
          <TD>
            <para>SQL_DESC_TYPE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_LABEL</para>
          </TD>
          <TD>
            <para>SQL_DESC_TYPE_NAME</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_LENGTH</para>
          </TD>
          <TD>
            <para>SQL_DESC_UNNAMED</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_LITERAL_PREFIX</para>
          </TD>
          <TD>
            <para>SQL_DESC_UNSIGNED</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_LITERAL_SUFFIX</para>
          </TD>
          <TD>
            <para>SQL_DESC_UPDATABLE</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Many statement attributes correspond to the header field of a descriptor. Setting these attributes through a call to <legacyBold>SQLSetStmtAttr</legacyBold> and setting the corresponding descriptor header field by calling <legacyBold>SQLSetDescField</legacyBold> have the same effect. The same is true for <legacyBold>SQLGetStmtAttr</legacyBold> and <legacyBold>SQLGetDescField</legacyBold>, both of which retrieve the same information. Calling the statement functions instead of the descriptor functions has the advantage that a descriptor handle does not have to be retrieved.</para>
    <para>The following header fields can be set by setting statement attributes:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>SQL_DESC_ARRAY_SIZE</para>
          </TD>
          <TD>
            <para>SQL_DESC_BIND_TYPE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_ARRAY_STATUS_PTR</para>
          </TD>
          <TD>
            <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_DESC_BIND_OFFSET_PTR</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="46eec3cc-0ecc-4980-9020-fb74a9af5730">Record Count</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="55d09344-6682-40f6-b634-036b134ff650">Bound Descriptor Records</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="5abeb9cc-4070-4f43-a80d-ad6a2004e5f3">Deferred Fields</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="deb80efa-ad1f-4ea5-b334-9817cd279e5c">Consistency Check</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>