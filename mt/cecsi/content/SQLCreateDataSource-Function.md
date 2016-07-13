---
title: SQLCreateDataSource Function
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLCreateDataSource
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 76ee851a-dca9-40cc-8e9e-eb3f74e560ee
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLCreateDataSource Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 2.0</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLCreateDataSource</legacyBold> displays a dialog box with which the user can add a data source.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
BOOL <legacyBold>SQLCreateDataSource</legacyBold>(
     HWND    <parameterReference>hwnd</parameterReference>,
     LPSTR   <parameterReference>lpszDS</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>hwnd</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Parent window handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>lpszDS</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Data source name. <legacyItalic>lpszDS</legacyItalic> can be a null pointer or an empty string.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>
        <legacyBold>SQLCreateDataSource</legacyBold> returns TRUE if the data source is created. Otherwise, it returns FALSE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLCreateDataSource</legacyBold> returns FALSE, an associated <legacyItalic>*pfErrorCode</legacyItalic> value can be obtained by calling <legacyBold>SQLInstallerError</legacyBold>. The following table lists the <legacyItalic>*pfErrorCode</legacyItalic> values that can be returned by <legacyBold>SQLInstallerError </legacyBold>and explains each one in the context of this function.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>*pfErrorCode</legacyItalic> </para>
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
              <para>ODBC_ERROR_INVALID_HWND</para>
            </TD>
            <TD>
              <para>Invalid window handle</para>
            </TD>
            <TD>
              <para>The <legacyItalic>hwnd</legacyItalic> argument was invalid or NULL.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_INVALID_DSN</para>
            </TD>
            <TD>
              <para>Invalid DSN</para>
            </TD>
            <TD>
              <para>The <legacyItalic>lpszDS</legacyItalic> argument contained a string that was invalid for a DSN.</para>
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
              <para>The call to <legacyBold>ConfigDSN</legacyBold> with the ODBC_ADD_DSN option failed.</para>
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
              <para>ODBC_ERROR_USER_CANCELED</para>
            </TD>
            <TD>
              <para>User canceled operation</para>
            </TD>
            <TD>
              <para>User canceled creation of a new data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC_ERROR_CREATE_DSN_FAILED</para>
            </TD>
            <TD>
              <para>Could not create the requested DSN</para>
            </TD>
            <TD>
              <para>Could not connect to the database; the call to <legacyBold>SQLDriverConnect</legacyBold> for a File DSN did not return a successful connection.</para>
              <para>Could not write to the file.</para>
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
      <para>If <legacyItalic>hwnd</legacyItalic> is null, <legacyBold>SQLCreateDataSource</legacyBold> returns FALSE. Otherwise, it displays the <legacyBold>Create New Data Source</legacyBold> dialog box with a wizard page for choosing the type of data source to be set up, as shown in the following illustration.</para>
      <mediaLink>
        <image xlink:href="66263c31-a98d-4822-8077-bebf519bac17" />
      </mediaLink>
      <para>The default option is <legacyBold>File Data Source</legacyBold>. When a data source has been chosen and <legacyBold>Next</legacyBold> clicked, the following wizard page that contains a list of installed drivers is displayed.</para>
      <mediaLink>
        <image xlink:href="90358ed2-bc9d-47af-83bd-e6af5cbe5467" />
      </mediaLink>
      <para>If <legacyBold>Cancel</legacyBold> is clicked, the dialog box disappears and <legacyBold>SQLCreateDataSource</legacyBold> returns FALSE with the error code of ODBC_ERROR_USER_CANCELED. If either the <legacyBold>User Data Source</legacyBold> or <legacyBold>System Data Source</legacyBold> option was selected, the <legacyBold>Advanced</legacyBold> button is unavailable.</para>
      <para>When the <legacyBold>Next</legacyBold> button is clicked, one of the following will occur, depending on which type of data source was selected:  </para>
      <list class="bullet">
        <listItem>
          <para>If <legacyBold>File Data Source</legacyBold> was selected, a wizard page is displayed for the user to enter a file name.</para>
        </listItem>
        <listItem>
          <para>If either <legacyBold>User Data Source</legacyBold> or <legacyBold>System Data Source</legacyBold> was selected, a wizard page displaying the type of data source and driver is displayed for review, and when <legacyBold>Finish</legacyBold> is clicked, the data source is set up.</para>
        </listItem>
      </list>
      <para>If <legacyBold>Advanced</legacyBold> is clicked from the Create New Data Source wizard page, a wizard page is displayed for the user to enter driver-specific information. In the text box of this dialog box, type the driver and keywords separated by returns, as shown in the following illustration.</para>
      <mediaLink>
        <image xlink:href="09b9f68a-b40d-44ac-b192-904cb7ea8b48" />
      </mediaLink>
      <para>Additional driver-specific keywords can be found under the description of <legacyBold>SQLDriverConnect</legacyBold>. All except <legacyBold>DSN</legacyBold> are allowed.</para>
      <para>The default for the <legacyBold>Verify This Connection</legacyBold> option is TRUE. This default applies whether or not this wizard page is activated. If <legacyBold>OK</legacyBold> is clicked, the string specified in the text box and the <legacyBold>Verify This Connection</legacyBold> option value are cached. (If the <legacyBold>Close</legacyBold> button or <legacyBold>Cancel</legacyBold> is clicked, any newly entered driver-specific information is lost because the string specified in the text box and the <legacyBold>Verify This Connection</legacyBold> option value are not cached.)</para>
      <para>If <legacyBold>File Data Source</legacyBold> was selected in the first wizard page, then after a driver has been selected and the keyword values have been entered in the Advanced wizard page, the user is prompted to enter a file name. Click <legacyBold>Browse</legacyBold> to search for a file name, in which case the default directory in the <legacyBold>Browse</legacyBold> box is specified by a combination of the path specified by CommonFileDir in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion and "ODBC\DataSources". (If CommonFileDir was "C:\Program Files\Common Files", the default directory would be "C:\Program Files\Common Files\ODBC\Data Sources".)</para>
      <para>When a file name has been entered and <legacyBold>Next</legacyBold> is clicked, the file name entered is checked for validity against the standard file-naming rules of the operating system. If the file name is invalid, an error message box notifies the user that an invalid file name was entered. After the user acknowledges the message box, the focus is returned to the wizard page in which the file name is entered. If the file name is valid, a wizard page that shows the selected keyword-value pairs is displayed for review, as shown in the following illustration.</para>
      <mediaLink>
        <image xlink:href="dcdff380-e688-4c65-8228-64b3d033cb0c" />
      </mediaLink>
      <para>If <legacyBold>Finish</legacyBold> is clicked and <legacyBold>File Data Source</legacyBold> was selected as the data source type, and if the <legacyBold>Verify this connection</legacyBold> option is TRUE, <legacyBold>SQLDriverConnect</legacyBold> is called with the <legacyBold>SAVEFILE</legacyBold> and <legacyBold>DRIVER</legacyBold> keywords. The <legacyItalic>DriverCompletion</legacyItalic> argument is set to SQL_DRIVER_COMPLETE. The file name for the <legacyBold>SAVEFILE</legacyBold> keyword is the name that was entered or chosen, and the driver name for the <legacyBold>DRIVER</legacyBold> keyword is the name that was chosen. If a driver-specific connection string was specified in the Advanced wizard page, that string is appended after the <legacyBold>DRIVER</legacyBold> keyword.</para>
      <para>If <legacyBold>SQLDriverConnect</legacyBold> returns SQL_SUCCESS, the Driver Manager has created the File DSN. <legacyBold>SQLCreateDataSource</legacyBold> returns TRUE. If <legacyBold>SQLDriverConnect</legacyBold> does not return SQL_SUCCESS, a warning message box indicates that a connection could not be made to the data source. A DSN with minimal connection information can still be created. This message box lets the user either cancel or continue with the File DSN creation.</para>
      <para>If the user chooses to continue creating the DSN, this process continues as if the <legacyBold>Verify this connection</legacyBold> option were set to FALSE. If the user chooses to cancel, FALSE is returned for <legacyBold>SQLCreateDataSource</legacyBold> with an error code of ODBC_ERROR_CREATE_DSN_FAILED.</para>
      <para>If <legacyBold>File Data Source</legacyBold> was selected as the data source type and the <legacyBold>Verify this connection</legacyBold> option is FALSE, a File DSN is created with the <legacyBold>DRIVER</legacyBold> keyword and user-specified connect string (if any) from the Advanced wizard page. If the file creation was successful, TRUE is returned for <legacyBold>SQLCreateDataSource</legacyBold>. If the file creation was not successful, an error message box notifies the user with whatever error was returned from the operating system. FALSE is returned for <legacyBold>SQLCreateDataSource</legacyBold> with an error code of ODBC_ERROR_CREATE_DSN_FAILED. For more information about file data sources, see <legacyLink xlink:href="3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae">Connecting Using File Data Sources</legacyLink>, or see <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>.</para>
      <para>If <legacyBold>User</legacyBold> or <legacyBold>System Data Source</legacyBold> was selected as the data source type, <legacyBold>ConfigDSN</legacyBold> in the driver setup library is called with the ODBC_ADD_DSN <legacyItalic>fRequest</legacyItalic>. For more information, see <legacyLink xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN</legacyLink>.</para>
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
              <para>Managing data sources</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac6d186f-b394-406c-94c4-c6331d1ca468">SQLManageDataSources</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>