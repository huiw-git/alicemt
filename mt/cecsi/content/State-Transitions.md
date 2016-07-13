---
title: State Transitions
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc741611-6535-43cc-8156-6d897d04664e
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# State Transitions
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC defines discrete <legacyItalic>states</legacyItalic> for each environment, each connection, and each statement. For example, the environment has three possible states: Unallocated (in which no environment is allocated), Allocated (in which an environment is allocated but no connections are allocated), and Connection (in which an environment and one or more connections are allocated). Connections have seven possible states; statements have 13 possible states.</para>
    <para>A particular item, as identified by its handle, moves from one state to another when the application calls a certain function or functions and passes the handle to that item. Such movement is called a <legacyItalic>state transition</legacyItalic>. For example, allocating an environment handle with <legacyBold>SQLAllocHandle</legacyBold> moves the environment from Unallocated to Allocated, and freeing that handle with <legacyBold>SQLFreeHandle</legacyBold> returns it from Allocated to Unallocated. ODBC defines a limited number of legal state transitions, which is another way of saying that functions must be called in a certain order.</para>
    <para>Some functions, such as <legacyBold>SQLGetConnectAttr</legacyBold>, do not affect state at all. Other functions affect the state of a single item. For example, <legacyBold>SQLDisconnect</legacyBold> moves a connection from a Connection state to an Allocated state. Finally, some functions affect the state of more than one item. For example, allocating a connection handle with <legacyBold>SQLAllocHandle</legacyBold> moves a connection from an Unallocated to an Allocated state and moves the environment from an Allocated to a Connection state.</para>
    <para>If an application calls a function out of order, the function returns a <legacyItalic>state transition error</legacyItalic>. For example, if an environment is in a Connection state and the application calls <legacyBold>SQLFreeHandle</legacyBold> with that environment handle, <legacyBold>SQLFreeHandle</legacyBold> returns SQLSTATE HY010 (Function sequence error), because it can be called only when the environment is in an Allocated state. By defining this as an invalid state transition, ODBC prevents the application from freeing the environment while there are active connections.</para>
    <para>Some state transitions are inherent in the design of ODBC. For example, it is not possible to allocate a connection handle without first allocating an environment handle, because the function that allocates a connection handle requires an environment handle. Other state transitions are enforced by the Driver Manager and the drivers. For example, <legacyBold>SQLExecute</legacyBold> executes a prepared statement. If the statement handle passed to it is not in a Prepared state, <legacyBold>SQLExecute</legacyBold> returns SQLSTATE HY010 (Function sequence error).</para>
    <para>From the application's point of view, state transitions are usually straightforward: Legal state transitions tend to go hand-in-hand with the flow of a well-written application. State transitions are more complex for the Driver Manager and the drivers because they must track the state of the environment, each connection, and each statement. Most of this work is done by the Driver Manager; most of the work that must be done by drivers occurs with statements with pending results.</para>
    <para>Parts 1 and 2 of this manual ("Introduction to ODBC" and "Developing Applications and Drivers") tend not to explicitly mention state transitions. Instead, they describe the order in which functions must be called. For example, "Executing Statements" states that a statement must be prepared with <legacyBold>SQLPrepare</legacyBold> before it can be executed with <legacyBold>SQLExecute</legacyBold>. For a complete description of states and state transitions, including which transitions are checked by the Driver Manager and which must be checked by drivers, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>