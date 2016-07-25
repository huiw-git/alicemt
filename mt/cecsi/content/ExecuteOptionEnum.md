---
title: "ExecuteOptionEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
caps.latest.revision: 10
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
# ExecuteOptionEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies how a provider should execute a command.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Constant</para>
          </TD>
          <TD>
            <para>Value</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>adAsyncExecute</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10</para>
          </TD>
          <TD>
            <para>Indicates that the command should execute asynchronously.</para>
            <para>This value cannot be combined with the <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> value <legacyBold>adCmdTableDirect</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adAsyncFetch</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x20</para>
          </TD>
          <TD>
            <para>Indicates that the remaining rows after the initial quantity specified in the <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property should be retrieved asynchronously.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adAsyncFetchNonBlocking</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x40</para>
          </TD>
          <TD>
            <para>Indicates that the main thread never blocks while retrieving. If the requested row has not been retrieved, the current row automatically moves to the end of the file.</para>
            <para>If you open a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> from a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> containing a persistently stored <legacyBold>Recordset</legacyBold>, <legacyBold>adAsyncFetchNonBlocking</legacyBold> will not have an effect; the operation will be synchronous and blocking.</para>
            <para>
              <legacyBold>adAsynchFetchNonBlocking</legacyBold> has no effect when the <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">adCmdTableDirect</legacyLink> option is used to open the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adExecuteNoRecords</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x80</para>
          </TD>
          <TD>
            <para>Indicates that the command text is a command or stored procedure that does not return rows (for example, a command that only inserts data). If any rows are retrieved, they are discarded and not returned.</para>
            <para>
              <legacyBold>adExecuteNoRecords</legacyBold> can only be passed as an optional parameter to the <legacyBold>Command</legacyBold> or <legacyBold>Connection</legacyBold> <legacyBold>Execute</legacyBold> method.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adExecuteStream</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x400</para>
          </TD>
          <TD>
            <para>Indicates that the results of a command execution should be returned as a stream. </para>
            <para>
              <legacyBold>adExecuteStream</legacyBold> can only be passed as an optional parameter to the <legacyBold>Command</legacyBold> <legacyBold>Execute</legacyBold> method.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adExecuteRecord</legacyBold>
            </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>Indicates that the <legacyBold>CommandText</legacyBold> is a command or stored procedure that returns a single row which should be returned as a <legacyBold>Record</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adOptionUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Indicates that the command is unspecified.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>AdoEnums.ExecuteOption.ASYNCEXECUTE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ExecuteOption.ASYNCFETCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ExecuteOption.ASYNCFETCHNONBLOCKING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ExecuteOption.NORECORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ExecuteOption.UNSPECIFIED</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>