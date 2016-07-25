---
title: "RDS Tutorial (Visual J++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0d735e0-669a-41e7-ada2-8dd80924e349
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
# RDS Tutorial (Visual J++)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO/WFC does not completely follow the RDS object model in that it does not implement the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object. ADO/WFC implements only the client-side class, <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink>.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The <legacyBold>DataSpace</legacyBold> class implements one method, <legacyLink xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject</legacyLink>, which returns an <legacyLink xlink:href="f68f58bc-ad28-46cc-9fb3-099e1a678397">ObjectProxy</legacyLink> object. The <legacyBold>DataSpace</legacyBold> class also implements the <legacyLink xlink:href="4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549">InternetTimeout</legacyLink> property.</para>
    <para>The <legacyBold>ObjectProxy</legacyBold> class implements one method, call, which can invoke any server-side business object.</para>
    <para>         <legacyBold>This is the beginning of the tutorial.</legacyBold>       </para>
    <code>import com.ms.wfc.data.*;
public class RDSTutorial 
{
   public void tutorial()
   {
// Step 1: Specify a server program.
      ObjectProxy obj = 
         DataSpace.createObject(
            "RDSServer.DataFactory", 
            "http://YourServer");

// Step 2: Server returns a Recordset. 
      Recordset rs = (Recordset) obj.call(
            "Query", 
            new Object[] {"DSN=Pubs;", "SELECT * FROM Authors"});

// Step 3: Changes are sent to the server. 
      ...                        // Edit Recordset.
      obj.call(
            "SubmitChanges", 
            new Object[] {"DSN=Pubs;", rs});   
      return;
   }
}</code>
    <para>         <legacyBold>This is the end of the tutorial.</legacyBold>       </para>
  </introduction>
  <relatedTopics>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
<link xlink:href="e2a48c4d-88b1-43ff-a202-9cdec54997d2">RDS Tutorial (VBScript)</link>
</relatedTopics>
</developerConceptualDocument>