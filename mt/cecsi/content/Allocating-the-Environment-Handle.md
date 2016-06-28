---
title: Allocating the Environment Handle
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
translation.priority.ht: 
  - en-gb
---
# Allocating the Environment Handle
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The first task for any ODBC application is to load the Driver Manager; how this is done is operating-system dependent. For example, on a computer running Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional, or Microsoft Windows® 95/98, the application either links to the Driver Manager library or calls <legacyBold>LoadLibrary</legacyBold> to load the Driver Manager DLL.</para>
    <para>The next task, which must be done before an application can call any other ODBC function, is to initialize the ODBC environment and allocate an environment handle, as follows:  </para>
    <list class="ordered">
      <listItem>
        <para>The application declares a variable of type SQLHENV. It then calls <legacyBold>SQLAllocHandle</legacyBold> and passes the address of this variable and the SQL_HANDLE_ENV option. For example: </para>
        <code>SQLHENV henv1;

SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &amp;henv1);</code>
      </listItem>
      <listItem>
        <para>The Driver Manager allocates a structure in which to store information about the environment, and returns the environment handle in the variable.</para>
      </listItem>
    </list>
    <para>The Driver Manager does not call <legacyBold>SQLAllocHandle</legacyBold> in the driver at this time because it does not know which driver to call. It delays calling <legacyBold>SQLAllocHandle</legacyBold> in the driver until the application calls a function to connect to a data source. For more information, see <legacyLink xlink:href="77c05630-5a8b-467d-b80e-c705dc06d601">Driver Manager's Role in the Connection Process</legacyLink>, later in this section.</para>
    <para>When the application has finished using ODBC, it frees the environment handle with <legacyBold>SQLFreeHandle</legacyBold>. After freeing the environment, it is an application programming error to use the environment's handle in a call to an ODBC function; doing so has undefined but probably fatal consequences.</para>
    <para>When <legacyBold>SQLFreeHandle</legacyBold> is called, the driver releases the structure used to store information about the environment. Note that <legacyBold>SQLFreeHandle</legacyBold> cannot be called for an environment handle until after all connection handles on that environment handle have been freed.</para>
    <para>For more information about the environment handle, see <legacyLink xlink:href="917f1b0c-272b-4e37-a1f5-87cd24b9fa21">Environment Handles</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>