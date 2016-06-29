---
title: Translation DLLs
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38975059-b346-410f-bb27-326f3f7bbf39
translation.priority.ht: 
  - en-gb
---
# Translation DLLs
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The application and data source often store data in different character sets. ODBC provides a generic mechanism that allows the driver to translate data from one character set to another. It consists of a DLL that implements the translation functions <legacyBold>SQLDriverToDataSource</legacyBold> and <legacyBold>SQLDataSourceToDriver</legacyBold>, which are called by the driver to translate all data flowing between the data source and driver. This DLL can be written by the application developer, the driver developer, or a third party.</para>
    <para>The translation DLL for a particular data source can be specified in the system information for that data source; for more information, see <legacyLink xlink:href="d7e88a07-e6ab-4258-a45d-1ca21234fbec">Data Source Specification Subkeys</legacyLink>. It can also be set at run time with the SQL_ATTR_TRANSLATE_DLL and SQL_ATTR_TRANSLATE_OPTION connection attributes.</para>
    <para>The translation option is a value that can be interpreted only by a particular translation DLL. For example, if the translation DLL translates between different code pages, the option might give the numbers of the code pages used by the application and the data source. There is no requirement for a translation DLL to use a translation option.</para>
    <para>After a translation DLL has been specified, the driver loads it and calls it to translate all data flowing between the application and data source. This includes all SQL statements and character parameters being sent to the data source, and all character results, character metadata such as column names, and error messages retrieved from the data source. Connection data is not translated, because the translation DLL is not loaded until after the application has connected to the data source.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>