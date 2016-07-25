---
title: "ActiveConnection Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
caps.latest.revision: 11
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
# ActiveConnection Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates to which <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object the specified <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink>, <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, or <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object currently belongs.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyBold>String</legacyBold> value that contains a definition for a connection if the connection is closed, or a <legacyBold>Variant</legacyBold> containing the current <legacyBold>Connection</legacyBold> object if the connection is open. Default is a null object reference. See the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>ActiveConnection</legacyBold> property to determine the <legacyBold>Connection</legacyBold> object over which the specified <legacyBold>Command</legacyBold> object will execute or the specified <legacyBold>Recordset</legacyBold> will be opened.</para>
    </content>
    <sections>
      <section>
        <title>Command</title>
        <content>
          <para>For <legacyBold>Command</legacyBold> objects, the <legacyBold>ActiveConnection</legacyBold> property is read/write.</para>
          <para>If you attempt to call the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method on a <legacyBold>Command</legacyBold> object before setting this property to an open <legacyBold>Connection</legacyBold> object or valid connection string, an error occurs.</para>
          <para>If a <legacyBold>Connection</legacyBold> object is assigned to the <legacyBold>ActiveConnection</legacyBold> property, the object must be opened. Assigning a closed Connection object causes an error.</para>
        </content>
        <sections>
          <section>
            <title>Note</title>
            <content>
              <para>
                <legacyBold>Microsoft Visual Basic</legacyBold>   Setting the <legacyBold>ActiveConnection</legacyBold> property to <legacyItalic>Nothing</legacyItalic> disassociates the <legacyBold>Command</legacyBold> object from the current <legacyBold>Connection</legacyBold> and causes the provider to release any associated resources on the data source. You can then associate the <legacyBold>Command</legacyBold> object with the same or another <legacyBold>Connection</legacyBold> object. Some providers allow you to change the property setting from one <legacyBold>Connection</legacyBold> to another, without having to first set the property to <legacyItalic>Nothing</legacyItalic>.</para>
              <para>If the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection of the <legacyBold>Command</legacyBold> object contains parameters supplied by the provider, the collection is cleared if you set the <legacyBold>ActiveConnection</legacyBold> property to <legacyItalic>Nothing</legacyItalic> or to another <legacyBold>Connection</legacyBold> object. If you manually create <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> objects and use them to fill the <legacyBold>Parameters</legacyBold> collection of the <legacyBold>Command</legacyBold> object, setting the <legacyBold>ActiveConnection</legacyBold> property to <legacyItalic>Nothing</legacyItalic> or to another <legacyBold>Connection</legacyBold> object leaves the <legacyBold>Parameters</legacyBold> collection intact.</para>
              <para>Closing the <legacyBold>Connection</legacyBold> object with which a <legacyBold>Command</legacyBold> object is associated sets the <legacyBold>ActiveConnection</legacyBold> property to <legacyItalic>Nothing</legacyItalic>. Setting this property to a closed <legacyBold>Connection</legacyBold> object generates an error.</para>
            </content>
          </section>
        </sections>
      </section>
      <section>
        <title>Recordset</title>
        <content>
          <para>For open <legacyBold>Recordset</legacyBold> objects or for <legacyBold>Recordset</legacyBold> objects whose <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink> property is set to a valid <legacyBold>Command</legacyBold> object, the <legacyBold>ActiveConnection</legacyBold> property is read-only. Otherwise, it is read/write.</para>
          <para>You can set this property to a valid <legacyBold>Connection</legacyBold> object or to a valid connection string. In this case, the provider creates a new <legacyBold>Connection</legacyBold> object using this definition and opens the connection. Additionally, the provider may set this property to the new <legacyBold>Connection</legacyBold> object to give you a way to access the <legacyBold>Connection</legacyBold> object for extended error information or to execute other commands.</para>
          <para>If you use the <legacyItalic>ActiveConnection</legacyItalic> argument of the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method to open a <legacyBold>Recordset</legacyBold> object, the <legacyBold>ActiveConnection</legacyBold> property will inherit the value of the argument.</para>
          <para>If you set the <legacyBold>Source</legacyBold> property of the <legacyBold>Recordset</legacyBold> object to a valid <legacyBold>Command</legacyBold> object variable, the <legacyBold>ActiveConnection</legacyBold> property of the <legacyBold>Recordset</legacyBold> inherits the setting of the <legacyBold>Command</legacyBold> object's <legacyBold>ActiveConnection</legacyBold> property.</para>
          <alert class="note">
            <para>               <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Recordset</legacyBold> object, this property can be set only to a connection string or (in Microsoft Visual Basic or Visual Basic, Scripting Edition) to <legacyItalic>Nothing</legacyItalic>.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Record</title>
        <content>
          <para>This property is read/write when the <legacyBold>Record</legacyBold> object is closed, and may contain a connection string or reference to an open <legacyBold>Connection</legacyBold> object. This property is read-only when the <legacyBold>Record</legacyBold> object is open, and contains a reference to an open <legacyBold>Connection</legacyBold> object.</para>
          <para>A <legacyBold>Connection</legacyBold> object is created implicitly when the <legacyBold>Record</legacyBold> object is opened from a URL. Open the <legacyBold>Record</legacyBold> with an existing, open <legacyBold>Connection</legacyBold> object by assigning the <legacyBold>Connection</legacyBold> object to this property, or using the <legacyBold>Connection</legacyBold> object as a parameter in the <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open</legacyLink> method call. If the <legacyBold>Record</legacyBold> is opened from an existing <legacyBold>Record</legacyBold> or <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, then it is automatically associated with that <legacyBold>Record</legacyBold> or <legacyBold>Recordset</legacyBold> object's <legacyBold>Connection</legacyBold> object.</para>
          <alert class="note">
            <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
          </alert>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="dade4531-0bcc-4a52-8f86-b110ba2a3f9d">Visual Basic Example</link>
<link xlink:href="0d9917c4-9ef0-4d7a-b4ce-4f1fa6ce1817">Visual C++ Example</link>
<link xlink:href="69a4a219-8d52-401b-9e92-2ef415f68b05">Visual J++Example</link>
<link xlink:href="ea74e2a3-c965-43aa-9076-26a084b48ad8">JScriptExample</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>