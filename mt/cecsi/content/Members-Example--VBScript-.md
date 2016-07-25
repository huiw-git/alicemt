---
title: "Members Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87bbd4ad-bb1a-4123-93ef-99ef47fd970b
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
# Members Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This sample uses an MDX query string to retrieve OLAP data and writes the resulting cellset to an HTML table structure using column spanning features for multiple-dimension cellsets.</para>
  </introduction>
  <section>
    <content>
      <code>&lt;%@ Language=VBScript %&gt;
&lt;%
'************************************************************************
'*** Active Server Page displays OLAP data from default or provided
'*** MDX Query string and writes resulting cell set to HTML table
'*** structure. This ASP provides colspan features for multiple
'*** dimension cell sets.
'************************************************************************
Response.Buffer=True
Response.Expires=0
%&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;/head&gt;
&lt;body bgcolor="Ivory"&gt;
&lt;font FACE="Verdana"&gt;

&lt;%

Dim cat,cst,i,j,strSource,csw,LevelValue,intDC0,intDC1,intPC0, intPC1
'************************************************************************
'*** Gather Server Name and MDX Query Strings from text box and
'*** text area and assign them to Session Objects of same name
'************************************************************************
Session("ServerName")=Request.Form("strServerName")
Session("InitialCatalog")=Request.Form("strInitialCatalog")
Session("MDXQuery")=Request.Form("MDXQuery")

'************************************************************************
'*** Set Connection Objects for Multi dimensional Catalog and Cell Set
'************************************************************************
Set cat = Server.CreateObject("ADOMD.<codeFeaturedElement>Catalog</codeFeaturedElement>")
Set cst = Server.CreateObject("ADOMD.<codeFeaturedElement>CellSet</codeFeaturedElement>")

'************************************************************************
'*** Check to see if the Session Object Server Name is present
'*** If present then: Create Active Connection using Server Name
'*** and MSOLAP as connection Provider
'*** If not present then: Use default settings of a known OLAP Server
'*** for Server Name for Connection Set Server Name Session Object
'*** to default value
'************************************************************************
If Len(Session("ServerName")) &gt; 0 Then
   cat.<codeFeaturedElement>ActiveConnection</codeFeaturedElement> = "Data Source=" &amp; Session("ServerName") &amp; _
      ";Initial Catalog=" &amp; Session("InitialCatalog") &amp; _
      ";Provider=msolap;"
Else

'************************************************************************
'*** Must set OLAPServerName to OLAP Server that is
'*** present on network
'************************************************************************
   OLAPServerName = "Please set to present OLAP Server"
   cat.<codeFeaturedElement>ActiveConnection</codeFeaturedElement> = "Data Source=" &amp; OLAPServerName &amp; _
      ";Initial Catalog=FoodMart;Provider=msolap;"
   Session("ServerName") = OLAPServerName
   Session("InitialCatalog") = "FoodMart"
End if
'************************************************************************
'*** Check to see if the Session Object MDXQuery is present
'*** If present then: Set strSource using MDXQuery Session Object
'*** If not present then: Use default MDX Query string of a known query
'*** that works with default server Set MDXQuery Session Object to 
'*** default value
'************************************************************************
If Len(Session("MDXQuery")) &lt; 5 Then
   strSource = strSource &amp; "SELECT "
   strSource = strSource &amp; "CROSSJOIN({[Store].[Store Country].MEMBERS},"
   strSource = strSource &amp; "{[Measures].[Store " &amp; _
      "Invoice],[Measures].[Supply Time]}) ON COLUMNS,"
   strSource = strSource &amp; "CROSSJOIN({[Time].[Year].MEMBERS},"
   strSource = strSource &amp; "CROSSJOIN({[Store Type].[Store " &amp; _
      "Type].Members},{[Product].[Product Family].members})) ON ROWS"
   strSource = strSource &amp; " FROM Warehouse"
Else
   strSource = Session("MDXQuery")
End if

'************************************************************************
'*** Set Cell Set Source property to strSource to be passed on cell set 
'*** open method
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
'*** Standard HTML to collect Server Name and MDX Query Information
'*** Note that post action posts back to same page to process
'*** thus using state of Session Variables to change look of page
'************************************************************************
%&gt;
&lt;form action="ASPADOComplex.asp" method="POST" id="form1" name="form1"&gt;
&lt;table&gt;
&lt;tr&gt;&lt;td align="left"&gt;
&lt;b&gt;Olap Server name:&lt;/b&gt;&lt;br&gt;&lt;input type="text" id="strServerName" name="strServerName" value="&lt;%=Session("ServerName")%&gt;" size="20"&gt;
&lt;br&gt;
&lt;b&gt;Catalog name:&lt;/b&gt;&lt;br&gt;&lt;input type="text" id="strInitialCatalog" name="strInitialCatalog" value="&lt;%=Session("InitialCatalog")%&gt;" size="20"&gt;
&lt;/td&gt;&lt;td align="center"&gt;
&lt;b&gt;MDX Query:&lt;/b&gt;&lt;br&gt;
&lt;textarea rows="7" cols="70" id="textareaMDX" name="MDXQuery" wrap="soft"&gt;
&lt;%=Session("MDXQuery")%&gt;
&lt;/textarea&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;/table&gt;
&lt;table&gt;
&lt;tr&gt;&lt;td&gt;
&lt;input type="submit" value="Submit MDX Query" id="submit1" name="submit1"&gt;
&lt;/td&gt;&lt;td&gt;
&lt;input type="reset" value="Reset" id="reset1" name="reset1"&gt;
&lt;/td&gt;&lt;/tr&gt;
&lt;/table&gt;
&lt;/form&gt;
&lt;p align="left"&gt;
&lt;font color="Black" size="-3"&gt;
&lt;%=strSource%&gt;
&lt;/font&gt;
&lt;/p&gt;
&lt;%
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
'*** Loop to create Column header for all Dimensions based
'*** on Count of Dimensions for Axes(0)
'************************************************************************
For h=0 to intDC0
   Response.Write "&lt;TR&gt;"

'************************************************************************
'*** Loop to create spaces in front of Column headers
'*** to align with Row headers
'************************************************************************
   For c=0 to intDC1
      Response.Write "&lt;TD&gt;&lt;/TD&gt;"
   Next

'************************************************************************
'*** Check current dimension to see if equal to Last Dimension
'*** If True: Write Table header titles normally to HTML output with out 
'*** ColSpan value 
'*** If False: Write Table header titles with ColSpan values to HTML 
'*** output
'************************************************************************
   If h = intDC0 then

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
   Else

'************************************************************************
'*** Iterate through Axes(0) Positions writing member captions to table 
'*** header taking into account for the span of columns for duplicate 
'*** member captions
'************************************************************************
      CaptionCount = 1
      LastCaption = cst.Axes(0).Positions(0).Members(h).Caption
      Response.Write "&lt;TH"
      For t=1 to intPC0

'************************************************************************
'*** Check to see if LastCaption is equal to current members caption
'*** If True: Add one to CaptionCount to increase Colspan value
'*** If False: Write Table header titles with ColSpan values to HTML 
'*** output using current CaptionCount for Colspan and LastCaption for 
'*** header string
'************************************************************************
         If LastCaption = _
            cst.Axes(0).Positions(t).Members(h).Caption then
            CaptionCount = CaptionCount+1

'************************************************************************
'*** Check if at last position
'*** If True: Write HTML to finish table row using current
'*** CaptionCount and LastCaption
'************************************************************************
            If t = intPC0 then
               Response.Write " colspan=" &amp; CaptionCount &amp; _
                  "&gt;&lt;FONT size=-2&gt;" &amp; LastCaption &amp; "&lt;/FONT&gt;&lt;/TH&gt;"
            End if

         Else
            Response.Write " colspan=" &amp; CaptionCount &amp; _
               "&gt;&lt;FONT size=-2&gt;" &amp; LastCaption &amp; "&lt;/FONT&gt;&lt;/TH&gt;&lt;TH"
            CaptionCount = 1
            LastCaption=cst.Axes(0).Positions(t).Members(h).Caption
         End if
      Next
         End if
         Response.Write "&lt;/TR&gt;"
      Next

'************************************************************************
'*** Iterate through Axes(1) Positions first writing member captions 
'*** to table row headers then writing cell set data to table structure
'************************************************************************
      Dim aryRows()
      Dim intArray,Marker
      intArray=0

'************************************************************************
'*** Set value of Array for row header formatting
'************************************************************************
      For a=1 To intDC1
         intArray = intArray+(intPC1+1)
      Next
      intArray = intArray-1
      ReDim aryRows(intArray)
      Marker=0

'************************************************************************
'*** Use Array values for row header formatting to provide
'*** spaces under beginning row header titles
'************************************************************************
      For j = 0 To intPC1
         Response.Write "&lt;TR&gt;"
         For h=0 to intDC1
            If h=intDC1 then
               Response.Write "&lt;TD&gt;&lt;B&gt;"
               Response.Write "&lt;FONT size=-2&gt;"
               Response.Write cst.Axes(1).Positions(j).Members(h).Caption
               Response.Write "&lt;/FONT&gt;"
               Response.Write "&lt;/B&gt;&lt;/TD&gt;"
            Else
               aryRows(Marker) = _
                  cst.Axes(1).Positions(j).Members(h).Caption
               If Marker &lt; intDC1 then
                  Response.Write "&lt;TD&gt;&lt;B&gt;"
                  Response.Write "&lt;FONT size=-2&gt;"
                  Response.Write _
                     cst.Axes(1).Positions(j).Members(h).Caption
                  Response.Write "&lt;/FONT&gt;"
                  Response.Write "&lt;/B&gt;&lt;/TD&gt;"
                  Marker = Marker + 1
               Else
                  If aryRows(Marker) = aryRows(Marker - intDC1) then
                     Response.Write "&lt;TD&gt;&amp;nbsp;&lt;/TD&gt;"
                     Marker = Marker + 1
                  Else
                     Response.Write "&lt;TD&gt;&lt;B&gt;"
                     Response.Write "&lt;FONT size=-2&gt;"
                     Response.Write _
                        cst.Axes(1).Positions(j).Members(h).Caption
                     Response.Write "&lt;/FONT&gt;"
                     Response.Write "&lt;/B&gt;&lt;/TD&gt;"
                     Marker = Marker + 1
                  End if
               End if
            End if
         Next

'************************************************************************
'*** Alternates Cell background color
'************************************************************************
         If (j+1) Mod 2 = 0 Then
            csw = "#cccccc"
         Else
            csw = "#ccffff"
         End If
         For k = 0 To intPC0
            Response.Write "&lt;TD align=right bgcolor="
            Response.Write csw
            Response.Write "&gt;"
            Response.Write "&lt;FONT size=-2&gt;"

'************************************************************************
'*** FormattedValue property pulls data
'************************************************************************
            Response.Write cst(k, j).<codeFeaturedElement>FormattedValue</codeFeaturedElement>
            Response.Write "&lt;/FONT&gt;"
            Response.Write "&lt;/TD&gt;"
         Next
         Response.Write "&lt;/TR&gt;"
      Next
      Response.Write "&lt;/Table&gt;"

%&gt;
&lt;/font&gt;
&lt;/body&gt;
&lt;/html&gt;</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>