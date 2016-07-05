---
title: Registry Entries (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
translation.priority.ht: 
  - en-gb
---
# Registry Entries (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When you install the Visual FoxPro ODBC Driver, the installation program updates your system's registry, in the registry key HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, to add a new key called Microsoft Visual FoxPro Driver. Under that key, the values described in the following table are added.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Value name</para>
            </TD>
            <TD>
              <para>Value type</para>
            </TD>
            <TD>
              <para>Value</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>APILevel</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>"1"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ConnectFunctions</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>"YYN"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Driver</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>System path to the vfpodbc.dll file</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DriverODBCVer</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>"02.50"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FileExtns</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>"*.dbf,*.cdx,*.fpt"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FileUsage</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>"1"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setup</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>System path to the vfpodbc.dll file</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQLLevel</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>"0"</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The installation program also adds the key "Visual FoxPro Files", representing the default Visual FoxPro driver, to your system's HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini key. Under this key, the installation program adds the values described in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Value name</para>
            </TD>
            <TD>
              <para>Value type</para>
            </TD>
            <TD>
              <para>Value</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Driver</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>System path to the vfpodbc.dll file</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Each time you add a Visual FoxPro ODBC data source to your ODBC configuration, a new key is added for that data source name. The values for the data source correspond to values you set in the <legacyBold>ODBC Visual FoxPro Setup</legacyBold> dialog box, as listed in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Value name (keyword)</para>
            </TD>
            <TD>
              <para>Value type</para>
            </TD>
            <TD>
              <para>Value</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Collate</para>
            </TD>
            <TD>
              <para>REG_SQ</para>
            </TD>
            <TD>
              <para>Any supported collating sequence</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>User description of data source</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Driver</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>System path to the vfpodbc.dll file</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Exclusive</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>Yes or No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BackgroundFetch</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>Yes or No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SourceDB</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>Path to .DBC file </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SourceType</para>
            </TD>
            <TD>
              <para>REG_SZ</para>
            </TD>
            <TD>
              <para>"DBC" or "DBF"</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>You should not access this information directly; any administration of the registry is handled by the ODBC Administrator when you add, modify, or delete a data source.</para>
      <para>You can use some of these keywords and values as parameters in the <legacyLink xlink:href="10492c8f-3a18-4971-9db8-879e878083b9">SQLDriverConnect</legacyLink> ODBC API function.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>