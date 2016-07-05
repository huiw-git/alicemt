---
title: Transaction Isolation Levels
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d638d55-ffd0-48fb-834b-406f466214d4
translation.priority.ht: 
  - en-gb
---
# Transaction Isolation Levels
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyItalic>Transaction isolation levels</legacyItalic> are a measure of the extent to which transaction isolation succeeds. In particular, transaction isolation levels are defined by the presence or absence of the following phenomena:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Dirty Reads</legacyBold> A <legacyItalic>dirty read</legacyItalic> occurs when a transaction reads data that has not yet been committed. For example, suppose transaction 1 updates a row. Transaction 2 reads the updated row before transaction 1 commits the update. If transaction 1 rolls back the change, transaction 2 will have read data that is considered never to have existed.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Nonrepeatable Reads</legacyBold> A <legacyItalic>nonrepeatable read</legacyItalic> occurs when a transaction reads the same row twice but gets different data each time. For example, suppose transaction 1 reads a row. Transaction 2 updates or deletes that row and commits the update or delete. If transaction 1 rereads the row, it retrieves different row values or discovers that the row has been deleted.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Phantoms</legacyBold> A <legacyItalic>phantom</legacyItalic> is a row that matches the search criteria but is not initially seen. For example, suppose transaction 1 reads a set of rows that satisfy some search criteria. Transaction 2 generates a new row (through either an update or an insert) that matches the search criteria for transaction 1. If transaction 1 reexecutes the statement that reads the rows, it gets a different set of rows.</para>
      </listItem>
    </list>
    <para>The four transaction isolation levels (as defined by SQL-92) are defined in terms of these phenomena. In the following table, an "X" marks each phenomenon that can occur.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Transaction isolation level</para>
          </TD>
          <TD>
            <para>Dirty reads</para>
          </TD>
          <TD>
            <para>Nonrepeatable reads</para>
          </TD>
          <TD>
            <para>Phantoms</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Read uncommitted</para>
          </TD>
          <TD>
            <para>X</para>
          </TD>
          <TD>
            <para>X</para>
          </TD>
          <TD>
            <para>X</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Read committed</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
          <TD>
            <para>X</para>
          </TD>
          <TD>
            <para>X</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Repeatable read</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
          <TD>
            <para>X</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Serializable</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
          <TD>
            <para>--</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following table describes simple ways that a DBMS might implement the transaction isolation levels.</para>
    <alert class="important">
      <para>Most DBMSs use more complex schemes than these to increase concurrency. These examples are provided for illustration purposes only. In particular, ODBC does not prescribe how particular DBMSs isolate transactions from each other.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Transaction isolation</para>
          </TD>
          <TD>
            <para>Possible implementation</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Read uncommitted</para>
          </TD>
          <TD>
            <para>Transactions are not isolated from each other. If the DBMS supports other transaction isolation levels, it ignores whatever mechanism it uses to implement those levels. So that they do not adversely affect other transactions, transactions running at the Read Uncommitted level are usually read-only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Read committed</para>
          </TD>
          <TD>
            <para>The transaction waits until rows write-locked by other transactions are unlocked; this prevents it from reading any "dirty" data.</para>
            <para>The transaction holds a read lock (if it only reads the row) or write lock (if it updates or deletes the row) on the current row to prevent other transactions from updating or deleting it. The transaction releases read locks when it moves off the current row. It holds write locks until it is committed or rolled back.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Repeatable read</para>
          </TD>
          <TD>
            <para>The transaction waits until rows write-locked by other transactions are unlocked; this prevents it from reading any "dirty" data.</para>
            <para>The transaction holds read locks on all rows it returns to the application and write locks on all rows it inserts, updates, or deletes. For example, if the transaction includes the SQL statement <legacyBold>SELECT * FROM Orders</legacyBold>, the transaction read-locks rows as the application fetches them. If the transaction includes the SQL statement <legacyBold>DELETE FROM Orders WHERE Status = 'CLOSED'</legacyBold>, the transaction write-locks rows as it deletes them.</para>
            <para>Because other transactions cannot update or delete these rows, the current transaction avoids any nonrepeatable reads. The transaction releases its locks when it is committed or rolled back.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Serializable</para>
          </TD>
          <TD>
            <para>The transaction waits until rows write-locked by other transactions are unlocked; this prevents it from reading any "dirty" data.</para>
            <para>The transaction holds a read lock (if it only reads rows) or write lock (if it can update or delete rows) on the range of rows it affects. For example, if the transaction includes the SQL statement <legacyBold>SELECT * FROM Orders</legacyBold>, the range is the entire Orders table; the transaction read-locks the table and does not allow any new rows to be inserted into it. If the transaction includes the SQL statement <legacyBold>DELETE FROM Orders WHERE Status = 'CLOSED'</legacyBold>, the range is all rows with a Status of "CLOSED"; the transaction write-locks all rows in the Orders table with a Status of "CLOSED" and does not allow any rows to be inserted or updated such that the resulting row has a Status of "CLOSED".</para>
            <para>Because other transactions cannot update or delete the rows in the range, the current transaction avoids any nonrepeatable reads. Because other transactions cannot insert any rows in the range, the current transaction avoids any phantoms. The transaction releases its lock when it is committed or rolled back.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>It is important to note that the transaction isolation level does not affect a transaction's ability to see its own changes; transactions can always see any changes they make. For example, a transaction might consist of two <legacyBold>UPDATE</legacyBold> statements, the first of which raises the pay of all employees by 10 percent and the second of which sets the pay of any employees over some maximum amount to that amount. This succeeds as a single transaction only because the second <legacyBold>UPDATE</legacyBold> statement can see the results of the first.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>