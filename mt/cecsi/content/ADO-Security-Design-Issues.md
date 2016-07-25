---
title: "ADO Security Design Issues"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86b83a38-efdf-4831-a6d5-7e470d517d1c
caps.latest.revision: 17
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
# ADO Security Design Issues
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following sections describe security design features in ActiveX Data Objects (ADO) 2.8 and later. These changes were made in ADO 2.8 to improve security. ADO 6.0, which is included in Windows DAC 6.0 in Windows Vista, is functionally equivalent to ADO 2.8, which was included in MDAC 2.8 in Windows XP and Windows Server 2003. This topic provides information about how to best secure your applications in ADO 2.8 or later.</para>
    <alert class="important">
      <para>If you are updating your application from an earlier version of ADO, it is recommended that you test your updated application on a non-production computer before you deploy it to customers. This way, you can ensure you are aware of any compatibility issues before you deploy your updated application.</para>
    </alert>
  </introduction>
  <section>
    <title>Internet Explorer File Access Scenarios</title>
    <content>
      <para>The following features effect how ADO 2.8 and later works when it is used in scripted Web pages in Internet Explorer.</para>
    </content>
    <sections>
      <section>
        <title>Revised and improved security warning message box now used to alert users</title>
        <content>
          <para>For ADO 2.7 and earlier, the following warning message appears when a scripted Web page tries to run ADO code from an untrusted provider:</para>
          <code>This page accesses data on another domain. Do you want to allow this? To 
avoid this message in Internet Explorer, you can add a secure Web site to 
your Trusted Sites zone on the Security tab of the Internet Options dialog 
box.</code>
          <para>For ADO 2.8 and later, the preceding message no longer appears. Instead, the following message appears in this context:</para>
          <code>This Website uses a data provider that may be unsafe. If you trust the 
Website, click OK, otherwise click Cancel.</code>
          <para>The preceding message allows the user to make informed decision, while knowing the consequences for either choice:  </para>
          <list class="bullet">
            <listItem>
              <para>If user trusts the site, clicking OK will allow all disk-safe code (all ADO methods and properties with the exceptions of the disk-accessible APIs described later in this topic) to run and execute in the browser window.</para>
            </listItem>
            <listItem>
              <para>If user does not trust the site, clicking Cancel blocks the ADO code for data access from running and executing in its entirety.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Disk-accessible code limited now to trusted sites</title>
        <content>
          <para>Additional design changes were made in ADO 2.8 that specifically restrict the ability of a limited set of APIs, which might expose the potential to read from or write to files on the local computer. Here are the API methods that have been further restricted for safety when running Internet Explorer:  </para>
          <list class="bullet">
            <listItem>
              <para>For the ADO <legacyBold>Stream</legacyBold> object, if the <legacyLink xlink:href="b18d8d38-7354-4a94-b637-6ac035faa433">LoadFromFile</legacyLink> or <legacyLink xlink:href="8a8594f2-422b-4d2e-94f8-7fe337445900">SaveToFile</legacyLink> methods are used.</para>
            </listItem>
            <listItem>
              <para>For the ADO <legacyBold>Recordset</legacyBold> object, if either the <legacyLink xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save</legacyLink> method or the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method, such as when either the <legacyBold>adCmdFile</legacyBold> option is set or the <legacyLink xlink:href="e75ef0dc-2016-4fcc-8918-23311c0d4e02">Microsoft OLE DB Persistence Provider (MSPersist)</legacyLink> is used.</para>
            </listItem>
          </list>
          <para>For these limited sets of potentially disk-accessible functions, the following behavior occurs for ADO 2.8 and later, if any code that uses these methods is run in Internet Explorer:  </para>
          <list class="bullet">
            <listItem>
              <para>If the site that provided the code was added previously to the Trusted Sites zone list, the code executes in the browser and access is granted to local files.</para>
            </listItem>
            <listItem>
              <para>If the site does not appear in the Trusted Sites zone list, the code is blocked and access to local files is denied. </para>
              <alert class="note">
                <para>In ADO 2.8 and later, the user is not alerted or advised to add sites to the Trusted Sites zone list. Therefore the management of the Trusted Sites list is the responsibility of those who are deploying or supporting Web site–based applications that require access to the local file system.</para>
              </alert>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Access blocked to the ActiveCommand property on Recordset objects</title>
        <content>
          <para>When running in Internet Explorer, ADO 2.8 now blocks access to the <legacyLink xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand</legacyLink> property for an active <legacyBold>Recordset</legacyBold> object and returns an error. The error occurs regardless of whether the page comes from a Web site registered in the Trusted Sites list.</para>
        </content>
      </section>
      <section>
        <title>Changes in handling for OLE DB providers and integrated security</title>
        <content>
          <para>While reviewing ADO 2.7 and earlier versions for potential security issues and concerns, the following scenario was discovered:</para>
          <para>In some instances, OLE DB providers who support the Integrated Security <externalLink><linkText>DBPROP_AUTH_INTEGRATED</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/ms712973.aspx</linkUri></externalLink> property could potentially permit scripted Web pages to reuse the ADO Connection object to connect unintentionally to other servers using the current login credentials of the users. To prevent this, ADO 2.8 and later handle OLE DB providers depending on how they have chosen to provide, or not provide, for integrated security.</para>
          <para>For Web pages that are loaded from sites listed in the Trusted Sites zone list, the following table provides a breakdown of how ADO 2.8 and later manages ADO connections in each case.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>IE settings for user authentication, logon</para>
                </TD>
                <TD>
                  <para>Provider supports "Integrated Security" and UID and PWD are specified (SQLOLEDB)</para>
                </TD>
                <TD>
                  <para>Provider does not support "Integrated Security" (JOLT, MSDASQL, MSPersist)</para>
                </TD>
                <TD>
                  <para>Provider supports "Integrated Security" and it is set to SSPI (no UID/PWD are specified)</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Automatic logon with current username and password</para>
                </TD>
                <TD>
                  <para>Allow connection</para>
                </TD>
                <TD>
                  <para>Allow connection</para>
                </TD>
                <TD>
                  <para>Allow connection</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Prompt for user name and password</para>
                </TD>
                <TD>
                  <para>Allow connection</para>
                </TD>
                <TD>
                  <para>Fail connection</para>
                </TD>
                <TD>
                  <para>Fail connection</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Automatic logon only in Intranet zone</para>
                </TD>
                <TD>
                  <para>Allow connection</para>
                </TD>
                <TD>
                  <para>Prompt user with security warning</para>
                </TD>
                <TD>
                  <para>Prompt user with security warning</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Anonymous logon</para>
                </TD>
                <TD>
                  <para>Allow connection</para>
                </TD>
                <TD>
                  <para>Fail connection</para>
                </TD>
                <TD>
                  <para>Fail connection</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>In the case where a security warning now appears, the message box informs users:</para>
          <code>This Website is using your identity to access a data source. If you trust this Website, click OK, otherwise click Cancel.</code>
          <para>The preceding message allows the user to make a more informed decision and proceed accordingly.</para>
          <alert class="note">
            <para>For untrusted sites (that is, sites not listed in the Trusted Sites zone list), if the provider is also untrusted (as discussed earlier in this section), the user might see two security warnings in a row, a warning about the unsafe provider and a second warning about the attempt to use their identity. If the user clicks OK to the first warning, the Internet Explorer settings and response behavior code described in the preceding table are executed.</para>
          </alert>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Controlling whether password text is returned in ADO connection strings</title>
    <content>
      <para>When you try get the value of the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property on an ADO <legacyBold>Connection</legacyBold> object, the following events occur:  </para>
      <list class="ordered">
        <listItem>
          <para>If the connection is open, an initialization call is then made to the underlying OLE DB provider to get the connection string. </para>
        </listItem>
        <listItem>
          <para>Depending on the setting in the OLE DB provider of the <externalLink><linkText>DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/ms714905.aspx</linkUri></externalLink> property, passwords are included together with other connection string information that is returned.</para>
        </listItem>
      </list>
      <para>For example, if the ADO Connection dynamic property <unmanagedCodeEntityReference>Persist Security Info</unmanagedCodeEntityReference> is set to <languageKeyword>True</languageKeyword>, password information is included in the connection string returned. Otherwise, if the underlying provider has set the property to <languageKeyword>False</languageKeyword> (for example with the SQLOLEDB provider), password information is omitted in the returned connection string.</para>
      <para>If you are using third-party (that is, non-Microsoft) OLE DB providers with your ADO application code, you might check how the <legacyBold>DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO</legacyBold> property is implemented to determine whether inclusion of password information with ADO connection strings is permitted.</para>
    </content>
  </section>
  <section>
    <title>Checking for non-file devices when loading and saving recordsets or streams</title>
    <content>
      <para>For ADO 2.7 and earlier, file input/output operations such as <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> and <legacyLink xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save</legacyLink> that were used to read and write file-based data could in some cases allow a URL or file name to be used that specified a non-disk based file type. For example, LPT1, COM2, PRN.TXT, AUX could be used as an alias for input/output between printers and auxiliary devices on the system using certain </para>
      <para>For ADO 2.8 and later, this functionality has been updated. For opening and saving <legacyBold>Recordset</legacyBold> and <legacyBold>Stream</legacyBold> objects, ADO now performs a file type check to ensure that the input or output device specified in a URL or file name is an actual file.</para>
      <alert class="note">
        <para>File type checking as described in this section only applies for Windows 2000 and later. It does not apply to situations where ADO 2.8 or later is running under earlier Windows releases, such as Windows 98.</para>
      </alert>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>