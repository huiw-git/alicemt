---
title: "Axis Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4647211-2566-4657-ae7b-3dd761457d7b
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
# Axis Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This Active Server Page displays OLAP data from an MDX Query string and writes the resulting cellset to an HTML table structure.</para>
  </introduction>
  <section>
    <content>
      <code>&lt;%@ Language=VBScript %&gt;
&lt;%
'************************************************************************
'*** Active Server Page displays OLAP data from default
'*** MDX Query string and writes resulting cell set to HTML table
'*** structure.
'************************************************************************
Response.Buffer=True
Response.Expires=0
%&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;/HEAD&gt;
&lt;BODY bgcolor=Ivory&gt;
&lt;FONT FACE=Verdana&gt;

&lt;%

Dim cat,cst,i,j,strSource,csw,intDC0,intDC1,intPC0,intPC1

'************************************************************************
'*** Set Connection Objects for Multidimensional Catalog and Cellset
'************************************************************************
Set cat = Server.CreateObject("ADOMD.<codeFeaturedElement>Catalog</codeFeaturedElement>")
Set cst = Server.CreateObject("ADOMD.<codeFeaturedElement>CellSet</codeFeaturedElement>")

'************************************************************************
'*** Use default settings of a known OLAP Server
'*** for Server Name for Connection Set Server Name Session Object
'*** to default value
'************************************************************************
'*** Must set OLAPServerName to OLAP Server that is
'*** present on network
'************************************************************************
   OLAPServerName = "Please set to present OLAP Server"
   cat.<codeFeaturedElement>ActiveConnection</codeFeaturedElement> = "Data Source=" &amp; OLAPServerName &amp; _
      ";Initial Catalog=FoodMart;Provider=msolap;"

'************************************************************************
'*** Use default MDX Query string of a known query that works
'*** with default server Set MDXQuery Session Object to default value
'************************************************************************
   strSource = strSource &amp; "SELECT "
   strSource = strSource &amp; "{[Measures].members} ON COLUMNS,"
   strSource = strSource &amp; _
      "NON EMPTY [Store].[Store City].members ON ROWS"
   strSource = strSource &amp; " FROM Sales"

'************************************************************************
'*** Set Cell Set Source property to strSource to be passed on cell set '*** open method
'************************************************************************
    cst.<codeFeaturedElement>Source</codeFeaturedElement> = strSource

'************************************************************************
'*** Set Cell Sets Active connection to use the current Catalogs Active 
'*** connection
'************************************************************************
Set cst.<codeFeaturedElement>ActiveConnection</codeFeaturedElement> = cat.<codeFeaturedElement>ActiveConnection</codeFeaturedElement>

'************************************************************************
'*** Using Open method, Open cell set
'************************************************************************
cst.<codeFeaturedElement>Open</codeFeaturedElement>

'************************************************************************
'*** Set Dimension Counts minus 1 for Both Axes to intDC0, intDC1
'*** Set Position Counts minus 1 for Both Axes to intPC0, intPC1
'************************************************************************
intDC0 = cst.<codeFeaturedElement>Axes</codeFeaturedElement>(0).<codeFeaturedElement>DimensionCount</codeFeaturedElement>-1
intDC1 = cst.Axes(1).DimensionCount-1

intPC0 = cst.Axes(0).<codeFeaturedElement>Positions</codeFeaturedElement>.Count - 1
intPC1 = cst.Axes(1).Positions.Count - 1

'************************************************************************
'*** Create HTML Table structure to hold MDX Query return Record set
'************************************************************************
      Response.Write "&lt;Table width=100% border=1&gt;"

'************************************************************************
'*** Loop to create Column header
'************************************************************************
      For h=0 to intDC0
         Response.Write "&lt;TR&gt;"

'************************************************************************
'*** Loop to create spaces in front of Column headers
'*** to align with Row header
'************************************************************************
         For c=0 to intDC1
            Response.Write "&lt;TD&gt;&lt;/TD&gt;"
         Next

'************************************************************************
'*** Iterate through Axes(0) Positions writing member captions to table 
'*** header
'************************************************************************
         For i = 0 To intPC0
            Response.Write "&lt;TH&gt;"
            Response.Write "&lt;FONT size=-2&gt;"
            Response.Write cst.Axes(0).Positions(i).<codeFeaturedElement>Members</codeFeaturedElement>(h).<codeFeaturedElement>Caption</codeFeaturedElement>
            Response.Write "&lt;/FONT&gt;"
            Response.Write "&lt;/TH&gt;"
         Next
         Response.Write "&lt;/TR&gt;"
      Next
'************************************************************************
'*** Use Array values for row header formatting to provide
'*** spaces under beginning row header titles
'************************************************************************
      For j = 0 To intPC1
         Response.Write "&lt;TR&gt;"
         For h=0 to intDC1
            Response.Write "&lt;TD&gt;&lt;B&gt;"
            Response.Write "&lt;FONT size=-2&gt;"
            Response.Write cst.Axes(1).Positions(j).Members(h).Caption
            Response.Write "&lt;/FONT&gt;"
            Response.Write "&lt;/B&gt;&lt;/TD&gt;"
         Next
         For k = 0 To intPC0
            Response.Write "&lt;TD align=right bgcolor="
            Response.Write csw
            Response.Write "&gt;"
            Response.Write "&lt;FONT size=-2&gt;"
            Response.Write cst(k, j).<codeFeaturedElement>FormattedValue</codeFeaturedElement>
            Response.Write "&lt;/FONT&gt;"
            Response.Write "&lt;/TD&gt;"
         Next
         Response.Write "&lt;/TR&gt;"
      Next
      Response.Write "&lt;/Table&gt;"

%&gt;
&lt;/FONT&gt;
&lt;/BODY&gt;
&lt;/HTML&gt;</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>