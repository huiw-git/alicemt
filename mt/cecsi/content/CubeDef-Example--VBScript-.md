---
title: "CubeDef Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d72a912-ef53-4989-9fca-214937574116
caps.latest.revision: 8
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
# CubeDef Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example displays cube metadata on a web page.</para>
  </introduction>
  <section>
    <content>
      <code>&lt;%@ Language=VBScript %&gt;
&lt;%
Response.Buffer=True
'Response.Expires=0
%&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;%
Server.ScriptTimeout=360
Dim cat,cdf,di,hi,le,mem,strServer,strSource,strCubeName

'************************************************************************
'*** Set Session Variables
'************************************************************************
Session("CubeName") = Request.Form("strCubeName")
Session("CatalogName") = Request.Form("strCatalogName")
Session("ServerName") = Request.Form("strServerName")
Session("chkDim") = Request.Form("chkDimension")
Session("chkHier") =  Request.Form("chkHierarchy")
Session("chkLev") =  Request.Form("chkLevel")

'************************************************************************
'*** Create Catalog Object
'************************************************************************************
Set cat = Server.CreateObject("ADOMD.<codeFeaturedElement>Catalog</codeFeaturedElement>")

If Len(Session("ServerName")) &gt; 0 Then
   cat.<codeFeaturedElement>ActiveConnection</codeFeaturedElement> = "Data Source=" &amp; Session("ServerName") &amp; ";Initial Catalog=" &amp; Session("CatalogName") &amp; ";Provider=msolap;"
Else
'************************************************************************************
'*** Must set OLAPServerName to OLAP Server that is
'*** present on network
'************************************************************************
OLAPServerName = "Please set to present OLAP Server"
   cat.ActiveConnection = "Data Source=" &amp; OLAPServerName &amp; _
      ";Initial Catalog=FoodMart;Provider=msolap;"
   Session("ServerName") = OLAPServerName
   Session("InitialCatalog") = "FoodMart"
End if

If Len(Session("CubeName")) &gt; 0 Then
   Set cdf = cat.<codeFeaturedElement>CubeDefs</codeFeaturedElement>(Session("CubeName"))
Else
   Set cdf = cat.CubeDefs("Sales")
   Session("CubeName")="Sales"
End if

'************************************************************************
'*** Collect Information in HTML Form
'************************************************************************
%&gt;
&lt;form action="ASPADOCubeDoc.asp" method="post" id="form1" name="form1"&gt;
&lt;table&gt;
   &lt;tr&gt;
      &lt;td&gt;
      &lt;b&gt;Olap Server name:  &lt;/b&gt;&lt;br&gt;&lt;input type="text" id="strServerName" name="strServerName" value="&lt;%=Session("ServerName")%&gt;" size="20"&gt;&lt;br&gt;

      &lt;b&gt;Catalog Name:  &lt;/b&gt;&lt;br&gt;&lt;input type="text" id="strCatalogName" name="strCatalogName" value="&lt;%=Session("CatalogName")%&gt;" size="20"&gt;&lt;br&gt;

      &lt;b&gt;Cube Name:  &lt;/b&gt;&lt;br&gt;&lt;input type="text" id="strCubeName" name="strCubeName" value="&lt;%=Session("CubeName")%&gt;" size="20"&gt;
      &lt;/td&gt;
      &lt;td &lt;TD&gt;
         &lt;b&gt;Add Property Detail:  &lt;/b&gt;&lt;br&gt;
         Dimension Detail: &lt;input type="checkbox" id="chkDimension" name="chkDimension"&gt;&lt;br&gt;

         Hierarchy Detail: &lt;input type="checkbox" id="chkHierarchy" name="chkHierarchy"&gt;&lt;br&gt;

         Level Detail: &lt;input type="checkbox" id="chkLevel" name="chkLevel"&gt;
      &lt;/td&gt; 
   &lt;/tr&gt;
&lt;/table&gt;
&lt;input type="submit" value="Cube Information" id="submit1" name="submit1"&gt;&lt;input type="reset" value="Reset" id="reset1" name="reset1"&gt;
&lt;/form&gt;
&lt;%

'************************************************************************
'*** Start of Report
'************************************************************************
Response.Write "&lt;H3&gt;Report for " &amp; Session("CubeName") &amp; " Cube&lt;/H3&gt;"
Response.Write "&lt;OL TYPE='i'&gt;"

'************************************************************************
'*** Show properties of Cube
'************************************************************************
            For i = 0 To cdf.Properties.Count - 1
               Response.Write "&lt;LI&gt;"
               Response.Write "&lt;FONT size=-2&gt;" &amp; cdf.Properties(i).Name &amp; ": " &amp; cdf.Properties(i).Value &amp; "&lt;/FONT&gt;"
            Next
            Response.Write "&lt;/OL&gt;"
            Response.Write "&lt;UL TYPE='SQUARE'&gt;"   
 '************************************************************************
'*** Loop to display Dimension Name and Properties if Check box is 
'*** Checked
'************************************************************************
      For di = 0 To cdf.Dimensions.Count - 1
         Response.Write "&lt;LI&gt;"
         Response.Write "&lt;FONT size=4&gt;&lt;B&gt;Dimension: " &amp; _
            cdf.Dimensions(di).<codeFeaturedElement>Name</codeFeaturedElement> &amp; "&lt;/B&gt;&lt;/FONT&gt;"
         If Request.Form("chkDimension") = "on" Then
            Response.Write "&lt;OL TYPE='1'&gt;"
            For i = 0 To cdf.Dimensions(di).Properties.Count - 1
               Response.Write "&lt;LI&gt;"
               Response.Write "&lt;FONT size=-2&gt;" &amp; _
                  cdf.Dimensions(di).Properties(i).<codeFeaturedElement>Name</codeFeaturedElement> &amp; ": " &amp; _
                  cdf.Dimensions(di).Properties(i).<codeFeaturedElement>Value</codeFeaturedElement> &amp; "&lt;/FONT&gt;"
            Next
            Response.Write "&lt;/OL&gt;"
         End If
         Response.Write "&lt;UL TYPE= 'Circle'&gt;"
'************************************************************************
'*** Loop to display Hierarchy Name and Properties if Check box is 
'*** Checked
'************************************************************************
         For hi = 0 To cdf.Dimensions(di).Hierarchies.Count - 1
            Response.Write "&lt;LI&gt;"
            Response.Write "&lt;FONT size=3&gt;&lt;B&gt;Hierarchy: " &amp; _
               cdf.<codeFeaturedElement>Dimensions</codeFeaturedElement>(di).<codeFeaturedElement>Hierarchies</codeFeaturedElement>(hi).<codeFeaturedElement>Name</codeFeaturedElement> &amp; "&lt;/B&gt;&lt;/FONT&gt;"
            If Request.Form("chkHierarchy") = "on" Then
               Response.Write "&lt;OL TYPE='1'&gt;"
               For i = 0 To _
                  cdf.Dimensions(di).Hierarchies(hi).Properties.Count - 1
                  Response.Write "&lt;LI&gt;"
                  Response.Write "&lt;FONT size=-2&gt;" &amp; _
                     cdf.Dimensions(di).Hierarchies(hi).Properties(i)._
                     Name &amp; ": " &amp; _
                     cdf.Dimensions(di).Hierarchies(hi).Properties(i)._
                     Value &amp; "&lt;/FONT&gt;"
               Next
               Response.Write "&lt;/OL&gt;"
            End If
            Response.Write "&lt;UL TYPE='Disc'&gt;"
'************************************************************************
'*** Loop to display Level Name and Properties if Check box is Checked
'************************************************************************
      For le = 0 To cdf.Dimensions(di).Hierarchies(hi).<codeFeaturedElement>Levels</codeFeaturedElement>.Count - 1
               Response.Write "&lt;LI&gt;"
               Response.Write "&lt;FONT size=2&gt;&lt;B&gt;Level: " &amp; _
                  cdf.Dimensions(di).Hierarchies(hi).Levels(le).Name &amp; _
                  " with a Member Count of: " &amp; _
                  cdf.Dimensions(di).Hierarchies(hi).Levels(le)._
                  Properties("LEVEL_CARDINALITY") &amp; "&lt;/B&gt;&lt;/FONT&gt;"
               If Request.Form("chkLevel") = "on" Then
                  Response.Write "&lt;OL TYPE='1'&gt;"
                  For i = 0 To 
                     cdf.Dimensions(di).Hierarchies(hi).Levels(le)._
                     Properties.Count - 1
                     Response.Write "&lt;LI&gt;"
                     Response.Write "&lt;FONT size=-2&gt;" &amp; _
                        cdf.Dimensions(di).Hierarchies(hi).Levels(le)._
                        Properties(i).Name &amp; ": " &amp; _
                        cdf.Dimensions(di).Hierarchies(hi).Levels(le)._
                        Properties(i).Value &amp; "&lt;/FONT&gt;"
                  Next
                  Response.Write "&lt;/OL&gt;"
               End If
            Next
            Response.Write "&lt;/UL&gt;"
         Next
         Response.Write "&lt;/UL&gt;"
      Next
      Response.Write "&lt;/UL&gt;"
%&gt;
&lt;/body&gt;
&lt;/html&gt;</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>