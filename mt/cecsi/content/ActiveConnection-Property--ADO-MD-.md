---
title: "ActiveConnection Property (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
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
# ActiveConnection Property (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates to which ADO <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object the current cellset or catalog currently belongs.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Variant</languageKeyword> that contains a string defining a connection or <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object. The default is empty.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>You can set this property to a valid ADO <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object or to a valid connection string. When this property is set to a connection string, the provider creates a new <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object using this definition and opens the connection.</para>
      <para>If you use the <parameterReference>ActiveConnection</parameterReference> argument of the <legacyLink xlink:href="a87d8080-a238-45e5-bc80-9a8625b3810f">Open</legacyLink> method to open a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object, the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property will inherit the value of the argument.</para>
      <para>Setting the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property of a <legacyLink xlink:href="11f6f896-d69c-44a4-94cd-d54c93140e4a">Catalog</legacyLink> object to <legacyBold>Nothing</legacyBold> releases the associated data, including data in the <legacyLink xlink:href="c79a5e36-71fd-44c4-948d-d6a7a89bb3b5">CubeDefs</legacyLink> collection and any related <legacyLink xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">Dimension</legacyLink>, <legacyLink xlink:href="034af340-ac79-494e-ba5e-2b57da1cb9de">Hierarchy</legacyLink>, <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink>, and <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> objects. Closing a <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object that was used to open a <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference> has the same effect as setting the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property to <legacyBold>Nothing</legacyBold>.</para>
      <para>Changing the default database of the connection referenced by the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property of a <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference> object invalidates the contents of the <unmanagedCodeEntityReference>Catalog</unmanagedCodeEntityReference>.</para>
      <para>An error will occur if you attempt to change the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property for an open <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference> object.</para>
      <alert class="note">
        <para>In Visual Basic, remember to use the <legacyBold>Set</legacyBold> keyword when setting the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property to a <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object. If you omit the <legacyBold>Set</legacyBold> keyword, you will actually be setting the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property equal to the <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object's default property, <unmanagedCodeEntityReference>ConnectionString</unmanagedCodeEntityReference>. The code will work; however, you will create an additional connection to the data source, which may have negative performance implications.</para>
      </alert>
      <para>When using the MSOLAP data provider, set the data source in a connection string to a server name and set the initial catalog to the name of a catalog from the data source. To connect to a cube file that is disconnected from a server, set the location to the full path to the .CUB file. In either case, set the provider to the provider name. For example, the following string uses the MSOLAP Provider to connect to a catalog named Bobs Video Store on a server named <userInput>Servername</userInput>:</para>
      <code>"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"</code>
      <para>The following string connects to a local cube file at the location C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub:</para>
      <code>"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"</code>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="11f6f896-d69c-44a4-94cd-d54c93140e4a">Catalog Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2666ad1c-b48e-4b2c-b269-5a9f4e4a7810">Visual Basic Example</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="a87d8080-a238-45e5-bc80-9a8625b3810f">Open Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>