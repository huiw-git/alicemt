---
title: "Behavioral Changes"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Behavioral Changes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Behavioral changes are those changes for which the <legacyItalic>syntax</legacyItalic> of the interface remains the same, but the <legacyItalic>semantics</legacyItalic> have changed. For these changes, functionality used in ODBC 2.<legacyItalic>x </legacyItalic>behaves differently than the same functionality in ODBC 3.<legacyItalic>x</legacyItalic>.</para>
    <para>Whether an application exhibits ODBC 2.<legacyItalic>x</legacyItalic> behavior or ODBC 3.<legacyItalic>x</legacyItalic> behavior is determined by the SQL_ATTR_ODBC_VERSION environment attribute. This 32-bit value is set to SQL_OV_ODBC2 to exhibit ODBC 2.<legacyItalic>x</legacyItalic> behavior, and SQL_OV_ODBC3 to exhibit ODBC 3.<legacyItalic>x</legacyItalic> behavior.</para>
    <para>The SQL_ATTR_ODBC_VERSION environment attribute is set by a call to <legacyBold>SQLSetEnvAttr</legacyBold>. After an application calls <legacyBold>SQLAllocHandle</legacyBold> to allocate an environment handle, it must call<legacyBold>SQLSetEnvAttr</legacyBold> immediately to set the behavior it exhibits. (As a result, there is a new environment state to describe the environment handle in an allocated, but versionless, state.) For more information, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
    <para>An application states what behavior it exhibits with the SQL_ATTR_ODBC_VERSION environment attribute, but the attribute has no effect on the application's connection with an ODBC 2.<legacyItalic>x</legacyItalic> or ODBC 3.<legacyItalic>x</legacyItalic> driver. An ODBC 3.<legacyItalic>x</legacyItalic> application can connect to either an ODBC 2.<legacyItalic>x </legacyItalic>or 3.<legacyItalic>x</legacyItalic> driver, no matter what the setting of the environment attribute.</para>
    <para>ODBC 3.<legacyItalic>x</legacyItalic> applications should never call <legacyBold>SQLAllocEnv</legacyBold>. As a result, if the Driver Manager receives a call to <legacyBold>SQLAllocEnv</legacyBold>, it recognizes the application as an ODBC 2.<legacyItalic>x </legacyItalic>application.</para>
    <para>The SQL_ATTR_ODBC_VERSION attribute affects three different aspects of an ODBC 3.<legacyItalic>x</legacyItalic> driver's behavior:  </para>
    <list class="bullet">
      <listItem>
        <para>SQLSTATEs</para>
      </listItem>
      <listItem>
        <para>Data types for date, time, and timestamp</para>
      </listItem>
      <listItem>
        <para>The <legacyItalic>CatalogName</legacyItalic> argument in <legacyBold>SQLTables</legacyBold> accepts search patterns in ODBC 3.<legacyItalic>x</legacyItalic>, but not in ODBC 2.<legacyItalic>x</legacyItalic></para>
      </listItem>
    </list>
    <para>The setting of the SQL_ATTR_ODBC_VERSION environment attribute does not affect <legacyBold>SQLSetParam</legacyBold> or <legacyBold>SQLBindParam</legacyBold>. <legacyBold>SQLColAttribute</legacyBold> is also not affected by this bit. Although <legacyBold>SQLColAttribute</legacyBold> returns attributes that are affected by the version of ODBC (date type, precision, scale and length), the intended behavior is determined by the value of the <legacyItalic>FieldIdentifier</legacyItalic> argument. When <legacyItalic>FieldIdentifier </legacyItalic>is equal to SQL_DESC_TYPE, <legacyBold>SQLColAttribute</legacyBold> returns the ODBC 3.<legacyItalic>x</legacyItalic> codes for date, time, and timestamp; when <legacyItalic>FieldIdentifier</legacyItalic> is equal to SQL_COLUMN_TYPE, <legacyBold>SQLColAttribute</legacyBold> returns the ODBC 2.<legacyItalic>x </legacyItalic>codes for date, time, and timestamp.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="6e6cabcf-a204-40eb-b77d-8a0c4a5e8524">SQLSTATE Mappings</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="c38c79f9-8bb0-4633-ac86-542366c09a95">Datetime Data Type Changes</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>