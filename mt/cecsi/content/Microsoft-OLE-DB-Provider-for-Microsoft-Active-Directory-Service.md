---
title: "Microsoft OLE DB Provider for Microsoft Active Directory Service"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
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
# Microsoft OLE DB Provider for Microsoft Active Directory Service
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Active Directory Service Interfaces (ADSI) Provider allows ADO to connect to heterogeneous directory services through ADSI. This gives ADO applications read-only access to the Microsoft Windows NT 4.0 and Microsoft Windows 2000 directory services, in addition to any LDAP-compliant directory service and Novell Directory Services. ADSI itself is based on a provider model, so that if there is a new provider giving access to another directory, the ADO application will be able to access it seamlessly. The ADSI provider is free-threaded and Unicode enabled.</para>
  </introduction>
  <section>
    <title>Connection String Parameters</title>
    <content>
      <para>To connect to this provider, set the <legacyBold>Provider</legacyBold> argument of the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to the following:</para>
      <code>ADSDSOObject</code>
      <para>Reading the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property will return this string as well.</para>
    </content>
  </section>
  <section>
    <title>Typical Connection String</title>
    <content>
      <para>A typical connection string for this provider is as follows:</para>
      <code>"Provider=ADSDSOObject;User ID=<legacyItalic>MyUserID</legacyItalic>;Password=<legacyItalic>MyPassword</legacyItalic>;"</code>
      <para>The string consists of the following keywords.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Keyword</para>
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
                <legacyBold>Provider</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the OLE DB Provider for Active Directory Service. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>User ID</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user name. If this keyword is omitted, the current logon is used.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Password</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user password. If this keyword is omitted. Then the current logon is used.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Command Text</title>
    <content>
      <para>A four-part command text string is recognized by the provider in the following syntax:</para>
      <code>"Root; Filter; Attributes[; Scope]"</code>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
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
                <legacyItalic>Root</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Indicates the <legacyBold>ADsPath</legacyBold> object from which to start the search (that is, the root of the search).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Filter</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Indicates the search filter in the RFC 1960 format.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Attributes</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Indicates a comma-delimited list of attributes to be returned.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyItalic>Scope</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Optional. A <legacyBold>String</legacyBold> that specifies the scope of the search. Can be one of the following:</para>
              <list class="bullet">
                <listItem>
                  <para>Base — Search only the base object (root of the search).</para>
                </listItem>
                <listItem>
                  <para>OneLevel — Search only one level.</para>
                </listItem>
                <listItem>
                  <para>Subtree — Search the whole subtree.</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For example:</para>
      <code>"&lt;LDAP://DC=ArcadiaBay,DC=COM&gt;;(objectClass=*);sn, givenName; subtree"</code>
      <para>The provider also supports SQL SELECT for command text. For example:</para>
      <code>"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE 
objectClass='user' AND objectCategory='Person'"</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The provider does not accept stored procedure calls or simple table names (for example, the <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink> property will always be <legacyBold>adCmdText</legacyBold>). See the Active Directory Service Interfaces documentation for a more thorough description of the command text elements.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Recordset Behavior</title>
    <content>
      <para>The following tables list the features available on a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object opened by using this provider. Only the static cursor type (<legacyBold>adOpenStatic</legacyBold>) is available.</para>
      <para>For more information about <legacyBold>Recordset</legacyBold> behavior for your provider configuration, run the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method and enumerate the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection of the <legacyBold>Recordset</legacyBold> to determine whether provider-specific dynamic properties are present.</para>
      <para>
        <embeddedLabel>Availability of standard ADO Recordset properties:</embeddedLabel>
      </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Property</para>
            </TD>
            <TD>
              <para>Availability</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink>
              </para>
            </TD>
            <TD>
              <para>always <legacyBold>adUseServer</legacyBold></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink>
              </para>
            </TD>
            <TD>
              <para>always <legacyBold>adOpenStatic</legacyBold></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode</legacyLink>
              </para>
            </TD>
            <TD>
              <para>always <legacyBold>adEditNone</legacyBold></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="390c8abf-133e-40da-8b99-8f748a983e4f">MarshalOptions</legacyLink>
              </para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>
        <embeddedLabel>Availability of standard ADO Recordset methods:</embeddedLabel>
      </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Method</para>
            </TD>
            <TD>
              <para>Available?</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveLast</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For more information about ADSI and the specifics of the provider, refer to the Active Directory Service Interfaces documentation or visit the ADSI Web page.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType Property</link>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>