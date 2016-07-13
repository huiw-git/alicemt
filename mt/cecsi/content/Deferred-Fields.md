---
title: Deferred Fields
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5abeb9cc-4070-4f43-a80d-ad6a2004e5f3
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Deferred Fields
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The values of <legacyItalic>deferred fields</legacyItalic> are not used when they are set, but the driver saves the addresses of the variables for a deferred effect. For an application parameter descriptor, the driver uses the contents of the variables at the time of the call to <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold>. For an application row descriptor, the driver uses the contents of the variables at the time of the fetch.</para>
    <para>The following are deferred fields:  </para>
    <list class="bullet">
      <listItem>
        <para>The SQL_DESC_DATA_PTR and SQL_DESC_INDICATOR_PTR fields of a descriptor record.</para>
      </listItem>
      <listItem>
        <para>The SQL_DESC_OCTET_LENGTH_PTR field of an application descriptor record.</para>
      </listItem>
      <listItem>
        <para>In the case of a multirow fetch, the SQL_DESC_ARRAY_STATUS_PTR and SQL_DESC_ROWS_PROCESSED_PTR fields of a descriptor header.</para>
      </listItem>
    </list>
    <para>When a descriptor is allocated, the deferred fields of each descriptor record initially have a null value. The meaning of the null value is as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>If SQL_DESC_ARRAY_STATUS_PTR has a null value, a multirow fetch fails to return this component of the per-row diagnostic information.</para>
      </listItem>
      <listItem>
        <para>If SQL_DESC_DATA_PTR has a null value, the record is unbound.</para>
      </listItem>
      <listItem>
        <para>If the SQL_DESC_OCTET_LENGTH_PTR field of an ARD has a null value, the driver does not return length information for that column.</para>
      </listItem>
      <listItem>
        <para>If the SQL_DESC_OCTET_LENGTH_PTR field of an APD has a null value and the parameter is a character string, the driver assumes that string is null-terminated. For output dynamic parameters, a null value in this field prevents the driver from returning length information. (If the SQL_DESC_TYPE field does not indicate a character-string parameter, the SQL_DESC_OCTET_LENGTH_PTR field is ignored.)</para>
      </listItem>
    </list>
    <para>The application must not deallocate or discard variables used for deferred fields between the time it associates them with the fields and the time the driver reads or writes them.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>