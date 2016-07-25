---
title: "FilterColumn, FilterCriterion, FilterValue, SortColumn, and SortDirection Properties and Reset Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a74802f-34d6-4676-bf94-07df5f8bff66
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
# FilterColumn, FilterCriterion, FilterValue, SortColumn, and SortDirection Properties and Reset Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following code shows how to set the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> <legacyBold>Server</legacyBold> parameter at designtime and bind it to a data-aware HTML table using a data source. Cut and paste the following code to Notepad or another text editor and save it as <legacyBold>FilterColumnVBS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginFilterColumnVBS --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;META name="VI60_DefaultClientScript" Content="VBScript"&gt;

&lt;META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;TITLE&gt;FilterColumn, FilterCriterion, FilterValue, SortColumn, and SortDirection 
Properties and Reset Method Example (VBScript)&lt;/TITLE&gt;
&lt;/HEAD&gt;
&lt;BODY&gt;
&lt;h1&gt;FilterColumn, FilterCriterion, FilterValue, SortColumn, and SortDirection 
Properties and Reset Method Example (VBScript)&lt;/h1&gt;

&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
   ID=RDS HEIGHT=1 WIDTH=1&gt;
   &lt;PARAM NAME="SQL" VALUE="Select FirstName, LastName, Title, ReportsTo, Extension from Employees"&gt;
   &lt;PARAM NAME="SERVER" VALUE="&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;
   &lt;PARAM NAME="CONNECT" VALUE="Provider=SQLOLEDB;Initial Catalog=Northwind;Integrated Security=SSPI"&gt;
&lt;/OBJECT&gt;

Sort Column: &lt;SELECT NAME="cboSortColumn"&gt; 
              &lt;OPTION VALUE=""&gt;&lt;/OPTION&gt;
                  &lt;OPTION VALUE=ID&gt;ID&lt;/OPTION&gt;
                  &lt;OPTION VALUE=FirstName&gt;FirstName&lt;/OPTION&gt;
                  &lt;OPTION VALUE=LastName&gt;LastName&lt;/OPTION&gt;
                  &lt;OPTION VALUE=Title&gt;Title&lt;/OPTION&gt;
                  &lt;OPTION VALUE=Title&gt;ReportsTo&lt;/OPTION&gt;
                  &lt;OPTION VALUE=Phone&gt;Extension&lt;/OPTION&gt;
             &lt;/SELECT&gt;
             &lt;br&gt;
Sort Direction: &lt;SELECT NAME="cboSortDir"&gt; 
              &lt;OPTION VALUE=""&gt;&lt;/OPTION&gt;
                  &lt;OPTION VALUE=TRUE&gt;Ascending&lt;/OPTION&gt;
                  &lt;OPTION VALUE=FALSE&gt;Descending&lt;/OPTION&gt;
                &lt;/SELECT&gt;
&lt;HR WIDTH="25%"&gt;
Filter Column: &lt;SELECT NAME="cboFilterColumn"&gt; 
              &lt;OPTION VALUE=""&gt;&lt;/OPTION&gt;
                  &lt;OPTION VALUE=FirstName&gt;FirstName&lt;/OPTION&gt;
                  &lt;OPTION VALUE=LastName&gt;LastName&lt;/OPTION&gt;
                  &lt;OPTION VALUE=Title&gt;Title&lt;/OPTION&gt;
                  &lt;OPTION VALUE=Room&gt;ReportsTo&lt;/OPTION&gt;
                  &lt;OPTION VALUE=Phone&gt;Extension&lt;/OPTION&gt;
             &lt;/SELECT&gt;
             &lt;br&gt;
Filter Criterion: &lt;SELECT NAME="cboCriterion"&gt; 
                    &lt;OPTION VALUE=""&gt;&lt;/OPTION&gt;
                    &lt;OPTION VALUE="="&gt;=&lt;/OPTION&gt;
                    &lt;OPTION VALUE="&amp;gt;"&gt;&amp;gt;&lt;/OPTION&gt;
                    &lt;OPTION VALUE="&amp;lt;"&gt;&amp;lt;&lt;/OPTION&gt;
                    &lt;OPTION VALUE="&amp;gt;="&gt;&amp;gt;=&lt;/OPTION&gt;
                    &lt;OPTION VALUE="&amp;lt;="&gt;&amp;lt;=&lt;/OPTION&gt;
                    &lt;OPTION VALUE="&amp;lt;&amp;gt;"&gt;&amp;lt;&amp;gt;&lt;/OPTION&gt;
                  &lt;/SELECT&gt; 
              &lt;br&gt;
Filter Value: &lt;INPUT NAME="txtFilterValue"&gt;
&lt;HR WIDTH="25%"&gt;
&lt;INPUT TYPE=BUTTON NAME=Clear VALUE="CLEAR ALL"&gt; &amp;nbsp;
&lt;INPUT TYPE=BUTTON NAME=SortFilter VALUE="APPLY"&gt;

&lt;HR&gt;
&lt;TABLE DATASRC=#RDS ID="DataTable"&gt;
&lt;THEAD&gt;
  &lt;TR&gt;
    &lt;TH&gt;FirstName&lt;/TH&gt;
    &lt;TH&gt;LastName&lt;/TH&gt;
    &lt;TH&gt;Title&lt;/TH&gt;
    &lt;TH&gt;Reports To&lt;/TH&gt;
    &lt;TH&gt;Extension&lt;/TH&gt;
  &lt;/TR&gt;
&lt;/THEAD&gt;
&lt;TBODY&gt;
  &lt;TR&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="Title"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="ReportsTo"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="Extension"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
  &lt;/TR&gt;
&lt;/TBODY&gt;
&lt;/TABLE&gt;

&lt;Script Language="VBScript"&gt;
&lt;!--
Const adFilterNone = 0

Sub SortFilter_OnClick
   Dim vCriterion
   Dim vSortDir
   Dim vSortCol
   Dim vFilterCol
   
   ' The value of SortColumn will be the 
   ' value of what the user picks in the
   ' cboSortColumn box.
   vSortCol = cboSortColumn.options(cboSortColumn.selectedIndex).value
   
   If(vSortCol &lt;&gt; "") then
      RDS.SortColumn = vSortCol
   End If

   ' The value of SortDirection will be the 
   ' value of what the user specifies in the
   ' cboSortdirection box.
   
   If (vSortCol &lt;&gt; "") then
      vSortDir = cboSortDir.options(cboSortDir.selectedIndex).value
      If (vSortDir = "") then
         MsgBox "You must select a direction for the sort."
         Exit Sub
      Else
         If vSortDir = "Ascending" Then vSortDir = "TRUE"
         If vSortDir = "Descending" Then vSortDir = "FALSE"
         RDS.SortDirection = vSortDir
      End If
   End If

   ' The value of FilterColumn will be the 
   ' value of what the user specifies in the
   ' cboFilterColumn box.
   vFilterCol = cboFilterColumn.options(cboFilterColumn.selectedIndex).value
   
   If(vFilterCol &lt;&gt; "") then
      RDS.FilterColumn = vFilterCol
   End If

   ' The value of FilterCriterion will be the 
   ' text value of what the user specifies in the
   ' cboCriterion box.
   vCriterion = cboCriterion.options(cboCriterion.selectedIndex).value
   If (vCriterion &lt;&gt; "") Then
      RDS.FilterCriterion = vCriterion
   End If

   ' txtFilterValue is a rich text box
   ' control. The value of FilterValue will be the 
   ' text value of what the user specifies in the
   ' txtFilterValue box.
   If (txtFilterValue.value &lt;&gt; "") Then
      RDS.FilterValue = txtFilterValue.value
   End If

   ' Execute the sort and filter on a client-side
   ' Recordset based on the specified sort and filter
   ' properties. Calling Reset refreshes the result set
   ' that is displayed in the data-bound controls to
   ' display the filtered, sorted recordset.
   RDS.Reset
End Sub

Sub Clear_onClick()
   'clear the HTML input controls
   cboSortColumn.selectedIndex = 0
   cboSortDir.selectedIndex = 0
   cboFilterColumn.selectedIndex = 0
   cboCriterion.selectedIndex = 0
   txtFilterValue.value = ""
   
   'clear the filter
   RDS.FilterCriterion = ""
   RDS.Reset(FALSE)
End Sub
--&gt;
&lt;/Script&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndFilterColumnVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="0a5473e8-8ce6-4518-83fb-4920b827e285">FilterColumn Property (RDS)</link>
<link xlink:href="24eb03ba-ccfd-4353-b6af-03586b2da6fd">FilterCriterion Property (RDS)</link>
<link xlink:href="28f17186-b842-4cf9-b320-a9bb941c481b">FilterValue Property (RDS)</link>
<link xlink:href="3957197a-f543-4d6b-9e11-67a77c2063b7">Reset Method (RDS)</link>
<link xlink:href="f6f80f67-f0fb-4e63-a5f5-8fdf312aac63">SortColumn Property (RDS)</link>
<link xlink:href="1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2">SortDirection Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>