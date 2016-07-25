---
title: "Microsoft OLE DB Simple Provider"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e7dc6f0-482c-4103-8187-f890865e40fc
caps.latest.revision: 14
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
# Microsoft OLE DB Simple Provider
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft OLE DB Simple Provider (OSP) allows ADO to access any data for which a provider has been written using the <legacyLink xlink:href="6e7b7931-9e4a-4151-ae51-672abd3f84a6">OLE DB Simple Provider (OSP) Toolkit</legacyLink>. Simple providers are intended to access data sources that require only fundamental OLE DB support, such as in-memory arrays or XML documents.</para>
  </introduction>
  <section>
    <title>Connection String Parameters</title>
    <content>
      <para>To connect to the OLE DB Simple Provider DLL, set the <legacyItalic>Provider</legacyItalic> argument to the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to:</para>
      <code>MSDAOSP</code>
      <para>This value can also be set or read using the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property.</para>
      <para>You can connect to simple providers that have been registered as full OLE DB providers by using the registered provider name, determined by the provider writer.</para>
    </content>
  </section>
  <section>
    <title>Typical Connection String</title>
    <content>
      <para>A typical connection string for this provider is:</para>
      <code>"Provider=MSDAOSP;Data Source=<legacyItalic>serverName</legacyItalic>"</code>
      <para>The string consists of these keywords:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Keyword</para>
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
                <legacyBold>Provider</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the OLE DB provider for SQL Server. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Data Source</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the name of a server. </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>XML Document Example</title>
    <content>
      <para>The OLE DB Simple Provider (OSP) in MDAC 2.7 or later and Windows Data Access Components (Windows DAC) has been enhanced to support opening hierarchical ADO <legacyBold>Recordsets</legacyBold> over arbitrary XML files. These XML files may contain the ADO XML persistence schema, but it is not required. This has been implemented by connecting the OSP to the <legacyBold>MSXML2.DLL</legacyBold>; therefore <legacyBold>MSXML2.DLL</legacyBold> or later is required. </para>
      <para>The <legacyBold>portfolio.xml</legacyBold> file used in the following example contains the following tree:</para>
      <code>Portfolio
   Stock
      Shares
      Symbol
      Price
      Info
         Company Name
         WebSite</code>
      <para>The XML DSO uses built-in heuristics to convert the nodes in an XML tree to chapters in a hierarchical <legacyBold>Recordset</legacyBold>.</para>
      <para>Using these built-in heuristics, the XML tree is converted into a two-level hierarchical <legacyBold>Recordset</legacyBold> of the following form:</para>
      <code>Parent Recordset
Shares, Symbol, Price, $Text
   Child Recordset
      Company Name, WebSite, $Text</code>
      <para>Note that the Portfolio and Info tags are not represented in the hierarchical <legacyBold>Recordset</legacyBold>. For an explanation of how the XML DSO converts XML trees to hierarchical <legacyBold>Recordsets</legacyBold>, see the following rules. The $Text column is discussed in the following section.</para>
    </content>
  </section>
  <section>
    <title>Rules for Assigning XML Elements and Attributes to Columns and Rows</title>
    <content>
      <para>The XML DSO follows a procedure for assigning elements and attributes to columns and rows in data-bound applications. XML is modeled as a tree with one tag that contains the entire hierarchy. For example, an XML description of a book could contain chapter tags, figure tags, and section tags. At the highest level would be the book tag, containing the subelements chapter, figure, and section. When the XML DSO maps XML elements to rows and columns, the subelements, not the top level element, are converted.</para>
      <para>The XML DSO uses this procedure for converting the subelements:  </para>
      <list class="bullet">
        <listItem>
          <para>Each subelement and attribute corresponds to a column in some <legacyBold>Recordset</legacyBold> in the hierarchy.</para>
        </listItem>
        <listItem>
          <para>The name of the column is the same as the name of the subelement or attribute, unless the parent element has an attribute and a subelement with the same name, in which case a "!" is prepended to the subelement's column name.</para>
        </listItem>
        <listItem>
          <para>Each column is either a <legacyItalic>simple</legacyItalic> column that contains scalar values (usually strings) or a <legacyBold>Recordset</legacyBold> column that contains child <legacyBold>Recordsets</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>Columns corresponding to attributes are always simple.</para>
        </listItem>
        <listItem>
          <para>Columns corresponding to subelements are <legacyBold>Recordset</legacyBold> columns if either the subelement has its own subelements or attributes (or both), or the subelement's parent has more than one instance of the subelement as a child. Otherwise the column is simple.</para>
        </listItem>
        <listItem>
          <para>When there are multiple instances of a subelement (under different parents), its column is a <legacyBold>Recordset</legacyBold> column if <legacyItalic>any</legacyItalic> of the instances imply a <legacyBold>Recordset</legacyBold> column; its column is simple only if <legacyItalic>all</legacyItalic> instances imply a simple column.</para>
        </listItem>
        <listItem>
          <para>All <legacyBold>Recordsets</legacyBold> have an additional column named $Text.</para>
        </listItem>
      </list>
      <para>The code that is needed to construct a <legacyBold>Recordset</legacyBold> is as follows:</para>
      <code>   Dim adoConn as ADODB.Connection
   Dim adoRS as ADODB.Recordset

   Set adoRS = New ADODB.Connection
   Set adoRS = New ADODB.Recordset

   adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
   adoRS.Open "http://WebServer/VRoot/portfolio.xml, adoConn</code>
      <alert class="note">
        <para>The path of the data file can be specified by using four different naming conventions.</para>
      </alert>
      <code>   'HTTP://
   adoRS.Open "http://WebServer/VRoot/portfolio.xml", adoConn
   'FILE://
   adoRS.Open "file:/// C:\\Directory\\portfolio.xml", adoConn
   'UNC Path
   adoRS.Open "\\ComputerName\ShareName\portfolio.xml", adoConn
   'Full DOS Path
   adoRS.Open "C:\Directory\portfolio.xml", adoConn</code>
      <para>As soon as the <legacyBold>Recordset</legacyBold> has been opened, the usual ADO <legacyBold>Recordset</legacyBold> navigation commands can be used.</para>
      <para>
        <legacyBold>Recordsets</legacyBold> generated by the OSP have a few limitations:  </para>
      <list class="bullet">
        <listItem>
          <para>Client cursors (<legacyBold>adUseClient</legacyBold>) are not supported.</para>
        </listItem>
        <listItem>
          <para>Hierarchical <legacyBold>Recordsets</legacyBold> created over arbitrary XML cannot be persisted using <legacyBold>Recordset.Save</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Recordsets</legacyBold> created with the OSP are read-only.</para>
        </listItem>
        <listItem>
          <para>The XMLDSO adds an additional column of Data ($Text) to each <legacyBold>Recordset</legacyBold> in the Hierarchy.</para>
        </listItem>
      </list>
      <para>For more information about the OLE DB Simple Provider, see <legacyLink xlink:href="b31a6cba-58ae-4ee8-9039-700973d354d6">Building a Simple Provider</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>The following Visual Basic code demonstrates opening an arbitrary XML file, constructing a hierarchical <legacyBold>Recordset</legacyBold>, and recursively writing each record of each <legacyBold>Recordset</legacyBold> to the debug window.</para>
      <para>Here is a simple XML file that contains stock quotes. The following code uses this file to construct a two-level hierarchical <legacyBold>Recordset</legacyBold>.</para>
      <code>&lt;portfolio&gt;
   &lt;stock&gt;
      &lt;shares&gt;100&lt;/shares&gt;
      &lt;symbol&gt;MSFT&lt;/symbol&gt;
      &lt;price&gt;$70.00&lt;/price&gt;
      &lt;info&gt;
         &lt;companyname&gt;Microsoft Corporation&lt;/companyname&gt;
         &lt;website&gt;http://www.microsoft.com&lt;/website&gt;
      &lt;/info&gt;
   &lt;/stock&gt;
   &lt;stock&gt;
      &lt;shares&gt;100&lt;/shares&gt;
      &lt;symbol&gt;AAPL&lt;/symbol&gt;
      &lt;price&gt;$107.00&lt;/price&gt;
      &lt;info&gt;
         &lt;companyname&gt;Apple Computer, Inc.&lt;/companyname&gt;
         &lt;website&gt;http://www.apple.com&lt;/website&gt;
      &lt;/info&gt;
   &lt;/stock&gt;
   &lt;stock&gt;
      &lt;shares&gt;100&lt;/shares&gt;
      &lt;symbol&gt;DELL&lt;/symbol&gt;
      &lt;price&gt;$50.00&lt;/price&gt;
      &lt;info&gt;
         &lt;companyname&gt;Dell Corporation&lt;/companyname&gt;
         &lt;website&gt;http://www.dell.com&lt;/website&gt;
      &lt;/info&gt;
    &lt;/stock&gt;
    &lt;stock&gt;
       &lt;shares&gt;100&lt;/shares&gt;
       &lt;symbol&gt;INTC&lt;/symbol&gt;
       &lt;price&gt;$115.00&lt;/price&gt;
       &lt;info&gt;
          &lt;companyname&gt;Intel Corporation&lt;/companyname&gt;
          &lt;website&gt;http://www.intel.com&lt;/website&gt;
       &lt;/info&gt;
   &lt;/stock&gt;
&lt;/portfolio&gt;</code>
      <para>Following are two Visual Basic sub procedures. The first creates the <legacyBold>Recordset</legacyBold> and passes it to the <legacyItalic>WalkHier</legacyItalic> sub procedure, which recursively walks down the hierarchy, writing each <legacyBold>Field</legacyBold> in each record in each <legacyBold>Recordset</legacyBold> to the debug window.</para>
      <code>Private Sub BrowseHierRecordset()
' Add ADO 2.7 or later to Project/References
' No need to add MSXML2, ADO just passes the ProgID through to the OSP.

    Dim adoConn As ADODB.Connection
    Dim adoRS As ADODB.Recordset
    Dim adoChildRS As ADODB.Recordset
        
    Set adoConn = New ADODB.Connection
    Set adoRS = New ADODB.Recordset
    Set adoChildRS = ADODB.Recordset

    adoConn.Open "Provider=MSDAOSP; Data Source=MSXML2.DSOControl.2.6;"
    adoRS.Open "http://bwillett3/Kowalski/portfolio.xml", adoConn
       
    Dim iLevel As Integer
    iLevel = 0
    WalkHier iLevel, adoRS
                          
End Sub

Sub WalkHier(ByVal iLevel As Integer, ByVal adoRS As ADODB.Recordset)
    iLevel = iLevel + 1
    PriorLevel = iLevel
    While Not adoRS.EOF
        For ndx = 0 To adoRS.Fields.Count - 1
            If adoRS.Fields(ndx).Name &lt;&gt; "$Text" Then
                If adoRS.Fields(ndx).Type = adChapter Then
                    Set adoChildRS = adoRS.Fields(ndx).Value
                    WalkHier iLevel, adoChildRS
                Else
                    Debug.Print iLevel &amp; ": adoRS.Fields(" &amp; ndx &amp; _
                       ") = " &amp; adoRS.Fields(ndx).Name &amp; " = " &amp; _
                       adoRS.Fields(ndx).Value
                End If
            End If
        Next ndx
        adoRS.MoveNext
    Wend
    iLevel = PriorLevel
End Sub</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>