---
title: "Notification of Asynchronous Function Completion"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Notification of Asynchronous Function Completion
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In the Windows 8 SDK, ODBC added a mechanism to notify applications when an asynchronous operation completes, which we will refer to as "notification on completion". (See <link xlink:href="e509dad9-5263-4a10-9a4e-03b84b66b6b3">Asynchronous Execution (Notification Method)</link> for more information.) This topic discusses some of the issues for driver developers.</para>
  </introduction>
  <section>
    <title>The Interface between the Driver Manager and Driver</title>
    <content>
      <para>The Driver Manager internally provides a callback function <link xlink:href="c56aedc9-f7f7-4641-b605-f0f98ed4400c">SQLAsyncNotificationCallback</link>. <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> can only be called by the driver -- an application cannot directly call it. The driver calls <languageKeyword>SQLAsyncNotificationCallback</languageKeyword> whenever new data received from the server after last returning SQL_STILL_EXECUTING.</para>
      <para>The Driver Manager provides a callback mechanism so a driver can notify the Driver Manager when some progress has been made in executing an asynchronous operation after the corresponding function returns SQL_STILL_EXECUTING</para>
      <para>The Driver Manager sets the SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK attribute on a driver connection handle with a non-NULL function pointer, which is of type SQL_ASYNC_NOTIFICATION_CALLBACK, for the driver to work in notification mode for any asynchronous operations on that handle. Similarly, the Driver Manager sets the SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK attribute on a driver statement handle with a non-NULL function pointer, which is also of type SQL_ASYNC_NOTIFICATION_CALLBACK, for the driver to work in notification mode for any asynchronous operations on that handle.</para>
      <para>If an asynchronous operation is performed on a driver handle, the asynchronous driver functions should work in a non-blocking style. If the operation cannot complete immediately, the driver function should return SQL_STILL_EXECUTING. This requirement is true for both polling mode and notification mode.</para>
      <para>If a handle is in notification asynchronous mode, the driver must call the notification callback function, whose address is the value for the SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK or SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK attribute, once after returning SQL_STILL_EXECUTING. In other words, one returning SQL_STILL_EXECUTING must be paired with one invocation of the notification callback function. The driver should use the current value of the SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT or SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT handle attribute as the value for the call back function parameter <parameterReference>pContext</parameterReference>.</para>
      <para>The driver must not call back in the thread that calls the driver function; there is no reason to notify progress before the function returns. The driver should use its own thread to callback. The Driver Manager will not use the driver’s callback thread for executing extensive processing logic.</para>
      <para>The Driver Manager will call the original function again after the driver calls back. The Driver Manager may use a thread that is neither an application thread nor a driver thread. If the driver uses some information associated with the thread (for example, security token or user identifier), the driver should save the required information in the initial asynchronous call and use the saved value before the whole asynchronous operation completes. Usually, only <languageKeyword>SQLDriverConnect</languageKeyword>, <languageKeyword>SQLConnect</languageKeyword>, or <languageKeyword>SQLBrowseConnect</languageKeyword> need to use that kind of information.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
  </relatedTopics>
</developerConceptualDocument>