---
title: "Microsoft Data Shaping Service for OLE DB (ADO Service Provider)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 523009ce-e01b-4e2d-a7df-816d7688aff0
caps.latest.revision: 16
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
# Microsoft Data Shaping Service for OLE DB (ADO Service Provider)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, applications should use XML.</para>
    </alert>
    <para>The Microsoft Data Shaping Service for OLE DB service provider supports the construction of hierarchical (shaped) <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects from a data provider.</para>
  </introduction>
  <section>
    <title>Provider Keyword</title>
    <content>
      <para>To invoke the Data Shaping Service for OLE DB, specify the following keyword and value in the connection string.</para>
      <code>"Provider=<codeFeaturedElement>MSDataShape</codeFeaturedElement>"</code>
    </content>
  </section>
  <section>
    <title>Dynamic Properties</title>
    <content>
      <para>When this service provider is invoked, the following dynamic properties are added to the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection of the<legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d"> Connection</legacyLink> object.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Dynamic Property Name</para>
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
                <legacyBold>Unique Reshape Names</legacyBold> </para>
            </TD>
            <TD>
              <para>Indicates whether <legacyBold>Recordset </legacyBold>objects with duplicate values for their <legacyBold>Reshape Name</legacyBold> properties are allowed. If this dynamic property is <legacyBold>True</legacyBold> and a new <legacyBold>Recordset</legacyBold> is created with the same user-specified reshape name as an existing <legacyBold>Recordset</legacyBold>, then the new <legacyBold>Recordset</legacyBold> object's reshape name is modified to make it unique. If this property is <languageKeyword>False</languageKeyword> and a new <legacyBold>Recordset</legacyBold> is created with the same user-specified reshape name as the existing <legacyBold>Recordset</legacyBold>, both <legacyBold>Recordset</legacyBold> objects will have the same reshape name. Therefore, neither <legacyBold>Recordset</legacyBold> can be reshaped as long as both recordsets exist.</para>
              <para>The default value of the property is <legacyBold>False</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Data Provider</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Indicates the name of the provider that will supply rows to be shaped. This value can be NONE if a provider will not be used to supply rows.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>You can also set writable dynamic properties by specifying their names as keywords in the connection string. For example, in Microsoft Visual Basic, set the <legacyBold>Data Provider</legacyBold> dynamic property to "MSDASQL" by specifying:</para>
      <code>Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"</code>
      <para>You can also set or retrieve a dynamic property by specifying its name as the index to the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> property. For example, the following code example gets and prints the current value of the <legacyBold>Data Provider</legacyBold> dynamic property, then sets a new value if cn.DataProvider has been set to "MSDataShape" (either directly or indirectly through the connection string) and the connection has not been opened:</para>
      <code>Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"</code>
      <alert class="note">
        <para>The dynamic property, <unmanagedCodeEntityReference>Data Provider</unmanagedCodeEntityReference>, can be set only on an unopened <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object. Once the connection is opened, the <unmanagedCodeEntityReference>Data Provider</unmanagedCodeEntityReference> property becomes read-only.</para>
      </alert>
      <para>For more information about data shaping, see <legacyLink xlink:href="4cb5fd29-4e56-46ac-ae48-a6771c321c0c">Data Shaping</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>