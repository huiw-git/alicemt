---
title: "Catalog Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3aae1107-2f81-413c-8eda-ef96c3df1b8a
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
# Catalog Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This Visual Basic project creates a new cube using MDX. Then, it documents the structure of a cube in a Microsoft Word document.</para>
  </introduction>
  <section>
    <content>
      <code>Private Sub cmdCreateDocForCube_Click()
Dim cn As ADODB.Connection
Dim s As String
Dim strProvider As String
Dim strDataSource As String
Dim strSourceDSN As String
Dim strSourceDSNSuffix As String
Dim strCreateCube As String
Dim strInsertInto As String

On Error GoTo Error_cmdCreateDocForCube_Click

'*-----------------------------------------------------------------------
'* The following code builds a cube file then documents the properties 
'* with an OLE Connection to Word 8.0
'*-----------------------------------------------------------------------

'*-----------------------------------------------------------------------
'* Add Provider to the connection string.
'*-----------------------------------------------------------------------
strProvider = "PROVIDER=MSOLAP"

'*-----------------------------------------------------------------------
'* Add DataSource, the name of the file we will create.
'*-----------------------------------------------------------------------

strDataSource = "DATA SOURCE=c:\DocumentCube.cub"

'*-----------------------------------------------------------------------
'* Add Source DSN, the connection string for where the data comes from.
'* We need to quote the value so it is parsed as one value.
'* This can either be an ODBC connection string or an OLE DB connection 
'* string. (As returned by the Data Source Locator component.)
'*-----------------------------------------------------------------------

strSourceDSN = "SOURCE_DSN=FoodMart"

'*-----------------------------------------------------------------------
'* We may have some other parameters that we want applied at run time, 
'* but not stored in the cube file, or returned in the output string.
'*-----------------------------------------------------------------------


'*-----------------------------------------------------------------------
'* Add CREATE CUBE.  This defines the structure of the cube, but not the 
'* data in it. The BNF for is documented in the OLE DB for OLAP 
'* Programmer's Reference. Note that we can quote names with either 
'* double quotes or square brackets.
'*-----------------------------------------------------------------------

strCreateCube = "CREATECUBE=CREATE CUBE Sample( "
strCreateCube = strCreateCube &amp; "DIMENSION [Product],"
        strCreateCube = strCreateCube &amp; "LEVEL [All Products]  TYPE ALL,"
        strCreateCube = strCreateCube &amp; "LEVEL [Product Family] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Product Department] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Product Category] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Product Subcategory] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Brand Name] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Product Name] ,"
strCreateCube = strCreateCube &amp; "DIMENSION [Store],"
        strCreateCube = strCreateCube &amp; "LEVEL [All Stores]  TYPE ALL,"
        strCreateCube = strCreateCube &amp; "LEVEL [Store Country] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Store State] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Store City] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Store Name] ,"
strCreateCube = strCreateCube &amp; "DIMENSION [Store Type],"
        strCreateCube = strCreateCube &amp; _
            "LEVEL [All Store Type]  TYPE ALL,"
        strCreateCube = strCreateCube &amp; "LEVEL [Store Type] ,"
strCreateCube = strCreateCube &amp; "DIMENSION [Time] TYPE TIME,"
    strCreateCube = strCreateCube &amp; "HIERARCHY [Column],"
        strCreateCube = strCreateCube &amp; "LEVEL [All Time]  TYPE ALL,"
        strCreateCube = strCreateCube &amp; "LEVEL [Year]  TYPE YEAR,"
        strCreateCube = strCreateCube &amp; "LEVEL [Quarter]  TYPE QUARTER,"
        strCreateCube = strCreateCube &amp; "LEVEL [Month]  TYPE MONTH,"
        strCreateCube = strCreateCube &amp; "LEVEL [Week]  TYPE WEEK,"
        strCreateCube = strCreateCube &amp; "LEVEL [Day]  TYPE DAY,"
    strCreateCube = strCreateCube &amp; "HIERARCHY [Formula],"
        strCreateCube = strCreateCube &amp; _
            "LEVEL [All Formula Time]  TYPE ALL,"
        strCreateCube = strCreateCube &amp; "LEVEL [Year]  TYPE YEAR,"
        strCreateCube = strCreateCube &amp; "LEVEL [Quarter]  TYPE QUARTER,"
        strCreateCube = strCreateCube &amp; _
            "LEVEL [Month]  TYPE MONTH OPTIONS (SORTBYKEY) ,"
strCreateCube = strCreateCube &amp; "DIMENSION [Warehouse],"
        strCreateCube = strCreateCube &amp; _
            "LEVEL [All Warehouses]  TYPE ALL,"
        strCreateCube = strCreateCube &amp; "LEVEL [Country] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [State Province] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [City] ,"
        strCreateCube = strCreateCube &amp; "LEVEL [Warehouse Name] ,"
strCreateCube = strCreateCube &amp; "MEASURE [Store Invoice] "
    strCreateCube = strCreateCube &amp; "Function Sum "
    strCreateCube = strCreateCube &amp; "Format '#.#',"
strCreateCube = strCreateCube &amp; "MEASURE [Supply Time] "
    strCreateCube = strCreateCube &amp; "Function Sum "
    strCreateCube = strCreateCube &amp; "Format '#.#',"
strCreateCube = strCreateCube &amp; "MEASURE [Warehouse Cost] "
    strCreateCube = strCreateCube &amp; "Function Sum "
    strCreateCube = strCreateCube &amp; "Format '#.#',"
strCreateCube = strCreateCube &amp; "MEASURE [Warehouse Sales] "
    strCreateCube = strCreateCube &amp; "Function Sum "
    strCreateCube = strCreateCube &amp; "Format '#.#',"
strCreateCube = strCreateCube &amp; "MEASURE [Units Shipped] "
    strCreateCube = strCreateCube &amp; "Function Sum "
    strCreateCube = strCreateCube &amp; "Format '#.#',"
strCreateCube = strCreateCube &amp; "MEASURE [Units Ordered] "
    strCreateCube = strCreateCube &amp; "Function Sum "
    strCreateCube = strCreateCube &amp; "Format '#.#')"
'*-----------------------------------------------------------------------
'* Add INSERT INTO.  This defines where the data comes from, and how it
'* maps into the already-defined cube structure.  Note that the SELECT 
'* clause might just be passed through to the relational database.
'* So I could pass in a stored procedure, for example.  If we needed to, 
'* we could quote this whole thing.  Note that the columns in the SELECT 
'* can be in any order.  One merely has to adjust the ordering of the 
'* list of level/measure names to match the SELECT ordering.
'*-----------------------------------------------------------------------
strInsertInto = strInsertInto &amp; 
    "INSERTINTO=INSERT INTO Sample( " &amp; _
        "Product.[Product Family], Product.[Product Department],"
strInsertInto = strInsertInto &amp; 
    "Product.[Product Category], Product.[Product Subcategory],"
strInsertInto = strInsertInto &amp; 
    "Product.[Brand Name], Product.[Product Name],"
strInsertInto = strInsertInto &amp; 
    "Store.[Store Country], Store.[Store State], Store.[Store City],"
strInsertInto = strInsertInto &amp; 
    "Store.[Store Name], [Store Type].[Store Type], [Time].[Column],"
strInsertInto = strInsertInto &amp; 
    "[Time].Formula.Year, [Time].Formula.Quarter, " &amp; _
        "[Time].Formula.Month.[Key],"
strInsertInto = strInsertInto &amp; 
    "[Time].Formula.Month.Name, Warehouse.Country, " &amp; _
        "Warehouse.[State Province],"
strInsertInto = strInsertInto &amp; 
    "Warehouse.City, Warehouse.[Warehouse Name], " * _
        "Measures.[Store Invoice],"
strInsertInto = strInsertInto &amp; 
    "Measures.[Supply Time], Measures.[Warehouse Cost], " &amp; _
        "Measures.[Warehouse Sales],"
strInsertInto = strInsertInto &amp; 
    "Measures.[Units Shipped], Measures.[Units Ordered] )"
'*-----------------------------------------------------------------------
'* Add some options to the INSERT INTO if we need to.  These can control 
'* if the SELECT clause is analyzed or just passed through, and if the 
'* storage mode is MOLAP or ROLAP (DEFER_DATA).
'* strInsertInto = strInsertInto &amp; " OPTIONS ATTEMPT_ANALYSIS"
'*-----------------------------------------------------------------------

'*-----------------------------------------------------------------------
'* Add the SELECT clause of the INSERT INTO statement.  Note that it is 
'* merely concatenated onto the end of the INSERT INTO statement.  OLAP 
'* Services will pass this through to the source database if unable to 
'* parse it.  Note that for OLAP Services to analyze the SELECT clause, 
'* each column must be qualified with the table name.
'*-----------------------------------------------------------------------

strInsertInto = strInsertInto &amp; 
    "SELECT product_class.product_family AS Col1,"
strInsertInto = strInsertInto &amp; 
    "product_class.product_department AS Col2,"
strInsertInto = strInsertInto &amp; "product_class.product_category AS Col3,"
strInsertInto = strInsertInto &amp; 
    "product_class.product_subcategory AS Col4,"
strInsertInto = strInsertInto &amp; "product.brand_name AS Col5,"
strInsertInto = strInsertInto &amp; "product.product_name AS Col6,"
strInsertInto = strInsertInto &amp; "store.store_country AS Col7,"
strInsertInto = strInsertInto &amp; "store.store_state AS Col8,"
strInsertInto = strInsertInto &amp; "store.store_city AS Col9,"
strInsertInto = strInsertInto &amp; "store.store_name AS Col10,"
strInsertInto = strInsertInto &amp; "store.store_type AS Col11,"
strInsertInto = strInsertInto &amp; "time_by_day.the_date AS Col12,"
strInsertInto = strInsertInto &amp; "time_by_day.the_year AS Col13,"
strInsertInto = strInsertInto &amp; "time_by_day.quarter AS Col14,"
strInsertInto = strInsertInto &amp; "time_by_day.month_of_year AS Col15,"
strInsertInto = strInsertInto &amp; "time_by_day.the_month AS Col16,"
strInsertInto = strInsertInto &amp; "warehouse.warehouse_country AS Col17,"
strInsertInto = strInsertInto &amp; 
    "warehouse.warehouse_state_province AS Col18,"
strInsertInto = strInsertInto &amp; "warehouse.warehouse_city AS Col19,"
strInsertInto = strInsertInto &amp; "warehouse.warehouse_name AS Col20,"
strInsertInto = strInsertInto &amp; 
    "inventory_fact_1997.store_invoice AS Col21,"
strInsertInto = strInsertInto &amp; 
    "inventory_fact_1997.supply_time AS Col22,"
strInsertInto = strInsertInto &amp; 
    "inventory_fact_1997.warehouse_cost AS Col23,"
strInsertInto = strInsertInto &amp; 
    "inventory_fact_1997.warehouse_sales AS Col24,"
strInsertInto = strInsertInto &amp; 
    "inventory_fact_1997.units_shipped AS Col25,"
strInsertInto = strInsertInto &amp; 
    "inventory_fact_1997.units_ordered AS Col26 "
strInsertInto = strInsertInto &amp; 
    "From [inventory_fact_1997], [product], [product_class], " &amp;_
        "[time_by_day], [store], [warehouse] "
strInsertInto = strInsertInto &amp; 
    "Where [inventory_fact_1997].[product_id] = [product]." &amp;_
        "[product_id] And "
strInsertInto = strInsertInto &amp; 
    "[product].[product_class_id] = [product_class]." &amp;_
        "[product_class_id] And "
strInsertInto = strInsertInto &amp; 
    "[inventory_fact_1997].[time_id] = [time_by_day].[time_id] And "
strInsertInto = strInsertInto &amp; 
    "[inventory_fact_1997].[store_id] = [store].[store_id] And "
strInsertInto = strInsertInto &amp; 
    "[inventory_fact_1997].[warehouse_id] = [warehouse].[warehouse_id]"

'*-----------------------------------------------------------------------
'* Create the cube by passing connection string to Open.
'*-----------------------------------------------------------------------

Set cn = New ADODB.Connection
s = strProvider &amp; ";" &amp; strDataSource &amp; ";" &amp; strSourceDSN &amp; ";" &amp; _
    strCreateCube &amp; ";" &amp; strInsertInto &amp; ";"
Screen.MousePointer = vbHourglass
cn.Open s

'*-----------------------------------------------------------------------
'* Cube file is written to hard drive a Word Document can be produced by 
'* automating Word with VB
'*-----------------------------------------------------------------------

Dim cat As New ADOMD.<codeFeaturedElement>Catalog</codeFeaturedElement>
Dim cdf As ADOMD.<codeFeaturedElement>CubeDef</codeFeaturedElement>
Dim di As Integer
Dim hi As Integer
Dim le As Integer
Dim mem As Integer
Dim docWord As Word.Document
Dim rngCurrent As Word.Range
Dim SenCount As Integer
Dim strServer As String
Dim strSource As String
Dim strCubeName As String

'*-----------------------------------------------------------------------
'* Connection is made to cube file
'*-----------------------------------------------------------------------
cat.<codeFeaturedElement>ActiveConnection</codeFeaturedElement> = "DATA SOURCE=c:\DocumentCube.cub;Provider=msolap;"

'*-----------------------------------------------------------------------
'* Cube Definition is set to Name of Cube in cube file
'*-----------------------------------------------------------------------
Set cdf = cat.<codeFeaturedElement>CubeDefs</codeFeaturedElement>("Sample")

'*-----------------------------------------------------------------------
'* Object is created to hold Word 8.0
'*-----------------------------------------------------------------------
Set appword = CreateObject("Word.Application.8")

'*-----------------------------------------------------------------------
'* Create the document variable
'*-----------------------------------------------------------------------
   Set docWord = appword.Documents.Add()

   Set rngCurrent = docWord.Content

   SenCount = 0

'*-----------------------------------------------------------------------
'* Cube Title and Header written to Document
'*-----------------------------------------------------------------------
   With rngCurrent
       .InsertAfter "Report for Sample Cube"
       .InsertAfter vbCrLf
       SenCount = SenCount + 1
       docWord.Paragraphs(SenCount).Range.Bold = True
       docWord.Paragraphs(SenCount).Range.Underline = wdUnderlineSingle
       docWord.Paragraphs(SenCount).Range.Italic = False
       docWord.Paragraphs(SenCount).Range.Font.Size = 18

'*-----------------------------------------------------------------------
'* Properties of Cube are written to Document
'*-----------------------------------------------------------------------
For i = 0 To cdf.<codeFeaturedElement>Properties</codeFeaturedElement>.Count - 1
    .InsertAfter "(" &amp; i &amp; ") " &amp; cdf.Properties(i).Name &amp; ": " &amp; _
        cdf.Properties(i).Value
    .InsertAfter vbCrLf
    SenCount = SenCount + 1
    docWord.Paragraphs(SenCount).Range.Bold = False
    docWord.Paragraphs(SenCount).Range.Italic = True
    docWord.Paragraphs(SenCount).Range.Font.Size = 8
Next i

'*-----------------------------------------------------------------------
'* Dimension Name(s) written to Document
'*-----------------------------------------------------------------------
    For di = 0 To cdf.<codeFeaturedElement>Dimensions</codeFeaturedElement>.Count - 1
    .InsertAfter "Dimension: " &amp; cdf.Dimensions(di).Name
    .InsertAfter vbCrLf
    SenCount = SenCount + 1
    docWord.Paragraphs(SenCount).Range.Bold = True
    docWord.Paragraphs(SenCount).Range.Italic = False
    docWord.Paragraphs(SenCount).Range.Font.Size = 14

'*-----------------------------------------------------------------------
'* Properties of Dimension are written to Document
'*-----------------------------------------------------------------------
    For i = 0 To cdf.Dimensions(di).<codeFeaturedElement>Properties</codeFeaturedElement>.Count - 1
        .InsertAfter "(" &amp; i &amp; ") " &amp; _
            cdf.Dimensions(di).Properties(i).Name &amp; ": " &amp; _
            cdf.Dimensions(di).Properties(i).Value
        .InsertAfter vbCrLf
        SenCount = SenCount + 1
        docWord.Paragraphs(SenCount).Range.Bold = False
        docWord.Paragraphs(SenCount).Range.Italic = True
        docWord.Paragraphs(SenCount).Range.Font.Size = 8
    Next i

'*-----------------------------------------------------------------------
'* Hierarchy Name(s) written to Document
'*-----------------------------------------------------------------------
    For hi = 0 To cdf.Dimensions(di).<codeFeaturedElement>Hierarchies</codeFeaturedElement>.Count - 1
        .InsertAfter vbTab &amp; "Hierarchy: " &amp; _
            cdf.Dimensions(di).Hierarchies(hi).Name
        .InsertAfter vbCrLf
        SenCount = SenCount + 1
        docWord.Paragraphs(SenCount).Range.Bold = True
        docWord.Paragraphs(SenCount).Range.Italic = False
        docWord.Paragraphs(SenCount).Range.Font.Size = 12

'*-----------------------------------------------------------------------
'* Properties of Hierarchy are written to Document
'*-----------------------------------------------------------------------
    For i = 0 To cdf.Dimensions(di).Hierarchies(hi).<codeFeaturedElement>Properties</codeFeaturedElement>.Count - 1
        .InsertAfter vbTab &amp; "(" &amp; i &amp; ") " &amp; _
            cdf.Dimensions(di).Hierarchies(hi).Properties(i).Name &amp; _
            ": " &amp; cdf.Dimensions(di).Hierarchies(hi).Properties(i).Value
        .InsertAfter vbCrLf
        SenCount = SenCount + 1
        docWord.Paragraphs(SenCount).Range.Bold = False
        docWord.Paragraphs(SenCount).Range.Italic = True
        docWord.Paragraphs(SenCount).Range.Font.Size = 8
    Next i

'*-----------------------------------------------------------------------
'* Level Name(s) written to Document
'*-----------------------------------------------------------------------
    For le = 0 To cdf.Dimensions(di).Hierarchies(hi).<codeFeaturedElement>Levels</codeFeaturedElement>.Count - 1
        .InsertAfter vbTab &amp; vbTab &amp; "Level: " &amp; _
            cdf.Dimensions(di).Hierarchies(hi).Levels(le).Name &amp; _
            " with a Member Count of: " &amp; _
            cdf.Dimensions(di).Hierarchies(hi).Levels(le).<codeFeaturedElement>Members</codeFeaturedElement>.Count
        .InsertAfter vbCrLf
        SenCount = SenCount + 1
        docWord.Paragraphs(SenCount).Range.Bold = True
        docWord.Paragraphs(SenCount).Range.Italic = False
        docWord.Paragraphs(SenCount).Range.Font.Size = 10

'*-----------------------------------------------------------------------
'* Properties of Level are written to Document
'*-----------------------------------------------------------------------
    For i = 0 To 
       cdf.Dimensions(di).Hierarchies(hi).Levels(le).<codeFeaturedElement>Properties</codeFeaturedElement>.Count - 1
        .InsertAfter vbTab &amp; vbTab &amp; "(" &amp; i &amp; ") " &amp; _
             cdf.Dimensions(di).Hierarchies(hi).Levels(le)._
                 Properties(i).Name &amp; ": " &amp; _
             cdf.Dimensions(di).Hierarchies(hi).Levels(le)._
                 Properties(i).Value
        .InsertAfter vbCrLf
        SenCount = SenCount + 1
        docWord.Paragraphs(SenCount).Range.Bold = False
        docWord.Paragraphs(SenCount).Range.Italic = True
        docWord.Paragraphs(SenCount).Range.Font.Size = 8
    Next i

    Next le
    Next hi
    Next di

'*-----------------------------------------------------------------------
'* Set Word Document to visible
'*-----------------------------------------------------------------------
        appword.Visible = True
    End With
   Screen.MousePointer = vbDefault

'*-----------------------------------------------------------------------
'* Set Word Object to nothing to drop OLE connection
'*-----------------------------------------------------------------------
   Set appword = Nothing
Exit Sub

Error_cmdCreateDocForCube_Click:
    Screen.MousePointer = vbDefault
    MsgBox Err.Description
End Sub</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>