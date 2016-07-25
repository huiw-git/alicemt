---
title: "Microsoft ActiveX Data Objects (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fa6237b-44b8-4b6c-9952-5acd80a54e20
caps.latest.revision: 18
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
# Microsoft ActiveX Data Objects (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ActiveX Data Objects (ADO) consists of the following components:</para>
  </introduction>
  <section>
    <title>ADO</title>
    <content>
      <para>Microsoft ActiveX Data Objects (ADO) enable your client applications to access and manipulate data from a variety of sources through an OLE DB provider. Its primary benefits are ease of use, high speed, low memory overhead, and a small disk footprint. ADO supports key features for building client/server and Web-based applications.</para>
    </content>
  </section>
  <section>
    <title>ADO MD</title>
    <content>
      <para>Microsoft ActiveX Data Objects (Multidimensional) (ADO MD) provides easy access to multidimensional data from languages such as Microsoft Visual Basic, Microsoft Visual C++, and Microsoft Visual J++. ADO MD extends Microsoft ActiveX Data Objects (ADO) to include objects specific to multidimensional data, such as the CubeDef and Cellset objects. With ADO MD you can browse multidimensional schema, query a cube, and retrieve the results.</para>
      <para>Like ADO, ADO MD uses an underlying OLE DB provider to gain access to data. To work with ADO MD, the provider must be a multidimensional data provider (MDP) as defined by the OLE DB for OLAP specification. MDPs present data in multidimensional views as opposed to tabular data providers (TDPs) that present data in tabular views. Refer to the documentation for your OLAP OLE DB provider for more detailed information about the specific syntax and behaviors supported by your provider.</para>
    </content>
  </section>
  <section>
    <title>RDS</title>
    <content>
      <para>Remote Data Service (RDS) is a feature of ADO, with which you can move data from a server to a client application or Web page, manipulate the data on the client, and return updates to the server in a single round trip.</para>
      <alert class="important">
        <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to  <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>ADOX</title>
    <content>
      <para>Microsoft ActiveX Data Objects Extensions for Data Definition Language and Security (ADOX) is an extension to the ADO objects and programming model. ADOX includes objects for schema creation and modification, as well as security. Because it is an object-based approach to schema manipulation, you can write code that will work against various data sources regardless of differences in their native syntaxes.</para>
      <para>ADOX is a companion library to the core ADO objects. It exposes additional objects for creating, modifying, and deleting schema objects, such as tables and procedures. It also includes security objects to maintain users and groups and to grant and revoke permissions on objects.</para>
    </content>
  </section>
  <section>
    <title>Documentation</title>
    <content>
      <para>
        <link xlink:href="86b83a38-efdf-4831-a6d5-7e470d517d1c">ADO 2.8 Security Design Issues and Changes</link>
      </para>
      <para>
        <link xlink:href="e3c50eee-964a-4abd-810d-1bd51978e814">Programmer's Guide</link>
      </para>
      <para>An introduction to using ADO, RDS, ADO MD, and ADOX.</para>
      <para>
        <link xlink:href="6dc27c85-84e1-472a-b057-d1854b8c98a3">Programmer's Reference</link>
      </para>
      <para>This section of the ADO documentation contains topics for each ADO, RDS, ADO MD, and ADOX object, collection, property, dynamic property, method, event, and enumeration.</para>
      <para>
        <link xlink:href="b0478836-4123-4357-969a-c5784fc28be5">ADO Glossary</link>
      </para>
    </content>
  </section>
  <section>
    <title>Support</title>
    <content>
      <para>For free help with ADO issues, try posting to the ADO public newsgroup. This newsgroup is monitored by Microsoft Product Support Services (PSS) support professionals who cover ADO, and by other experienced ADO developers.</para>
      <para>Further information about support options can be found on the Microsoft Help and Support Web site.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>