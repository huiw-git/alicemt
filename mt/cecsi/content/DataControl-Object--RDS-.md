---
title: "DataControl Object (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
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
# DataControl Object (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Binds a data query <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to one or more controls (for example, a text box, grid control, or combo box) to display the <legacyBold>Recordset</legacyBold> data on a Web page.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"
   &lt;PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;"&gt;
   &lt;PARAM NAME="Server" VALUE="http://awebsrvr"&gt;
   &lt;PARAM NAME="SQL" VALUE="QueryText"&gt;
&lt;/OBJECT&gt;</legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>The class ID for the <legacyBold>RDS.DataControl</legacyBold> object is BD96C556-65A3-11D0-983A-00C04FC29E33.</para>
      <alert class="note">
        <para>If you get an error that an <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink> or <legacyBold>RDS.DataControl</legacyBold> object does not load, make sure that you are using the correct class ID. The class IDs for these objects have changed from version 1.0 and 1.1. Also, be aware that even nullable columns must be set when you use the <legacyBold>RDS DataControl</legacyBold> object.</para>
      </alert>
      <para>For a basic scenario, you need to set only the <legacyBold>SQL</legacyBold>, <legacyBold>Connect</legacyBold>, and <legacyBold>Server</legacyBold> properties of the <legacyBold>RDS.DataControl</legacyBold> object, which will automatically call the default business object, <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink>.</para>
      <para>All the properties in the <legacyBold>RDS.DataControl</legacyBold> are optional because custom business objects can replace their functionality.</para>
      <alert class="note">
        <para>If you query for multiple results, only the first <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> is returned. If multiple result sets are needed, assign each to its own <legacyBold>DataControl</legacyBold>. An example of a query for multiple results could be the following: <codeInline>"Select * from Authors, Select * from Topics"</codeInline></para>
      </alert>
      <para>Adding "DFMode=20;" to your connection string when you use the <legacyBold>RDS.DataControl</legacyBold> object can improve the performance of your server when you update data. With this setting, the <legacyBold>RDSServer.DataFactory</legacyBold> object on the server uses a less resource-intensive mode. However, the following features are not available in this configuration:  </para>
      <list class="bullet">
        <listItem>
          <para>Using parameterized queries.</para>
        </listItem>
        <listItem>
          <para>Getting parameter or column information before calling the <legacyBold>Execute</legacyBold> method.</para>
        </listItem>
        <listItem>
          <para>Setting <legacyBold>Transact Updates</legacyBold> to <legacyBold>True</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>Getting row status.</para>
        </listItem>
        <listItem>
          <para>Calling the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Refreshing (explicitly or automatically) via the <legacyLink xlink:href="8a3bb608-66d7-4128-a3ef-84cb0556de0d">Update Resync</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Setting <legacyBold>Command</legacyBold> or <legacyLink xlink:href="a29e3fb9-306d-497a-9a59-1856a914e5e9">Recordset</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Using <legacyBold>adCmdTableDirect</legacyBold>.</para>
        </listItem>
      </list>
      <para>The <legacyBold>RDS.DataControl</legacyBold> object runs in asynchronous mode by default. If you require synchronous execution for your application, set the <legacyLink xlink:href="62a4fd88-afc3-4f1f-b978-40710a30c4e9">ExecuteOptions</legacyLink> parameter equal to <legacyBold>adcExecSync</legacyBold> and the <legacyLink xlink:href="7b2e254a-9354-4541-bc98-bb185276388f">FetchOptions</legacyLink> parameter equal to <legacyBold>adcFetchUpFront</legacyBold>, as shown in the following example.</para>
      <code>&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" 
    ID="DataControl"
   &lt;PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;"&gt;
   &lt;PARAM NAME="Server" VALUE="http://awebsrvr"&gt;
   &lt;PARAM NAME="SQL" VALUE="QueryText"&gt;
<codeFeaturedElement>   &lt;PARAM NAME="ExecuteOptions" VALUE="1"&gt;   &lt;PARAM NAME="FetchOptions" VALUE="1"&gt;</codeFeaturedElement>
&lt;/OBJECT&gt;</code>
      <para>Use one <legacyBold>RDS.DataControl</legacyBold> object to link the results of a single query to one or more visual controls. For example, suppose you code a query requesting customer data such as Name, Residence, Place of Birth, Age, and Priority Customer Status. You can use a single <legacyBold>RDS.DataControl</legacyBold> object to display a customer's Name, Age, and Region in three separate text boxes; Priority Customer Status in a check box; and all the data in a grid control.</para>
      <para>Use different <legacyBold>RDS.DataControl</legacyBold> objects to link the results of multiple queries to different visual controls. For example, suppose you use one query to obtain information about a customer, and a second query to obtain information about merchandise that the customer has purchased. You want to display the results of the first query in three text boxes and one check box, and the results of the second query in a grid control. If you use the default business object (<legacyBold>RDSServer.DataFactory</legacyBold>), you must do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Add two <legacyBold>RDS.DataControl</legacyBold> objects to your Web page.</para>
        </listItem>
        <listItem>
          <para>Write two queries, one for each <legacyBold>SQL</legacyBold> property of the two <legacyBold>RDS.DataControl</legacyBold> objects. One <legacyBold>RDS.DataControl </legacyBold>object will contain an SQL query requesting customer information; the second will contain a query requesting a list of merchandise the customer has purchased.</para>
        </listItem>
        <listItem>
          <para>In the OBJECT tags of each bound control, specify the DATAFLD value to set the values for the data that you want to display in each visual control.</para>
        </listItem>
      </list>
      <para>There is no count restriction on the number of <legacyBold>RDS.DataControl</legacyBold> objects that you can embed by using OBJECT tags on a single Web page.</para>
      <para>When you define the <legacyBold>RDS.DataControl</legacyBold> object on a Web page, use nonzero <legacyBold>Height</legacyBold> and <legacyBold>Width</legacyBold> values such as 1 (to avoid the inclusion of extra space).</para>
      <para>Remote Data Service client components are already included as part of Internet Explorer 4.0; therefore, you do not need to include a CODEBASE parameter in your <legacyBold>RDS.DataControl</legacyBold> object tag.</para>
      <para>With Internet Explorer 4.0 or later, you can bind to data by using HTML controls and ActiveX® controls only if they are marked as apartment model controls.</para>
      <alert class="note">
        <para>  <legacyBold>Microsoft Visual Basic Users</legacyBold>   The <legacyBold>RDS.DataControl</legacyBold> is safe for scripting and is used only in Web-based applications. A Visual Basic client application has no need for it.</para>
      </alert>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="9a8f9b0c-8452-4e95-a561-cfc4b7165c5e">DataControl Object (RDS) Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="4f306a51-d5a4-4785-b426-487639cda164">VBScript Example</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>