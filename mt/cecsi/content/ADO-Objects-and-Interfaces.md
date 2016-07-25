---
title: "ADO Objects and Interfaces"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0b7e254-c89f-4406-b846-a060ef038c30
caps.latest.revision: 13
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
# ADO Objects and Interfaces
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The relationships between these objects are represented in the <legacyLink xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</legacyLink>.</para>
    <para>Each object can be contained in its corresponding collection. For example, an <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object can be contained in an <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection. For more information, see <legacyLink xlink:href="b5e1d26d-b41d-4e35-8c7c-972426473dfb">ADO Collections</legacyLink> or a specific collection topic.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>
              <externalLink>
                <linkText>IADOCommandConstruction</linkText>
                <linkUri>https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx</linkUri>
              </externalLink>
            </para>
          </TD>
          <TD>
            <para>Used to retrieve the underlying OLEDB Command from an ADOCommand object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="52a5429e-5829-455e-be3b-31f05cbecf2d">ADORecordConstruction</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Constructs an ADO <legacyBold>Record</legacyBold> object from an OLE DB <legacyBold>Row</legacyBold> object in a C/C++ application.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="08386eba-f1f7-4879-8ffd-8733930ecb2f">ADORecordsetConstruction</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Constructs an ADO <legacyBold>Recordset</legacyBold> object from an OLE DB <legacyBold>Rowset</legacyBold> object in a C/C++ application.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="92f5a939-3e1a-4b14-a9dd-90e6ce2dec74">ADOStreamConstruction</link>
            </para>
          </TD>
          <TD>
            <para>Constructs an ADO <legacyBold>Stream</legacyBold> object from an OLE DB <legacyBold>IStream</legacyBold> object in a C/C++ application.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Defines a specific command that you intend to execute against a data source.</para>
            <para>The <legacyBold>Command</legacyBold> object is not safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Represents an open connection to a data source.</para>
            <para>The <legacyBold>Connection</legacyBold> object is safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="ad4ba313-1161-4bc7-b8f6-4083305bc81e">IDSOShapeExtensions Interface</link>
            </para>
          </TD>
          <TD>
            <para>Gets the underlying OLEDB Data Source object for the SHAPE provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Contains details about data access errors that pertain to a single operation involving the provider.</para>
            <para>The <legacyBold>Error</legacyBold> object is not safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Represents a column of data with a common data type.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Represents a parameter or argument associated with a <legacyBold>Command</legacyBold> object based on a parameterized query or stored procedure.</para>
            <para>The <legacyBold>Parameter</legacyBold> object is not safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Represents a dynamic characteristic of an ADO object that is defined by the provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Represents a row of a <legacyBold>Recordset</legacyBold>, or a directory or file in a file system. The <legacyBold>Record</legacyBold> object is safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Represents the set of records from a base table or the results of an executed command. At any time, the <legacyBold>Recordset</legacyBold> object refers to only a single record within the set as the current record.</para>
            <para>The <legacyBold>Recordset</legacyBold> object is safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Represents a binary stream of data.</para>
            <para>The <legacyBold>Stream</legacyBold> object is safe for scripting.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="bfd96a4b-c913-45aa-9e4c-ec86ac364f3a">ADO API Reference</link>
<link xlink:href="b5e1d26d-b41d-4e35-8c7c-972426473dfb">ADO Collections</link>
<link xlink:href="d7b06d72-f792-4328-93a2-5006b9e2c581">ADO Dynamic Properties</link>
<link xlink:href="c97ed131-1a93-463c-9e61-22f029b0c474">ADO Enumerated Constants</link>
<link xlink:href="0ce201c3-6657-4c87-ae81-0d7dc5b5a431">Appendix B: ADO Errors</link>
<link xlink:href="0ded5ad9-8f83-4224-95af-38512783b972">ADO Events</link>
<link xlink:href="a38c5670-ba28-44f3-bd5b-fcb46880e904">ADO Methods</link>
<link xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</link>
<link xlink:href="0ac0d1a7-6c7a-4f4c-b115-428935e0f98b">ADO Properties</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>