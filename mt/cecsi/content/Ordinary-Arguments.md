---
title: Ordinary Arguments
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
translation.priority.ht: 
  - en-gb
---
# Ordinary Arguments
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When a catalog function string argument is an ordinary argument, it is treated as a literal string. An ordinary argument accepts neither a string search pattern nor a list of values. The case of an ordinary argument is significant, and quote characters in the string are taken literally. These arguments are treated as ordinary arguments if the SQL_ATTR_METADATA_ID statement attribute is set to SQL_FALSE; they are treated as identifier arguments instead if this attribute is set to SQL_TRUE.</para>
    <para>If an ordinary argument is set to a null pointer and the argument is a required argument, the function returns SQL_ERROR and SQLSTATE HY009 (Invalid use of null pointer). If an ordinary argument is set to a null pointer and the argument is not a required argument, the argument's behavior is driver-dependent. The required arguments are listed in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Function</para>
          </TD>
          <TD>
            <para>Required arguments</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColumnPrivileges</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLForeignKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>PKTableName</legacyItalic>, <legacyItalic>FKTableName</legacyItalic></para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLPrimaryKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSpecialColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLStatistics</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>