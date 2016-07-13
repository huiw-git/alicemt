---
title: Transferring Data in Its Binary Form
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Transferring Data in Its Binary Form
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application can safely transfer data (in the internal form used by a specified DBMS) between two data sources that use the same DBMS and hardware platform. For a given piece of data, the SQL data types must be the same in the source and target data sources. The C data type is SQL_C_BINARY.</para>
  </introduction>
  <section>
    <content>
      <para>When the application calls <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold> to retrieve the data from the source data source, the driver retrieves the data from the data source and transfers it, without conversion, to a storage location of type SQL_C_BINARY. When the application calls <legacyBold>SQLBulkOperations</legacyBold>,<legacyBold> SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLPutData, or SQLSetPos </legacyBold>to send the data to the target data source, the driver retrieves the data from the storage location and transfers it, without conversion, to the target data source.</para>
      <alert class="note">
        <para>Applications that transfer any data (except binary data) in this manner are not interoperable among DBMSs.</para>
      </alert>
      <para>
        <legacyBold>SQLCopyDesc</legacyBold> can be used to copy row bindings from the source DBMS to parameter bindings in the target DBMS.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>