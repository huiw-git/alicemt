---
title: Scrollable Cursors and Transaction Isolation
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
translation.priority.ht: 
  - en-gb
---
# Scrollable Cursors and Transaction Isolation
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists the factors governing the visibility of changes.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Changes made by:</para>
          </TD>
          <TD>
            <para>Visibility depends on:</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Cursor</para>
          </TD>
          <TD>
            <para>Cursor type, cursor implementation</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Other statements in same transaction</para>
          </TD>
          <TD>
            <para>Cursor type</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Statements in other transactions</para>
          </TD>
          <TD>
            <para>Cursor type, transaction isolation level</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>These factors are shown in the following illustration.</para>
    <mediaLink>
      <image xlink:href="f5fc3937-9034-420d-8b7e-812e09a24d43" />
    </mediaLink>
    <para>The following table summarizes the ability of each cursor type to detect changes made by itself, by other operations in its own transaction, and by other transactions. The visibility of the latter changes depends on the cursor type and the isolation level of the transaction containing the cursor.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Cursor type\action</para>
          </TD>
          <TD>
            <para>Self</para>
          </TD>
          <TD>
            <para>Own</para>
            <para>Txn</para>
          </TD>
          <TD>
            <para>Othr</para>
            <para>Txn</para>
            <para>(RU[a])</para>
          </TD>
          <TD>
            <para>Othr</para>
            <para>Txn</para>
            <para>(RC[a])</para>
          </TD>
          <TD>
            <para>Othr</para>
            <para>Txn</para>
            <para>(RR[a])</para>
          </TD>
          <TD>
            <para>Othr</para>
            <para>Txn</para>
            <para>(S[a])</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Static</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Insert</para>
          </TD>
          <TD>
            <para>Maybe[b]</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Update</para>
          </TD>
          <TD>
            <para>Maybe[b]</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Delete</para>
          </TD>
          <TD>
            <para>Maybe[b]</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Keyset-driven</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Insert</para>
          </TD>
          <TD>
            <para>Maybe[b]</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Update</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Delete</para>
          </TD>
          <TD>
            <para>Maybe[b]</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Dynamic</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Insert</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Update</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>   Delete</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>Yes</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
          <TD>
            <para>No</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The letters in parentheses indicate the isolation level of the transaction containing the cursor; the isolation level of the other transaction (in which the change was made) is irrelevant.</para>
    <para>RU: Read uncommitted</para>
    <para>RC: Read committed</para>
    <para>RR: Repeatable read</para>
    <para>S:  Serializable</para>
    <para>[b]   Depends on how the cursor is implemented. Whether the cursor can detect such changes is reported through the SQL_STATIC_SENSITIVITY option in <legacyBold>SQLGetInfo</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>