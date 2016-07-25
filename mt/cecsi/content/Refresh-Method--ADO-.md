---
title: "Refresh Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
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
# Refresh Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Updates the objects in a collection to reflect objects available from, and specific to, the provider.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>collection</parameterReference>.<legacyBold>Refresh</legacyBold></legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>The <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method accomplishes different tasks depending on the collection from which you call it. </para>
    </content>
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <title>Parameters</title>
            <content>
              <para>Using the <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method on the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection of a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object retrieves provider-side parameter information for the stored procedure or parameterized query specified in the <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object. The collection will be empty for providers that do not support stored procedure calls or parameterized queries.</para>
              <para>You should set the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property of the <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object to a valid <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object, the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property to a valid command, and the <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink> property to <legacyBold>adCmdStoredProc</legacyBold> before calling the <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method.</para>
              <para>If you access the <unmanagedCodeEntityReference>Parameters</unmanagedCodeEntityReference> collection before calling the <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method, ADO will automatically call the method and populate the collection for you.</para>
              <alert class="note">
                <para>If you use the <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method to obtain parameter information from the provider and it returns one or more variable-length data type <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> objects, ADO may allocate memory for the parameters based on their maximum potential size, which will cause an error during execution. You should explicitly set the <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink> property for these parameters before calling the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method to prevent errors.</para>
              </alert>
            </content>
          </section>
          <section>
            <title>Fields</title>
            <content>
              <para>Using the <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method on the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection has no visible effect. To retrieve changes from the underlying database structure, you must use either the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method or, if the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object does not support bookmarks, the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink> method.</para>
            </content>
          </section>
          <section>
            <title>Properties</title>
            <content>
              <para>Using the <unmanagedCodeEntityReference>Refresh</unmanagedCodeEntityReference> method on a <unmanagedCodeEntityReference>Properties</unmanagedCodeEntityReference> collection of some objects populates the collection with the dynamic properties that the provider exposes. These properties provide information about functionality specific to the provider, beyond the built-in properties ADO supports.</para>
            </content>
          </section>
        </sections>
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
                <legacyLink xlink:href="072fb21a-ec0f-4b02-9022-1cef3ad4bfff">Axes Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="c79a5e36-71fd-44c4-948d-d6a7a89bb3b5">CubeDefs Collection</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="eaf6f4e7-2ea0-49a3-89ee-e219e025257c">Dimensions Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="bef0fcb1-8060-4faa-84f0-3d52e9c4526f">Hierarchies Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="184cf536-455c-42be-bf1c-a5c25bade961">Indexes Collection</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="fed8684a-b428-4ee4-8f8d-928abe4ad9ad">Levels Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="3a647cde-efdc-4394-b1b9-8cbb1b9d689f">Members Collection</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="5b9e7545-cf30-464d-80ef-5c99c8306bab">Positions Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users Collection</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</legacyLink>
              </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="f5375fa1-4711-4f7e-9ba4-54c427f71325">Visual Basic Example</link>
<link xlink:href="3dc3443b-a1b0-4fbd-908a-6e274dec981c">Visual C++ Example</link>
<link xlink:href="c0fbf728-0ccb-468d-be1e-c09dad9ffddb">Visual VJ++ Example</link>
<link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property</link>
<link xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh Method (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>