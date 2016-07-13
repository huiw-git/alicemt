---
title: Setting ODBC Connection Pooling Options
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 037e2f78-f204-40f4-b4ab-d9cdf562012b
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting ODBC Connection Pooling Options
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Connection pooling enables an application to use a connection from a pool of connections that do not need to be reestablished for each use. You can use the <legacyBold>Connection Pooling</legacyBold> tab of the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box to enable and disable performance monitoring. Double-click a driver name to set the connection time-out period.</para>
    <para>At the driver level, connection pooling is enabled by the CPTimeout registry value. This selective per-driver enabling allows a system administrator to enable connection pooling for just the drivers that can support it. It is accomplished by setting the default value of CPTimeout during the driver's setup program. Double-click a driver name to set the connection time-out period.</para>
    <para>For more information about connection pooling, see <legacyLink xlink:href="ee95ffdb-5aa1-49a3-beb2-7695b27c3df9">ODBC Connection Pooling</legacyLink>.</para>
  </introduction>
  <section>
    <title>Performance Monitoring</title>
    <content>
      <para>Performance monitoring tracks connection performance by recording a variety of statistics. These statistics can be customized by the developer to include items such as the following:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Counter</para>
            </TD>
            <TD>
              <para>Definition</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ODBC Hard Connection Counter per Second</para>
            </TD>
            <TD>
              <para>The number of actual connections per second that are made to the server. The first time your environment carries a heavy load, this counter will go up very quickly. After a few seconds, it will drop to zero. This is the normal situation when connection pooling is working. When the connections to the server have been established, they will be used and placed in the pool for reuse.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC Hard Disconnect Counter per Second</para>
            </TD>
            <TD>
              <para>The number of hard disconnects per second issued to the server. These are actual connections to the server that are being released by connection pooling. This value will increase from zero when you stop all clients on the system and the connections start to time out.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC Soft Connection Counter per Second</para>
            </TD>
            <TD>
              <para>The number of connections satisfied by the pool per second—in other words, connections from that pool that were handed to users. This counter indicates whether pooling is working. Depending on the load on your server, it is not uncommon for this to show 40–60 soft connections per second.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC Soft Disconnection Counter per Second</para>
            </TD>
            <TD>
              <para>The number of disconnects per second issued by the applications. When the application releases or disconnects, the connection is placed back in the pool.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC Current Active Connection Counter</para>
            </TD>
            <TD>
              <para>The number of connections in the pool that are currently in use.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC Current Free Connection Counter</para>
            </TD>
            <TD>
              <para>The current number of free connections available in the pool. These are live connections that are available for use.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Pools Currently Active</para>
            </TD>
            <TD>
              <para>The number of pools currently active. This counter was added in Windows 8, for drivers that manage connections in the connection pool. For more information, see <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling.</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Pools Created</para>
            </TD>
            <TD>
              <para>The number of pools active, including active and removed pools. This counter was added in Windows 8, for drivers that manage connections in the connection pool. For more information, see <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling.</link>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>You must specify your own monitoring parameters. Samples for performance monitoring have been included with this version of ODBC.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>