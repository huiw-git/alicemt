---
title: "Running the Address Book Sample Application"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a2644e9-d634-4ae6-a5b7-13fb7b317ec7
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
# Running the Address Book Sample Application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>To run the Address Book application, follow this procedure.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <procedure>
      <title>To run this application</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Make sure that Microsoft SQL Server is running. Click <legacyBold>Start</legacyBold>, point to <legacyBold>Programs</legacyBold>, point to <legacyBold>Microsoft SQL Server 7.0</legacyBold>, and then click <legacyBold>Service Manager</legacyBold>. If there is a green arrow in the white circle, then SQL Server is running. If it is not (there will be a red square in the white circle), click <legacyBold>Start/Continue</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In Microsoft Internet Explorer 4.0 or later, type the following address: </para>
            <para>                 <legacyBold>http://</legacyBold>                 <legacyItalic>webserver</legacyItalic>                 <legacyBold>/RDS/AddressBook/AddrBook.asp</legacyBold>               </para>
            <para>where <legacyItalic>webserver</legacyItalic> is the name of the Web server where the RDS server components are installed. </para>
          </content>
        </step>
        <step>
          <content>
            <para>You can then try various scenarios in the Address Book sample application, such as searching for a person based on his or her e-mail name, listing all people with the title "Program Manager," or editing existing records. Click <legacyBold>Find</legacyBold> to fill the data grid with all the available names. </para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics>
<link xlink:href="080c1925-d453-4b89-92ac-c93591490518">Address Book Data-Binding Object</link>
</relatedTopics>
</developerConceptualDocument>