---
title: Physical Architecture (Analysis Services - Data Mining)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25eeecf0-6e85-4527-b94d-5503d27edaed
---
# Physical Architecture (Analysis Services - Data Mining)
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] uses both server and client components to supply data mining functionality for business intelligence applications:  
  
-   The server component is implemented as a Microsoft Windows service. You can have multiple instances on the same computer, with each instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] implemented as a separate instance of the Windows service.  
  
-   Clients communicate with [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] using the public standard XML for Analysis \(XMLA\), a SOAP\-based protocol for issuing commands and receiving responses, exposed as a Web service. Client object models are also provided over XMLA, and can be accessed either by using a managed provider, such as ADOMD.NET, or a native OLE DB provider.  
  
-   Query commands can be issued using Data Mining Extensions \(DMX\), an industry standard query language oriented toward data mining. Analysis Services Scripting Language \(ASSL\) can also be used to manage [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database objects.  
  
## Architectural Diagram  
 An [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance runs as a stand\-alone service and communication with the service occurs through XML for Analysis \(XMLA\), by using either HTTP or TCP.  
  
 AMO is a layer between the user application and the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance that provides access to [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] administrative objects. AMO is a class library that takes commands from a client application and converts those commands into XMLA messages for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance. AMO presents [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance objects as classes to the end user application, with method members that run commands and property members that hold the data for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] objects.  
  
 The following illustration shows the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] components architecture, including services within the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance and user components that interact with the instance.  
  
 The illustration shows that the only way to access the instance is by using the XML for Analysis \(XMLA\) Listener, either by using HTTP or TCP.  
  
> [!WARNING]  
>  DSO has been deprecated. You should not use DSO to develop solutions.  
  
 ![Analysis Services System Architecture Diagram](../../Images\Image\ImageNotContaina/AnalysisServicesSystemArchitecture.gif "AnalysisServicesSystemArchitecture")  
  
## Server Configuration  
 One server instance can support multiple [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] databases, each with its own instance of the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] service that responds to client requests and processes objects.  
  
 Separate instances must be installed if you want to work with both tabular models and data mining and\/or multidimensional models. [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] supports side\-by\-side installation of instances running in tabular mode \(which uses the xVelocity in\-memory analytics engine \(VertiPaq\) storage engine\) and instances running in one of the conventional OLAP, MOLAP, or ROLAP configurations. For more information, see [Determine the Server Mode of an Analysis Services Instance](../../Topics\TopicNameNotContainA/Determine-the-Server-Mode-of-an-Analysis-Services-Instance.md).  
  
 All communications between a client and the Analysis Services server use XMLA, which is a platform\-independent and language\-independent protocol. When a request is received from a client, Analysis Services determines whether the request relates to OLAP or data mining, and routes the request appropriately. For more information, see [OLAP Engine Server Components](../Topic/OLAP%20Engine%20Server%20Components.md).  
  
## See Also  
 [Logical Architecture &#40;Analysis Services - Data Mining&#41;](../Topic/Logical%20Architecture%20\(Analysis%20Services%20-%20Data%20Mining\).md)  
  
  