---
title: "CubeDef Object (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
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
# CubeDef Object (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a cube from a multidimensional schema, containing a set of related dimensions.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>With the collections and properties of a <legacyBold>CubeDef</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify a <legacyBold>CubeDef</legacyBold> with the <legacyLink xlink:href="4a04380b-51dc-4aaf-8d25-123cdd589641">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return a string that describes the cube with the <legacyLink xlink:href="6d626d35-0bf3-4f24-9934-ad9c9c91273a">Description</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the dimensions that make up the cube with the <legacyLink xlink:href="eaf6f4e7-2ea0-49a3-89ee-e219e025257c">Dimensions</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Obtain additional information about the <legacyBold>CubeDef </legacyBold>with the standard ADO <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
      </list>
      <para>The <legacyBold>Properties</legacyBold> collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>CatalogName</para>
            </TD>
            <TD>
              <para>The name of the catalog to which this cube belongs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CreatedOn</para>
            </TD>
            <TD>
              <para>Date and time of cube creation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CubeGUID</para>
            </TD>
            <TD>
              <para>Cube GUID.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CubeName</para>
            </TD>
            <TD>
              <para>The name of the cube.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CubeType</para>
            </TD>
            <TD>
              <para>The type of the cube.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DataUpdatedBy</para>
            </TD>
            <TD>
              <para>User ID of the person doing the last data update.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>A meaningful description of the cube.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LastSchemaUpdate</para>
            </TD>
            <TD>
              <para>Date and time of last schema update.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SchemaName</para>
            </TD>
            <TD>
              <para>The name of the schema to which this cube belongs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SchemaUpdatedBy</para>
            </TD>
            <TD>
              <para>User ID of the person doing the last schema update.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="5dac737a-b77e-47d3-9228-cd52b7a97b0a">Properties, Methods, and Events</legacyLink> </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="4d72a912-ef53-4989-9fca-214937574116">VBScript Example</link>
<link xlink:href="11f6f896-d69c-44a4-94cd-d54c93140e4a">Catalog Object</link>
<link xlink:href="c79a5e36-71fd-44c4-948d-d6a7a89bb3b5">CubeDefs Collection</link>
<link xlink:href="eaf6f4e7-2ea0-49a3-89ee-e219e025257c">Dimensions Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>