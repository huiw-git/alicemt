---
title: "DataControl Error Codes"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 293df9d5-e1a2-406d-9107-07bf7cdc6f96
caps.latest.revision: 9
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
# DataControl Error Codes
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object error codes. The positive decimal translation of the low two bytes, the negative decimal translation of the full error code, and the hexadecimal values are shown.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>RDS.DataControl error codes</para>
          </TD>
          <TD>
            <para>Number</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_AsyncPending</legacyBold>             </para>
          </TD>
          <TD>
            <para>4107 -2146824175 0x800A1011</para>
          </TD>
          <TD>
            <para>Operation cannot be performed while async operation is pending.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_BadInlineTablegram</legacyBold>             </para>
          </TD>
          <TD>
            <para>4105 -2146824183 0x800A1009</para>
          </TD>
          <TD>
            <para>Bad inline tablegram.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_CantConnect</legacyBold>             </para>
          </TD>
          <TD>
            <para>4099 -2146824189 0x800A1003</para>
          </TD>
          <TD>
            <para>Cannot connect to server.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_CantCreateObject</legacyBold>             </para>
          </TD>
          <TD>
            <para>4100 -2146824188 0x800A1004</para>
          </TD>
          <TD>
            <para>Business object cannot be created.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_CantFindDataspace</legacyBold>             </para>
          </TD>
          <TD>
            <para>4102 -2146824186 0x800A1006</para>
          </TD>
          <TD>
            <para>Dataspace property is not valid.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_CantInvokeMethod</legacyBold>             </para>
          </TD>
          <TD>
            <para>4101 -2146824187 0x800A1005</para>
          </TD>
          <TD>
            <para>Method cannot be invoked on business object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_CrossDomainWarning</legacyBold>             </para>
          </TD>
          <TD>
            <para>4112 -2146824170 0x800A1016</para>
          </TD>
          <TD>
            <para>This page accesses data on another domain. Do you want to allow this? To avoid this message in Internet Explorer, you can add a secure Web site to your Trusted Sites zone on the <legacyBold>Security</legacyBold> tab of the <legacyBold>Internet Options</legacyBold> dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_InvalidADCClientVersion</legacyBold>             </para>
          </TD>
          <TD>
            <para>4106 -2146824176 0x800A1010</para>
          </TD>
          <TD>
            <para>Invalid RDS Client Version — Client is newer than server.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_INVALIDARG</legacyBold>             </para>
          </TD>
          <TD>
            <para>5376 -2147019520 0x80071500</para>
          </TD>
          <TD>
            <para>One or more arguments are invalid.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_InvalidBindings</legacyBold>             </para>
          </TD>
          <TD>
            <para>4097 -2146824191 0x800A1001</para>
          </TD>
          <TD>
            <para>Error in bindings property.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_InvalidParam</legacyBold>             </para>
          </TD>
          <TD>
            <para>4110 -2146824172 0x800A1014</para>
          </TD>
          <TD>
            <para>One or more arguments are invalid.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_NOINTERFACE</legacyBold>             </para>
          </TD>
          <TD>
            <para>5377 -2147019519 0x80071501</para>
          </TD>
          <TD>
            <para>No such interface is supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_NotReentrant</legacyBold>             </para>
          </TD>
          <TD>
            <para>4111 -2146824171 0x800A1015</para>
          </TD>
          <TD>
            <para>Request cannot be executed while the event handler is still processing.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_ObjectNotSafe</legacyBold>             </para>
          </TD>
          <TD>
            <para>4103 -2146824185 0x800A1007</para>
          </TD>
          <TD>
            <para>Safety settings on this computer prohibit creation of business object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_RecordsetNotOpen</legacyBold>             </para>
          </TD>
          <TD>
            <para>4109 -2146824173 0x800A1013</para>
          </TD>
          <TD>
            <para>               <legacyBold>Recordset</legacyBold> is not open.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_ResetInvalidField</legacyBold>             </para>
          </TD>
          <TD>
            <para>4108 -2146824174 0x800A1012</para>
          </TD>
          <TD>
            <para>Column specified in <legacyBold>SortColumn</legacyBold> or <legacyBold>FilterColumn</legacyBold> does not exist.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_RowsetNotUpdateable</legacyBold>             </para>
          </TD>
          <TD>
            <para>4104 -2146824184 0x800A1008</para>
          </TD>
          <TD>
            <para>Rowset not updateable.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_UnexpectedError</legacyBold>             </para>
          </TD>
          <TD>
            <para>4351 -2146823937 0x800A10FF</para>
          </TD>
          <TD>
            <para>Unexpected error.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_UpdatesFailed</legacyBold>             </para>
          </TD>
          <TD>
            <para>4098 -2146824190 0x800A1002</para>
          </TD>
          <TD>
            <para>Unable to update database.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>IDS_URLMONNotFound</legacyBold>             </para>
          </TD>
          <TD>
            <para>4119 -2146824169 0x800A1017</para>
          </TD>
          <TD>
            <para>DataControl <legacyBold>URL</legacyBold> property requires the system file Urlmon.dll, which cannot be found.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>