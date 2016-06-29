---
title: Identifier Arguments
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
translation.priority.ht: 
  - en-gb
---
# Identifier Arguments
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If a string in an identifier argument is quoted, the driver removes leading and trailing blanks and treats literally the string within the quotation marks. If the string is not quoted, the driver removes trailing blanks and folds the string to uppercase. Setting an identifier argument to a null pointer returns SQL_ERROR and SQLSTATE HY009 (Invalid use of null pointer), unless the argument is a catalog name and catalogs are not supported.</para>
    <para>These arguments are treated as identifier arguments if the SQL_ATTR_METADATA_ID statement attribute is set to SQL_TRUE. In this case, the underscore (_) and the percent sign (%) will be treated as the actual character, not as a search pattern character. These arguments are treated as either an ordinary argument or a pattern argument, depending on the argument, if this attribute is set to SQL_FALSE.</para>
    <para>Although identifiers containing special characters must be quoted in SQL statements, they must not be quoted when passed as catalog function arguments, because quote characters passed to catalog functions are interpreted literally. For example, suppose the identifier quote character (which is driver-specific and returned through <legacyBold>SQLGetInfo</legacyBold>) is a double quotation mark ("). The first call to <legacyBold>SQLTables</legacyBold> returns a result set containing information about the Accounts Payable table, while the second call returns information about the "Accounts Payable" table, which is probably not what was intended.</para>
    <code>SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);</code>
    <para>Quoted identifiers are used to distinguish a true column name from a pseudo-column of the same name, such as ROWID in Oracle. If "ROWID" is passed in an argument of a catalog function, the function will work with the ROWID pseudo-column if it exists. If the pseudo-column does not exist, the function will work with the "ROWID" column. If ROWID is passed in an argument of a catalog function, the function will work with the ROWID column.</para>
    <para>For more information about quoted identifiers, see <legacyLink xlink:href="729ba55f-743b-4a04-8c39-ac0a9914211d">Quoted Identifiers</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>