---
title: Setting Tracing Options
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44404a79-b716-4bc1-9ffb-70cd8239d237
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Tracing Options
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>Tracing</legacyBold> tab of the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box enables you to configure the way ODBC function calls are traced.</para>
  </introduction>
  <section>
    <title>How Tracing Works</title>
    <content>
      <para>When you start tracing from the <legacyBold>Tracing</legacyBold> tab, the Driver Manager will log all ODBC function calls for all subsequently run applications. ODBC function calls from applications that are running before tracing is started are not logged. ODBC function calls are recorded in a log file that you specify.</para>
      <para>Tracing stops only after you click <legacyBold>Stop Tracing Now</legacyBold>. Remember that while tracing is on, the log file continues to increase and that this affects the performance of all your ODBC applications.</para>
      <para>For more information about tracing, see <legacyLink xlink:href="77ed4c6c-d976-4eb2-8526-a12697b0ef83">Tracing</legacyLink>.</para>
    </content>
    <sections>
      <section>
        <title>Changes in ODBC tracing</title>
        <content>
          <para>Prior to MDAC 2.7 SP2, ODBC tracing was only allowed to occur on a machine-wide basis, in which trace captures exposed details about all ODBC applications running under any identities. This included tracing for ODBC-related activity that might occur for processes created or run on behalf of other local user accounts and built-in security principals such as the Local Service and Network Service.</para>
          <para>By default, ODBC tracing now uses per-user mode. If you are a local administrator, however, you can still enable machine-wide tracing by using the ODBC Data Source Administrator.</para>
          <para>To configure the ODBC tracing mode:  </para>
          <list class="ordered">
            <listItem>
              <para>If it is necessary, log on using an account that has membership in the Local Administrators' group.</para>
            </listItem>
            <listItem>
              <para>From Administrative Tools, open the ODBC Data Source Administrator.</para>
            </listItem>
            <listItem>
              <para>Click the <legacyBold>Tracing</legacyBold> tab.</para>
            </listItem>
            <listItem>
              <para>Configure the tracing mode using the <legacyBold>Machine-Wide tracing for all user identities</legacyBold> check box:</para>
            </listItem>
            <listItem>
              <para>To enable machine-wide tracing, select the check box.</para>
            </listItem>
            <listItem>
              <para>To return to per-user tracing, clear the check box.</para>
            </listItem>
            <listItem>
              <para>Click <legacyBold>Apply</legacyBold>.</para>
            </listItem>
          </list>
          <alert class="note">
            <para>If you have already started tracing in one mode, you have to stop tracing and switch to the other mode for the mode to be changed successfully. </para>
          </alert>
          <alert class="important">
            <para>Machine-wide tracing should only be enabled when it is needed; otherwise, it should be left turned off. </para>
          </alert>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Visual Studio Analyzer Tracing</title>
    <content>
      <alert class="important">
        <para>Support for Visual Studio Analyzer was removed beginning in Windows 8 (Visual Studio Analyzer was only included in older versions of Visual Studio.). For an alternative troubleshooting mechanism, use BID tracing.</para>
      </alert>
      <para>Visual Studio® Analyzer Tracing provides performance and debugging information about the ODBC layer. All outgoing events will be fired at the top-level interface to present as accurate a picture as possible regarding time spent in ODBC components. Visual Studio Analyzer Tracing requires any event source to register when the source is set up. For more information about this kind of tracing, see the Visual Studio documentation.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>