---
title: "CommandTypeEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
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
# CommandTypeEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies how a command argument should be interpreted.</para>
    <para>It is important to validate user-supplied <parameterReference>CommandString</parameterReference> values to avoid giving application users the opportunity to inject potentially dangerous commands for ADO to execute.</para>
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
              <legacyBold>adCmdUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Does not specify the command type argument.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCmdText</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Evaluates <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> as a textual definition of a command or stored procedure call.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCmdTable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Evaluates <legacyBold>CommandText</legacyBold> as a table name whose columns are all returned by an internally generated SQL query.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCmdStoredProc</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Evaluates <legacyBold>CommandText</legacyBold> as a stored procedure name.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCmdUnknown</legacyBold>
            </para>
          </TD>
          <TD>
            <para>8</para>
          </TD>
          <TD>
            <para>Default. Indicates that the type of command in the <legacyBold>CommandText</legacyBold> property is not known.</para>
            <para>When the type of command is not known, ADO will make several attempts to interpret the <legacyBold>CommandText</legacyBold>.</para>
            <list class="bullet">
              <listItem>
                <para>
                  <legacyBold>CommandText</legacyBold> is interpreted as a textual definition of a command or stored procedure call. This is the same behavior as <legacyBold>adCmdText</legacyBold>.</para>
              </listItem>
              <listItem>
                <para>
                  <legacyBold>CommandText</legacyBold> is the name of a stored procedure. This is the same behavior as <legacyBold>adCmdStoredProc</legacyBold>.</para>
              </listItem>
              <listItem>
                <para>
                  <legacyBold>CommandText</legacyBold> is interpreted as the name of a table. All columns are returned by an internally generated SQL query. This is the same behavior as <legacyBold>adCmdTable</legacyBold>.</para>
              </listItem>
            </list>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCmdFile</legacyBold>
            </para>
          </TD>
          <TD>
            <para>256</para>
          </TD>
          <TD>
            <para>Evaluates <legacyBold>CommandText</legacyBold> as the file name of a persistently stored <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. Used with <legacyBold>Recordset.</legacyBold><legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> or <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCmdTableDirect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>512</para>
          </TD>
          <TD>
            <para>Evaluates <legacyBold>CommandText</legacyBold> as a table name whose columns are all returned. Used with <legacyBold>Recordset.Open</legacyBold> or <legacyBold>Requery</legacyBold> only. To use the <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink> method, the <legacyBold>Recordset</legacyBold> must be opened with <legacyBold>adCmdTableDirect</legacyBold>.</para>
            <para>This value cannot be combined with the <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink> value <legacyBold>adAsyncExecute</legacyBold>.</para>
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
              <para>AdoEnums.CommandType.UNSPECIFIED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CommandType.TEXT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CommandType.TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CommandType.STOREDPROC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CommandType.UNKNOWN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CommandType.FILE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CommandType.TABLEDIRECT</para>
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
                <link xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType Property</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>