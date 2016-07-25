---
title: "Granting Guest Privileges to a Web Server Computer"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
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
# Granting Guest Privileges to a Web Server Computer
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The anonymous Web server account (IUSR_<legacyItalic>ComputerName</legacyItalic>) must be added to the Guests local group on the Web server computer to use RDS.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <procedure>
      <title>To grant guest privileges to a Web server computer</title>
      <steps class="ordered">
        <step>
          <content>
            <para>On your Microsoft Windows 2000 Server computer, click <legacyBold>Start</legacyBold>, point to <legacyBold>Programs</legacyBold>, point to <legacyBold>Administrative Tools</legacyBold>, and then click <legacyBold>Computer Management</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the console tree, in <legacyBold>Local Users and Groups</legacyBold>, click <legacyBold>Groups</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select the <legacyBold>Guests</legacyBold> local group. From the <legacyBold>Action</legacyBold> menu, choose <legacyBold>Properties</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the <legacyBold>Guests Properties</legacyBold> dialog box, click <legacyBold>Add</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>If the anonymous Web server account does not appear in the list in the <legacyBold>Select Users or Groups</legacyBold> dialog box, type its name (IUSR_<legacyItalic>ComputerName</legacyItalic>) into the bottom blank box, and then click <legacyBold>Add</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Click <legacyBold>OK</legacyBold>.</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>