---
title: Allocating a Connection Handle ODBC
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
translation.priority.ht: 
  - en-gb
---
# Allocating a Connection Handle ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Before the application can connect to a data source or driver, it must allocate a connection handle, as follows:  </para>
    <list class="ordered">
      <listItem>
        <para>The application declares a variable of type SQLHDBC. It then calls <legacyBold>SQLAllocHandle</legacyBold> and passes the address of this variable, the handle of the environment in which to allocate the connection, and the SQL_HANDLE_DBC option. For example: </para>
        <code>SQLHDBC hdbc1;

SQLAllocHandle(SQL_HANDLE_DBC, henv1, &amp;hdbc1);</code>
      </listItem>
      <listItem>
        <para>The Driver Manager allocates a structure in which to store information about the statement and returns the connection handle in the variable.</para>
      </listItem>
    </list>
    <para>The Driver Manager does not call <legacyBold>SQLAllocHandle</legacyBold> in the driver at this time because it does not know which driver to call. It delays calling <legacyBold>SQLAllocHandle</legacyBold> in the driver until the application calls a function to connect to a data source. For more information, see <legacyLink xlink:href="77c05630-5a8b-467d-b80e-c705dc06d601">Driver Manager's Role in the Connection Process</legacyLink>, later in this section.</para>
    <para>It is important to note that allocating a connection handle is not the same as loading a driver. The driver is not loaded until a connection function is called. Thus, after allocating a connection handle and before connecting to the driver or data source, the only functions the application can call with the connection handle are <legacyBold>SQLSetConnectAttr</legacyBold>, <legacyBold>SQLGetConnectAttr</legacyBold>, or <legacyBold>SQLGetInfo</legacyBold> with the SQL_ODBC_VER option. Calling other functions with the connection handle, such as <legacyBold>SQLEndTran</legacyBold>, returns SQLSTATE 08003 (Connection not open). For complete details, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
    <para>For more information about connection handles, see <legacyLink xlink:href="12222653-f04d-46d6-bdee-61348f5d550f">Connection Handles</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>