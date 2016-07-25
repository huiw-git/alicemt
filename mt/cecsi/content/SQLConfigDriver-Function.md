---
title: "SQLConfigDriver Function"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLConfigDriver
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 4f681961-ac9f-4d88-b065-5258ba112642
caps.latest.revision: 11
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLConfigDriver Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 2.5</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLConfigDriver</legacyBold> loads the appropriate driver setup DLL and calls the <legacyBold>ConfigDriver</legacyBold> function.</para>
        <para>The functionality of <legacyBold>SQLConfigDriver</legacyBold> can also be accessed with <link xlink:href="3bf2be83-61f9-4183-836b-85204ac7116a">ODBCCONF.EXE</link>.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLConfigDriver</legacyBold>(
     HWND     <parameterReference>hwndParent</parameterReference>,
     WORD     <parameterReference>fRequest</parameterReference>,
     LPCSTR   <parameterReference>lpszDriver</parameterReference>,
     LPCSTR   <parameterReference>lpszArgs</parameterReference>,
     LPSTR    <parameterReference>lpszMsg</parameterReference>,
     WORD     <parameterReference>cbMsgMax</parameterReference>,
     WORD *   <parameterReference>pcbMsgOut</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hwndParent</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parent window handle. The function will not display any dialog boxes if the handle is null.</para>
        </definition>
        <definedTerm>
          <legacyItalic>fRequest</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Type of request. <legacyItalic>fRequest</legacyItalic> must contain one of the following values:</para>
          <para>ODBC_CONFIG_DRIVER: Changes the connection pooling timeout used by the driver.   </para>
          <para>ODBC_INSTALL_DRIVER: Installs a new driver.   </para>
          <para>ODBC_REMOVE_DRIVER: Removes an existing driver.   </para>
          <para>This option can also be driver-specific, in which case the <legacyItalic>fRequest</legacyItalic> for the first option must start from ODBC_CONFIG_DRIVER_MAX+1. The <legacyItalic>fRequest</legacyItalic> for any additional option must also start from a value greater than ODBC_CONFIG_DRIVER_MAX+1. </para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszDriver</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The name of the driver as registered in the system information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszArgs</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A null-terminated string that contains arguments for a driver-specific <legacyItalic>fRequest</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>lpszMsg</legacyItalic></definedTerm>
        <definition>
          <para>[Output] A null-terminated string that contains an output message from the driver setup.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbMsgMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>lpszMsg.</legacyItalic></para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbMsgOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes available to return in <legacyItalic>lpszMsg</legacyItalic>. If the number of bytes available to return is greater than or equal to <legacyItalic>cbMsgMax</legacyItalic>, the output message in <legacyItalic>lpszMsg</legacyItalic> is truncated to <legacyItalic>cbMsgMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbMsgOut</legacyItalic> argument can be a null pointer.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>The function returns TRUE if it is successful, FALSE if it fails.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLConfigDriver</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>*pfErrorCode</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>ODBC_ERROR_GENERAL_ERR</para>
            </TD>
            <TD>
              <para>General installer error</para>
            </TD>
            <TD>
              <para>An error occurred for which there was no specific installer error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_BUFF_LEN</para>
            </TD>
            <TD>
              <para>Invalid buffer length</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszMsg</legacyItalic> argument was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_HWND</para>
            </TD>
            <TD>
              <para>Invalid window handle</para>
            </TD>
            <TD>
              <para>The <legacyItalic>hwndParent</legacyItalic> argument was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_REQUEST_TYPE</para>
            </TD>
            <TD>
              <para>Invalid type of request</para>
            </TD>
            <TD>
              <para>The <legacyItalic>fRequest</legacyItalic> argument was not one of the following:</para>
              <para>ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER</para>
              <para>The <legacyItalic>fRequest</legacyItalic> argument was a driver-specific option that was less than or equal to ODBC_CONFIG_DRIVER_MAX.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_NAME</para>
            </TD>
            <TD>
              <para>Invalid driver or translator name</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszDriver</legacyItalic> argument was invalid. It could not be found in the registry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_KEYWORD_VALUE</para>
            </TD>
            <TD>
              <para>Invalid keyword-value pairs</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszArgs</legacyItalic> argument contained a syntax error.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>Request</legacyItalic> failed</para>
            </TD>
            <TD>
              <para>The installer could not perform the operation requested by the <legacyItalic>fRequest</legacyItalic> argument. The call to <legacyBold>ConfigDriver</legacyBold> failed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_LOAD_LIBRARY_FAILED</para>
            </TD>
            <TD>
              <para>Could not load the driver or translator setup library</para>
            </TD>
            <TD>
              <para>The driver setup library could not be loaded.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_OUT_OF_MEM</para>
            </TD>
            <TD>
              <para>Out of memory</para>
            </TD>
            <TD>
              <para>The installer could not perform the function because of a lack of memory.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>
        <legacyBold>SQLConfigDriver</legacyBold> allows an application to call a driver's <legacyBold>ConfigDriver</legacyBold> routine without having to know the name and load the driver-specific setup DLL. A Setup program calls this function after the driver setup DLL has been installed. The calling program should be aware that this function might not be available for all drivers. In such a case, the calling program should continue without error.</para>
    </content>
  </section>
  <section>
    <title>Driver-Specific Options</title>
    <content>
      <para>An application can request driver-specific features exposed by the driver by using the <legacyItalic>fRequest</legacyItalic> argument. The <legacyItalic>fRequest</legacyItalic> for the first option will be ODBC_CONFIG_DRIVER_MAX+1, and additional options will be incremented by 1 from that value. Any arguments required by the driver for that function should be provided in a null-terminated string passed in the <legacyItalic>lpszArgs</legacyItalic> argument. Drivers providing such functionality should maintain a table of driver-specific options. The options should be fully documented in driver documentation. Application writers who use driver-specific options should be aware that this use will make the application less interoperable.</para>
    </content>
  </section>
  <section>
    <title>Setting Connection Pooling Timeout</title>
    <content>
      <para>Connection pooling timeout properties can be set when you set the configuration of the driver. <legacyBold>SQLConfigDriver</legacyBold> is called with an <legacyItalic>fRequest</legacyItalic> of ODBC_CONFIG_DRIVER and <legacyItalic>lpszArgs</legacyItalic> set to <legacyBold>CPTimeout</legacyBold>. <legacyBold>CPTimeout</legacyBold> determines the period of time that a connection can remain in the connection pool without being used. When the timeout expires, the connection is closed and removed from the pool. The default timeout is 60 seconds.</para>
      <para>When <legacyBold>SQLConfigDriver</legacyBold> is called with <legacyItalic>fRequest</legacyItalic> set to ODBC_INSTALL_DRIVER or ODBC_REMOVE_DRIVER, the Driver Manager loads the appropriate driver setup DLL and calls the <legacyBold>ConfigDriver</legacyBold> function. When <legacyBold>SQLConfigDriver</legacyBold> is called with an <legacyItalic>fRequest</legacyItalic> of ODBC_CONFIG_DRIVER, all processing is performed in the ODBC installer, so that the driver setup DLL does not have to be loaded.</para>
    </content>
  </section>
  <section>
    <title>Messages</title>
    <content>
      <para>A driver setup routine can send a text message to an application as null-terminated strings in the <legacyItalic>lpszMsg</legacyItalic> buffer. The message will be truncated to <legacyItalic>cbMsgMax</legacyItalic> minus the null-termination character by the <legacyBold>ConfigDriver</legacyBold> function if it is greater than or equal to <legacyItalic>cbMsgMax</legacyItalic> characters.</para>
    </content>
  </section>
  <section>
    <title>Related Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>For information about</para>
            </TD>
            <TD>
              <para>See</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Adding, modifying, or removing a driver</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9473f48f-bcae-4784-89c1-7839bad4ed13">ConfigDriver</legacyLink>(in the setup DLL)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Removing the default data source</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="db803266-57df-4864-a41b-901247549c1f">SQLRemoveDefaultDataSource</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>