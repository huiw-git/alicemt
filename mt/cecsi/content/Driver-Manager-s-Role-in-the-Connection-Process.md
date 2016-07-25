---
title: "Driver Manager&#39;s Role in the Connection Process"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77c05630-5a8b-467d-b80e-c705dc06d601
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Manager&#39;s Role in the Connection Process
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Remember that applications do not call driver functions directly. Instead, they call Driver Manager functions with the same name and the Driver Manager calls the driver functions. Usually, this happens almost immediately. For example, the application calls <legacyBold>SQLExecute</legacyBold> in the Driver Manager and after a few error checks, the Driver Manager calls <legacyBold>SQLExecute</legacyBold> in the driver.</para>
    <para>The connection process is different. When the application calls <legacyBold>SQLAllocHandle</legacyBold> with the SQL_HANDLE_ENV and SQL_HANDLE_DBC options, the function allocates handles only in the Driver Manager. The Driver Manager does not call this function in the driver because it does not know which driver to call. Similarly, if the application passes the handle of an unconnected connection to <legacyBold>SQLSetConnectAttr</legacyBold> or <legacyBold>SQLGetConnectAttr</legacyBold>, only the Driver Manager executes the function. It stores or gets the attribute value from its connection handle and returns SQLSTATE 08003 (Connection not open) when getting a value for an attribute that has not been set and for which ODBC does not define a default value.</para>
    <para>When the application calls <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, or <legacyBold>SQLBrowseConnect</legacyBold>, the Driver Manager first determines which driver to use. It then checks to determine whether a driver is currently loaded on the connection:  </para>
    <list class="bullet">
      <listItem>
        <para>If no driver is loaded on the connection, the Driver Manager checks whether the specified driver is loaded on another connection in the same environment. If not, the Driver Manager loads the driver on the connection and calls <legacyBold>SQLAllocHandle</legacyBold> in the driver with the SQL_HANDLE_ENV option. </para>
        <para>The Driver Manager then calls <legacyBold>SQLAllocHandle</legacyBold> in the driver with the SQL_HANDLE_DBC option, whether or not it was just loaded. If the application set any connection attributes, the Driver Manager calls <legacyBold>SQLSetConnectAttr</legacyBold> in the driver; if an error occurs, the Driver Manager's connection function returns SQLSTATE IM006 (Driver's <legacyBold>SQLSetConnectAttr</legacyBold> failed). Finally, the Driver Manager calls the connection function in the driver. </para>
      </listItem>
      <listItem>
        <para>If the specified driver is loaded on the connection, the Driver Manager calls only the connection function in the driver. In this case, the driver must make sure that all connection attributes on the connection maintain their current settings.</para>
      </listItem>
      <listItem>
        <para>If a different driver is loaded on the connection, the Driver Manager calls <legacyBold>SQLFreeHandle</legacyBold> in the driver to free the connection. If there are no other connections that use the driver, the Driver Manager calls <legacyBold>SQLFreeHandle</legacyBold> in the driver to free the environment and unloads the driver. The Driver Manager then performs the same operations as when a driver is not loaded on the connection.</para>
      </listItem>
    </list>
    <para>The Driver Manager will lock the environment handle (<parameterReference>henv</parameterReference>) before calling a driver’s <unmanagedCodeEntityReference>SQLAllocHandle</unmanagedCodeEntityReference> and<unmanagedCodeEntityReference> SQLFreeHandle</unmanagedCodeEntityReference> when <parameterReference>HandleType</parameterReference> is set to <languageKeyword>SQL_HANDLE_DBC</languageKeyword>.</para>
    <para>When the application calls <legacyBold>SQLDisconnect</legacyBold>, the Driver Manager calls <legacyBold>SQLDisconnect</legacyBold> in the driver. However, it leaves the driver loaded in case the application reconnects to the driver. When the application calls <legacyBold>SQLFreeHandle</legacyBold> with the SQL_HANDLE_DBC option, the Driver Manager calls <legacyBold>SQLFreeHandle</legacyBold> in the driver. If the driver is not used by any other connections, the Driver Manager then calls <legacyBold>SQLFreeHandle</legacyBold> in the driver with the SQL_HANDLE_ENV option and unloads the driver.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>