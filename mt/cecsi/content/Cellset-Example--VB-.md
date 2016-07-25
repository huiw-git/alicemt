---
title: "Cellset Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2666ad1c-b48e-4b2c-b269-5a9f4e4a7810
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
# Cellset Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This Visual Basic project demonstrates the basics of using ADO MD to access cube data. It displays member captions for column and row headers, then displays formatted values of specific cells within the cellset.</para>
  </introduction>
  <section>
    <content>
      <code>Private Sub cmdCellSettoDebugWindow_Click()
Dim cat As New ADOMD.<codeFeaturedElement>Catalog</codeFeaturedElement>
Dim cst As New ADOMD.<codeFeaturedElement>Cellset</codeFeaturedElement>
Dim i As Integer
Dim j As Integer
Dim strServer As String
Dim strSource As String
Dim strColumnHeader As String
Dim strRowText As String

On Error GoTo Error_cmdCellSettoDebugWindow_Click
Screen.MousePointer = vbHourglass
'*-----------------------------------------------------------------------
'* Set Server to Local Host
'*-----------------------------------------------------------------------
    strServer = "LOCALHOST"

'*-----------------------------------------------------------------------
'* Set MDX query string Source
'*-----------------------------------------------------------------------
    strSource = strSource &amp; "SELECT "
    strSource = strSource &amp; "{[Measures].members} ON COLUMNS,"
    strSource = strSource &amp; _
        "NON EMPTY [Store].[Store City].members ON ROWS"
    strSource = strSource &amp; " FROM Sales"

'*-----------------------------------------------------------------------
'* Set Active Connection
'*-----------------------------------------------------------------------
        cat.ActiveConnection = "Data Source=" &amp; strServer &amp; _
            ";Provider=msolap;"

'*-----------------------------------------------------------------------
'* Set Cell Set source to MDX query string
'*-----------------------------------------------------------------------
        cst.<codeFeaturedElement>Source</codeFeaturedElement> = strSource

'*-----------------------------------------------------------------------
'* Set Cell Sets active connection to current connection
'*-----------------------------------------------------------------------
    Set cst.<codeFeaturedElement>ActiveConnection</codeFeaturedElement> = cat.<codeFeaturedElement>ActiveConnection</codeFeaturedElement>

'*-----------------------------------------------------------------------
'* Open Cell Set
'*-----------------------------------------------------------------------
    cst.<codeFeaturedElement>Open</codeFeaturedElement>

'*-----------------------------------------------------------------------
'* Allow space for Row Header Text
'*-----------------------------------------------------------------------
strColumnHeader = vbTab &amp; vbTab &amp; vbTab &amp; vbTab &amp; vbTab &amp; vbTab

'*-----------------------------------------------------------------------
'* Loop through Column Headers
'*-----------------------------------------------------------------------
       For i = 0 To cst.<codeFeaturedElement>Axes</codeFeaturedElement>(0).<codeFeaturedElement>Positions</codeFeaturedElement>.Count - 1
            strColumnHeader = strColumnHeader &amp; _
                cst.Axes(0).Positions(i).<codeFeaturedElement>Members</codeFeaturedElement>(0).<codeFeaturedElement>Caption</codeFeaturedElement> &amp; vbTab &amp; _
                    vbTab &amp; vbTab &amp; vbTab
       Next
       Debug.Print vbTab &amp; strColumnHeader &amp; vbCrLf

'*-----------------------------------------------------------------------
'* Loop through Row Headers and Provide data for each row
'*-----------------------------------------------------------------------
        strRowText = ""
        For j = 0 To cst.<codeFeaturedElement>Axes</codeFeaturedElement>(1).<codeFeaturedElement>Positions</codeFeaturedElement>.Count - 1
            strRowText = strRowText &amp; _
                cst.Axes(1).Positions(j).<codeFeaturedElement>Members</codeFeaturedElement>(0).<codeFeaturedElement>Caption</codeFeaturedElement> &amp; vbTab &amp; _
                    vbTab &amp; vbTab &amp; vbTab
            For k = 0 To cst.<codeFeaturedElement>Axes</codeFeaturedElement>(0).<codeFeaturedElement>Positions</codeFeaturedElement>.Count - 1
                strRowText = strRowText &amp; cst(k, j).<codeFeaturedElement>FormattedValue</codeFeaturedElement> &amp; _
                    vbTab &amp; vbTab &amp; vbTab &amp; vbTab
            Next
            Debug.Print strRowText &amp; vbCrLf
            strRowText = ""
        Next

    Screen.MousePointer = vbDefault
Exit Sub

Error_cmdCellSettoDebugWindow_Click:
   Beep
   Screen.MousePointer = vbDefault
   MsgBox "The Following Error has occurred:" &amp; vbCrLf &amp; _
      Err.Description, vbCritical, " Error!"
   Exit Sub
End Sub</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>