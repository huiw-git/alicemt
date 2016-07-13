---
title: Trace DLL
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Trace DLL
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The DLL that performs tracing is one of the ODBC core components. The trace DLL is currently provided as a sample DLL in the ODBC component of the Windows SDK, and was formerly included the Microsoft Data Access Components (MDAC) SDK. Therefore, the registry entry, interface, and sample code for the trace DLL are available. This DLL can be replaced by a trace DLL produced by either an ODBC user or a third-party vendor. A custom trace DLL should be given a different name than the original sample trace DLL. Trace DLLs must be installed in the system directory, or they will fail to load. The connection strings will not be passed to the trace DLL by the Driver Manager.</para>
    <para>The trace DLL traces input arguments, output arguments, deferred arguments, return codes, and SQLSTATEs. When tracing is enabled, the Driver Manager calls the trace DLL at two points: once upon function entry (before argument validation) and again just before the function returns.</para>
    <para>When an application calls a function, the Driver Manager calls a trace function in the trace DLL before calling the function in the driver or processing the call itself. Each ODBC function has a corresponding trace function (prefixed with <legacyItalic>Trace</legacyItalic>) that is identical to the ODBC function with the exception of the name. When the trace function is called, the trace DLL captures the input arguments and returns a return code. Because the trace DLL is called before the Driver Manager validates arguments, invalid function calls are traced, so state transition errors and invalid arguments are logged.</para>
    <para>After calling the trace function in the trace DLL, the Driver Manager calls the ODBC function in the driver. It then calls <legacyBold>TraceReturn</legacyBold> in the trace DLL. This function takes two arguments: the value returned by the trace DLL for the trace function, and the return code returned by the driver to the Driver Manager for the ODBC function (or the value returned by the Driver Manager itself if it processed the function). The function uses the value returned for the trace function to manipulate captured input argument values. It writes the code returned for the ODBC function to the log file (or displays it dynamically, if that is enabled). It dereferences the output argument pointers and logs the output argument values.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>