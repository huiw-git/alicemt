---
title: "Using RDS with ODBC Connection Pooling"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
caps.latest.revision: 12
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Using RDS with ODBC Connection Pooling
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If you're using an ODBC data source, you can use the connection pooling option in Internet Information Services (IIS) to achieve high performance handling of client load. Connection pooling is a resource manager for connections, maintaining the open state on frequently used connections.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>To enable connection pooling, refer to the Internet Information Services documentation.</para>
    <para>Please note that enabling connection pooling may subject the Web server to other restrictions, as noted in the Microsoft Internet Information Services documentation.</para>
    <para>To ensure that connection pooling is stable and provides additional performance gains, you must configure Microsoft SQL Server to use the TCP/IP Socket network library.</para>
    <para>To do this, you need to: </para>
    <list class="bullet">
      <listItem>
        <para>Configure the SQL Server computer to use TCP/IP Sockets. </para>
      </listItem>
      <listItem>
        <para>Configure the Web server to use TCP/IP Sockets.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Configuring the SQL Server Computer to Use TCP/IP Sockets</title>
    <content>
      <para>On the SQL Server computer, run the SQL Server Setup program so that interactions with the data source use the TCP/IP Socket network library.</para>
    </content>
    <sections>
      <section>
        <title>To specify the TCP/IP Socket network library on the SQL Server computer</title>
        <content />
      </section>
      <section>
        <title>In Microsoft SQL Server 6.5:</title>
        <content>
          <list class="ordered">
            <listItem>
              <para>From the Start menu, point to Programs, point to Microsoft SQL Server 6.5, and then click SQL Setup. </para>
            </listItem>
            <listItem>
              <para>Click Continue twice. </para>
            </listItem>
            <listItem>
              <para>In the Microsoft SQL Server —Options dialog box, select Change Network Support, and then click Continue. </para>
            </listItem>
            <listItem>
              <para>Make sure the TCP/IP Sockets check box is selected, and click OK. </para>
            </listItem>
            <listItem>
              <para>Click Continue to finish, and exit setup. </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>In Microsoft SQL Server 7.0:</title>
        <content>
          <list class="ordered">
            <listItem>
              <para>From the Start menu, point to Programs, point to Microsoft SQL Server 7.0, and then click Server Network Utility. </para>
            </listItem>
            <listItem>
              <para>On the General tab of the dialog box, click Add. </para>
            </listItem>
            <listItem>
              <para>In the Add Network Library Configuration dialog box, click TCP/IP. </para>
            </listItem>
            <listItem>
              <para>In the Port number and Proxy address boxes, enter the port number and proxy address provided by your network administrator. </para>
            </listItem>
            <listItem>
              <para>Click OK to finish, and exit setup. </para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Configuring the Web Server to Use TCP/IP Sockets</title>
    <content>
      <para>There are two options for configuring the Web server to use TCP/IP Sockets. What you do depends on whether all SQL Servers are accessed from the Web server, or only a specific SQL Server is accessed from the Web server.</para>
      <para>If all SQL Servers are accessed from the Web server, you need to run the SQL Server Client Configuration Utility on the Web server computer. The following steps change the default network library for all SQL Server connections made from this IIS Web server to use the TCP/IP Sockets network library.</para>
    </content>
    <sections>
      <section>
        <title>To configure the Web server (all SQL Servers)</title>
        <content />
      </section>
      <section>
        <title>For Microsoft SQL Server 6.5:</title>
        <content>
          <list class="ordered">
            <listItem>
              <para>From the Start menu, point to Programs, point to Microsoft SQL Server 6.5 , and then click SQL Client Configuration Utility. </para>
            </listItem>
            <listItem>
              <para>Click the Net Library tab. </para>
            </listItem>
            <listItem>
              <para>In the Default Network box, select TCP/IP Sockets. </para>
            </listItem>
            <listItem>
              <para>Click Done to save changes and exit the utility. </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>For Microsoft SQL Server 7.0:</title>
        <content>
          <list class="ordered">
            <listItem>
              <para>From the Start menu, point to Programs, point to Microsoft SQL Server 7.0 , and then click Client Network Utility. </para>
            </listItem>
            <listItem>
              <para>Click the General tab. </para>
            </listItem>
            <listItem>
              <para>In the Default network library box, click TCP/IP. </para>
            </listItem>
            <listItem>
              <para>Click OK to save changes and exit the utility. </para>
            </listItem>
          </list>
          <para>If a specific SQL Server is accessed from a Web server, you need to run the SQL Server Client Configuration Utility on the Web server computer. To change the network library for a specific SQL Server connection, configure the SQL Server Client software on the Web server computer as follows.</para>
        </content>
      </section>
      <section>
        <title>To configure the Web server (a specific SQL Server)</title>
        <content />
      </section>
      <section>
        <title>For Microsoft SQL Server 6.5:</title>
        <content>
          <list class="ordered">
            <listItem>
              <para>From the Start menu, point to Programs, point to Microsoft SQL Server 6.5, and then click SQL Client Configuration Utility. </para>
            </listItem>
            <listItem>
              <para>Click the Advanced tab. </para>
            </listItem>
            <listItem>
              <para>In the Server box, type the name of the server to connect to using TCP/IP Sockets. </para>
            </listItem>
            <listItem>
              <para>In the DLL Name box, select TCP/IP Sockets. </para>
            </listItem>
            <listItem>
              <para>Click Add/Modify. All data sources pointing to this server will now use TCP/IP Sockets. </para>
            </listItem>
            <listItem>
              <para>Click Done. </para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>For Microsoft SQL Server 7.0:</title>
        <content>
          <list class="ordered">
            <listItem>
              <para>From the Start menu, point to Programs, point to Microsoft SQL Server 7.0, and then click Client Configuration Utility. </para>
            </listItem>
            <listItem>
              <para>Click the General tab. </para>
            </listItem>
            <listItem>
              <para>Click Add. </para>
            </listItem>
            <listItem>
              <para>Enter the alias of the server in the Server alias box. In the Network libraries box, click TCP/IP. In the Computer name box, enter the computer name of the computer that listens for TCP/IP Sockets clients. In the Port number box, enter the port on which the SQL Server listens. </para>
            </listItem>
            <listItem>
              <para>Click OK, and then OK again to exit the utility.</para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>