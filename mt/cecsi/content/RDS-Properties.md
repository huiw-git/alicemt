---
title: "RDS Properties"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4e04cbd-21fc-44a1-9f21-49aa68746934
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
# RDS Properties
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the database name from which the query and update operations are run.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="62a4fd88-afc3-4f1f-b978-40710a30c4e9">ExecuteOptions (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates whether asynchronous execution is enabled.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="7b2e254a-9354-4541-bc98-bb185276388f">FetchOptions (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the type of asynchronous fetching.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="0a5473e8-8ce6-4518-83fb-4920b827e285">FilterColumn (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the column on which to evaluate the filter criteria.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="24eb03ba-ccfd-4353-b6af-03586b2da6fd">FilterCriterion (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the evaluation operator to use in the filter value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="28f17186-b842-4cf9-b320-a9bb941c481b">FilterValue (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the value to filter records.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the name of a server-side customization program (<legacyItalic>handler</legacyItalic>) that extends the functionality of the <legacyBold>RDSServer.DataFactory</legacyBold>, and any parameters used by the <legacyItalic>handler</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549">InternetTimeout (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the number of milliseconds to wait before a request times out.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="5be75bc7-1171-4440-a37e-c8cc6b5cd865">ReadyState (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the progress of a <legacyBold>DataControl</legacyBold> object as it fetches data into its <legacyBold>Recordset</legacyBold> object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="a29e3fb9-306d-497a-9a59-1856a914e5e9">Recordset and SourceRecordset (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the <legacyBold>Recordset</legacyBold> object returned from a custom business object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="d2727ce7-da9f-4271-ae3c-9334ef477c14">Server (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the Internet Information Services (IIS) name and communication protocol.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="f6f80f67-f0fb-4e63-a5f5-8fdf312aac63">SortColumn (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates by which column to sort the records.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2">SortDirection (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates whether a sort order is ascending or descending.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates the query string used to retrieve the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="8c56b233-1be8-442c-8d0e-a4c96465bc99">URL (RDS)</legacyLink>           </para>
          </TD>
          <TD>
            <para>Indicates a string that contains a relative or absolute URL.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerOrientationDocument>