---
title: "Effect of Transactions on Cursors and Prepared Statements"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Effect of Transactions on Cursors and Prepared Statements
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Committing or rolling back a transaction has the following effect on cursors and access plans:  </para>
    <list class="bullet">
      <listItem>
        <para>All cursors are closed, and access plans for prepared statements on that connection are deleted.</para>
      </listItem>
      <listItem>
        <para>All cursors are closed, and access plans for prepared statements on that connection remain intact.</para>
      </listItem>
      <listItem>
        <para>All cursors remain open, and access plans for prepared statements on that connection remain intact.</para>
      </listItem>
    </list>
    <para>For example, suppose a data source exhibits the first behavior in this list, the most restrictive of these behaviors. Now suppose an application does the following:  </para>
    <list class="ordered">
      <listItem>
        <para>Sets the commit mode to manual-commit.</para>
      </listItem>
      <listItem>
        <para>Creates a result set of sales orders on statement 1.</para>
      </listItem>
      <listItem>
        <para>Creates a result set of the lines in a sales order on statement 2, when the user highlights that order.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLExecute</legacyBold> to execute a positioned update statement that has been prepared on statement 3, when the user updates a line.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLEndTran</legacyBold> to commit the positioned update statement.</para>
      </listItem>
    </list>
    <para>Because of the data source's behavior, the call to <legacyBold>SQLEndTran</legacyBold> in step 5 causes it to close the cursors on statements 1 and 2 and to delete the access plan on all statements. The application must reexecute statements 1 and 2 to re-create the result sets and reprepare the statement on statement 3.</para>
    <para>In auto-commit mode, functions other than <legacyBold>SQLEndTran</legacyBold> commit transactions:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> In the preceding example, the call to <legacyBold>SQLExecute</legacyBold> in step 4 commits a transaction. This causes the data source to close the cursors on statements 1 and 2 and delete the access plan on all statements on that connection.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> In the preceding example, suppose that in step 4 the application calls <legacyBold>SQLSetPos</legacyBold> with the SQL_UPDATE option on statement 2, instead of executing a positioned update statement on statement 3. This commits a transaction and causes the data source to close the cursors on statements 1 and 2, and discards all access plans on that connection.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>SQLCloseCursor</legacyBold> In the preceding example, suppose that when the user highlights a different sales order, the application calls <legacyBold>SQLCloseCursor</legacyBold> on statement 2 before creating a result of the lines for the new sales order. The call to <legacyBold>SQLCloseCursor</legacyBold> commits the <legacyBold>SELECT</legacyBold> statement that created the result set of lines and causes the data source to close the cursor on statement 1, and then discards all access plans on that connection.</para>
      </listItem>
    </list>
    <para>Applications, especially screen-based applications in which the user scrolls around the result set and updates or deletes rows, must be careful to code around this behavior.</para>
    <para>To determine how a data source behaves when a transaction is committed or rolled back, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR options.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>