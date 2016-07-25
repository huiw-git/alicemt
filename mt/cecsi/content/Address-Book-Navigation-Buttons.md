---
title: "Address Book Navigation Buttons"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277
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
# Address Book Navigation Buttons
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Address Book application displays the navigation buttons at the bottom of the Web page. You can use the navigation buttons to navigate through the data in the HTML grid display by selecting either the first or last row of data, or rows adjacent to the current selection.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Navigation Sub Procedures</title>
    <content>
      <para>The Address Book application contains several procedures that allow users to click the <legacyBold>First</legacyBold>, <legacyBold>Next</legacyBold>, <legacyBold>Previous</legacyBold>, and <legacyBold>Last</legacyBold> buttons to move around the data.</para>
      <para>For example, clicking the <legacyBold>First</legacyBold> button activates the VBScript First_OnClick Sub procedure. The procedure executes a <legacyLink xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveFirst</legacyLink> method, which makes the first row of data the current selection. Clicking the <legacyBold>Last</legacyBold> button activates the Last_OnClick Sub procedure, which invokes the <legacyLink xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveLast</legacyLink> method, making the last row of data the current selection. The remaining navigation buttons work in a similar fashion. </para>
      <code>' Move to the first record in the bound Recordset.
Sub First_OnClick
   DC1.Recordset.MoveFirst
End Sub

' Move to the next record from the current position 
' in the bound Recordset.
Sub Next_OnClick
   If Not DC1.Recordset.EOF Then    ' Cannot move beyond bottom record.
      DC1.Recordset.MoveNext
      Exit Sub
   End If   
End Sub

' Move to the previous record from the current position in the bound 
' Recordset.
Sub Prev_OnClick
   If Not DC1.Recordset.BOF Then    ' Cannot move beyond top record.
      DC1.Recordset.MovePrevious
      Exit Sub
   End If
End Sub

' Move to the last record in the bound Recordset.
Sub Last_OnClick
   DC1.Recordset.MoveLast
End Sub</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="45c80bb5-136f-4204-9df2-78740fa55574">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)</link>
</relatedTopics>
</developerConceptualDocument>