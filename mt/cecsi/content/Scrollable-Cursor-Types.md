---
title: Scrollable Cursor Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Scrollable Cursor Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The four types of scrollable cursors are static, dynamic, keyset-driven, and mixed. Static cursors detect few or no changes but are relatively cheap to implement. Dynamic cursors detect all changes but are expensive to implement. Keyset-driven and mixed cursors lie in between, detecting most changes but at less expense than dynamic cursors.</para>
    <para>The following terms are used to define the characteristics of each type of scrollable cursor:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Own updates, deletes, and inserts.</legacyBold> Updates, deletes, and inserts made through the cursor, either with a call to <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> or with a positioned update or delete statement.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Other updates, deletes, and inserts.</legacyBold> Updates, deletes, and inserts not made by the cursor, including those made by other operations in the same transaction, those made through other transactions, and those made by other applications.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Membership.</legacyBold> The set of rows in the result set.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Order.</legacyBold> The order in which rows are returned by the cursor.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Values.</legacyBold> The values in each row in the result set.</para>
      </listItem>
    </list>
    <para>For information about how to update, delete, and insert data, see <legacyLink xlink:href="062036a4-cda6-4aaa-9765-f1ec3e0b31b1">Updating Data Overview</legacyLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="28cb324c-e1c3-4b5c-bc3e-54df87037317">ODBC Static Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="de709fd3-9eb2-44e1-a2f0-786e2b9602a6">ODBC Dynamic Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="01769f43-1d9c-4685-84fa-15a6465335e9">Keyset-Driven Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9beb2db9-0b6d-491d-9529-d64e64e59014">Mixed Cursors</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>