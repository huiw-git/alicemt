---
title: ConfigDriver Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - ConfigDriver
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 9473f48f-bcae-4784-89c1-7839bad4ed13
translation.priority.ht: 
  - en-gb
---
# ConfigDriver Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 2.5 </para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>ConfigDriver</legacyBold> allows a setup program to perform install and uninstall functions without requiring the program to call <legacyBold>ConfigDSN</legacyBold>. This function will perform driver-specific functions such as creating driver-specific system information and performing DSN conversions during installation, as well as cleaning up system information modifications during uninstall. This function is exposed by the driver setup DLL or a separate setup DLL.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>ConfigDriver</legacyBold>(
      HWND    <parameterReference>hwndParent</parameterReference>,
      WORD    <parameterReference>fRequest</parameterReference>,
      LPCSTR  <parameterReference>lpszDriver</parameterReference>,
      LPCSTR  <parameterReference>lpszArgs</parameterReference>,
      LPSTR   <parameterReference>lpszMsg</parameterReference>,
      WORD    <parameterReference>cbMsgMax</parameterReference>,
      WORD *  <parameterReference>pcbMsgOut</parameterReference>);</legacySyntax>
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
          <para>[Input] Type of request. The <legacyItalic>fRequest</legacyItalic> argument must contain one of the following values:</para>
          <para>ODBC_INSTALL_DRIVER: Install a new driver. </para>
          <para>ODBC_REMOVE_DRIVER: Remove a driver.</para>
          <para>This option can also be driver-specific, in which case the <legacyItalic>fRequest</legacyItalic> argument for the first option must start from ODBC_CONFIG_DRIVER_MAX+1. The <legacyItalic>fRequest</legacyItalic> argument for any additional option must also start from a value greater than ODBC_CONFIG_DRIVER_MAX+1. </para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszDriver</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] The name of the driver as registered in the Odbcinst.ini key of the system information.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszArgs</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] A null-terminated string containing arguments for a driver-specific <legacyItalic>fRequest</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszMsg</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] A null-terminated string containing an output message from the driver setup.</para>
        </definition>
        <definedTerm>
          <legacyItalic>cbMsgMax</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of <legacyItalic>lpszMsg</legacyItalic>.</para>
        </definition>
        <definedTerm>
          <legacyItalic>pcbMsgOut</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Output] Total number of bytes available to return in <legacyItalic>lpszMsg</legacyItalic>.</para>
          <para>If the number of bytes available to return is greater than or equal to <legacyItalic>cbMsgMax</legacyItalic>, the output message in <legacyItalic>lpszMsg</legacyItalic> is truncated to <legacyItalic>cbMsgMax</legacyItalic> minus the null-termination character. The <legacyItalic>pcbMsgOut</legacyItalic> argument can be a null pointer. </para>
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
      <para>When <legacyBold>ConfigDriver</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value is posted to the installer error buffer by a call to <legacyBold>SQLPostInstallerError</legacyBold> and can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
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
              <para>The driver-specific option was less than or equal to ODBC_CONFIG_DRIVER_MAX.</para>
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
              <para>ODBC_ERROR_REQUEST_FAILED</para>
            </TD>
            <TD>
              <para>               <legacyItalic>Request</legacyItalic> failed</para>
            </TD>
            <TD>
              <para>Could not perform the operation requested by the <legacyItalic>fRequest</legacyItalic> argument.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_DRIVER_SPECIFIC</para>
            </TD>
            <TD>
              <para>Driver- or translator-specific error</para>
            </TD>
            <TD>
              <para>A driver-specific error for which there is no defined ODBC installer error. The <legacyItalic>SzError</legacyItalic> argument in a call to the <legacyBold>SQLPostInstallerError</legacyBold> function should contain the driver-specific error message.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content />
    <sections>
      <section>
        <title>Driver-Specific Options</title>
        <content>
          <para>An application can request driver-specific features exposed by the driver by using the <legacyItalic>fRequest</legacyItalic> argument. The <legacyItalic>fRequest</legacyItalic> for the first option will be ODBC_CONFIG_DRIVER_MAX plus 1, and additional options will be incremented by 1 from that value. Any arguments required by the driver for that function should be provided in a null-terminated string passed in the <legacyItalic>lpszArgs</legacyItalic> argument. Drivers providing such functionality should maintain a table of driver-specific options. The options should be fully documented in driver documentation. Application writers who use driver-specific options should be aware that this will make the application less interoperable.</para>
        </content>
      </section>
      <section>
        <title>Messages</title>
        <content>
          <para>A driver setup routine can send a text message to an application as a null-terminated string in the <legacyItalic>lpszMsg</legacyItalic> buffer. The message will be truncated to <legacyItalic>cbMsgMax</legacyItalic> minus the null-termination character by the <legacyBold>ConfigDriver</legacyBold> function if it is greater than or equal to <legacyItalic>cbMsgMax</legacyItalic> characters.</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>