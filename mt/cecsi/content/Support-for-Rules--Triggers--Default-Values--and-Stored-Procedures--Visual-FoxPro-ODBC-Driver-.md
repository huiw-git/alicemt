---
title: Support for Rules, Triggers, Default Values, and Stored Procedures (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e449de20-d6ca-4902-9f8e-814eb6e86650
translation.priority.ht: 
  - en-gb
---
# Support for Rules, Triggers, Default Values, and Stored Procedures (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You cannot create Visual FoxPro rules, triggers, default values, or stored procedures using the Visual FoxPro ODBC Driver. However, your application might interact with existing rules, triggers, default values, or stored procedures as it inserts, updates, or deletes Visual FoxPro data stored in a database.</para>
    <para>The following table lists the Visual FoxPro commands and functions supported by the Visual FoxPro ODBC Driver when the commands or functions exist in rules, triggers, default values, or stored procedures.</para>
    <para>If your application interacts with data whose rules, triggers, default values, or stored procedures call any other Visual FoxPro commands or functions, the driver generates an error. See <legacyLink xlink:href="afdb6b7e-738d-42ca-8053-67ae50873ca6">Unsupported Visual FoxPro Commands and Functions</legacyLink> for a list of commands and functions not supported by the driver.</para>
    <alert class="tip">
      <para>If you want to insert conditional code into your rules, triggers, or stored procedures that determines the commands to execute when called by the driver, you can use the <legacyBold>VERSION( )</legacyBold> function. The <legacyBold>VERSION( )</legacyBold> function returns "Visual FoxPro ODBC Driver <legacyItalic>&lt;version&gt;</legacyItalic>" when called by the driver.</para>
    </alert>
  </introduction>
  <section>
    <title>Visual FoxPro Commands and Functions Supported in Rules, Triggers, Default Values, and Stored Procedures</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>$ Operator</para>
            </TD>
            <TD>
              <para>% Operator</para>
            </TD>
            <TD>
              <para>&amp; Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>&amp;&amp; Command</para>
            </TD>
            <TD>
              <para>* Command</para>
            </TD>
            <TD>
              <para>= Command</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>A</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>ABS( ) Function</para>
            </TD>
            <TD>
              <para>ACOPY( ) Function</para>
            </TD>
            <TD>
              <para>ADD TABLE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ADATABASES( ) Function</para>
            </TD>
            <TD>
              <para>ADBOBJECTS( ) Function</para>
            </TD>
            <TD>
              <para>AERROR( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ADEL( ) Function</para>
            </TD>
            <TD>
              <para>AELEMENT( ) Function</para>
            </TD>
            <TD>
              <para>ALEN( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AFIELDS( ) Function</para>
            </TD>
            <TD>
              <para>AINS( ) Function</para>
            </TD>
            <TD>
              <para>ALTER TABLE - SQL Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ALIAS( ) Function</para>
            </TD>
            <TD>
              <para>ALLTRIM( ) Function</para>
            </TD>
            <TD>
              <para>APPEND FROM ARRAY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AND Operator</para>
            </TD>
            <TD>
              <para>APPEND Command</para>
            </TD>
            <TD>
              <para>APPEND MEMO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>APPEND FROM Command</para>
            </TD>
            <TD>
              <para>APPEND GENERAL Command</para>
            </TD>
            <TD>
              <para>ASCAN( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>APPEND PROCEDURES Command</para>
            </TD>
            <TD>
              <para>ASC( ) Function</para>
            </TD>
            <TD>
              <para>ASUBSCRIPT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ASIN( ) Function</para>
            </TD>
            <TD>
              <para>ASORT( ) Function</para>
            </TD>
            <TD>
              <para>ATAN( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AT( ) Function</para>
            </TD>
            <TD>
              <para>AT_C( ) Function</para>
            </TD>
            <TD>
              <para>ATCLINE( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ATC( ) Function</para>
            </TD>
            <TD>
              <para>ATCC( ) Function</para>
            </TD>
            <TD>
              <para>AUSED( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ATLINE( ) Function</para>
            </TD>
            <TD>
              <para>ATN2( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AVERAGE Command</para>
            </TD>
            <TD>
              <para>ACOS( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>B</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>BEGIN TRANSACTION Command</para>
            </TD>
            <TD>
              <para>BETWEEN( ) Function</para>
            </TD>
            <TD>
              <para>BITNOT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BITCLEAR( ) Function</para>
            </TD>
            <TD>
              <para>BITLSHIFT( ) Function</para>
            </TD>
            <TD>
              <para>BITSET( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BITOR( ) Function</para>
            </TD>
            <TD>
              <para>BITRSHIFT( ) Function</para>
            </TD>
            <TD>
              <para>BLANK Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BITTEST( ) Function</para>
            </TD>
            <TD>
              <para>BITXOR( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BOF( ) Function</para>
            </TD>
            <TD>
              <para>BITAND( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>C</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>CALCULATE Command</para>
            </TD>
            <TD>
              <para>CANDIDATE( ) Function</para>
            </TD>
            <TD>
              <para>CHR( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CDX( ) Function</para>
            </TD>
            <TD>
              <para>CEILING( ) Function</para>
            </TD>
            <TD>
              <para>CLOSE Commands</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CHRTRAN( ) Function</para>
            </TD>
            <TD>
              <para>CHRTRANC( ) Function</para>
            </TD>
            <TD>
              <para>COPY INDEXES Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CMONTH( ) Function</para>
            </TD>
            <TD>
              <para>CONTINUE Command</para>
            </TD>
            <TD>
              <para>COPY STRUCTURE EXTENDED Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COPY PROCEDURES Command</para>
            </TD>
            <TD>
              <para>COPY STRUCTURE Command</para>
            </TD>
            <TD>
              <para>COPY TO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COPY TAG Command</para>
            </TD>
            <TD>
              <para>COPY TO ARRAY Command</para>
            </TD>
            <TD>
              <para>CPCONVERT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COS( ) Function</para>
            </TD>
            <TD>
              <para>COUNT Command</para>
            </TD>
            <TD>
              <para>CTOD( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CPCURRENT( ) Function</para>
            </TD>
            <TD>
              <para>CPDBF( ) Function</para>
            </TD>
            <TD>
              <para>CURSORSETPROP( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CTOT( ) Function</para>
            </TD>
            <TD>
              <para>CURSORGETPROP( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CURVAL( ) Function</para>
            </TD>
            <TD>
              <para>CDOW( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>D</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>DATE( ) Function</para>
            </TD>
            <TD>
              <para>DATETIME( ) Function</para>
            </TD>
            <TD>
              <para>DAY( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DBC( ) Function</para>
            </TD>
            <TD>
              <para>DBF( ) Function</para>
            </TD>
            <TD>
              <para>DBGETPROP( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DBUSED( ) Function</para>
            </TD>
            <TD>
              <para>DELETE - SQL Command</para>
            </TD>
            <TD>
              <para>DELETE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DELETE TAG Command</para>
            </TD>
            <TD>
              <para>DELETED( ) Function</para>
            </TD>
            <TD>
              <para>DESCENDING( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DIFFERENCE( ) Function</para>
            </TD>
            <TD>
              <para>DIMENSION Command</para>
            </TD>
            <TD>
              <para>DISKSPACE( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DMY( ) Function</para>
            </TD>
            <TD>
              <para>DO CASE ... ENDCASE Command</para>
            </TD>
            <TD>
              <para>DO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DO WHILE ... ENDDO Command</para>
            </TD>
            <TD>
              <para>DOW( ) Function</para>
            </TD>
            <TD>
              <para>DTOC( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DTOR( ) Function</para>
            </TD>
            <TD>
              <para>DTOS( ) Function</para>
            </TD>
            <TD>
              <para>DTOT( ) Function</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>E</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>EMPTY( ) Function</para>
            </TD>
            <TD>
              <para>EVALUATE( ) Function</para>
            </TD>
            <TD>
              <para>EXIT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ERROR( ) Function</para>
            </TD>
            <TD>
              <para>EXP( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>END TRANSACTION Command</para>
            </TD>
            <TD>
              <para>EOF( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>F</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>FCOUNT( ) Function</para>
            </TD>
            <TD>
              <para>FDATE( ) Function</para>
            </TD>
            <TD>
              <para>FIELD( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FILE( ) Function</para>
            </TD>
            <TD>
              <para>FILTER( ) Function</para>
            </TD>
            <TD>
              <para>FLDLIST( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FLOCK( ) Function</para>
            </TD>
            <TD>
              <para>FLOOR( ) Function</para>
            </TD>
            <TD>
              <para>FLUSH Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FOR ... ENDFOR Command</para>
            </TD>
            <TD>
              <para>FOR( ) Function</para>
            </TD>
            <TD>
              <para>FOUND( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FREE TABLE Command</para>
            </TD>
            <TD>
              <para>FSIZE( ) Function</para>
            </TD>
            <TD>
              <para>FTIME( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FULLPATH( ) Function</para>
            </TD>
            <TD>
              <para>FUNCTION Command</para>
            </TD>
            <TD>
              <para>FV( ) Function</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>G</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>GATHER Command</para>
            </TD>
            <TD>
              <para>GETNEXTMODIFIED( ) Function</para>
            </TD>
            <TD>
              <para>GO/GOTO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>GETFLDSTATE( ) Function</para>
            </TD>
            <TD>
              <para>GOMONTH( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>GETCP( ) Function</para>
            </TD>
            <TD>
              <para>GETENV( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>H</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>HEADER( ) Function</para>
            </TD>
            <TD>
              <para>HOUR( ) Function</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>I</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>IDXCOLLATE( ) Function</para>
            </TD>
            <TD>
              <para>IF ... ENDIF Command</para>
            </TD>
            <TD>
              <para>IIF( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>INDBC( ) Function</para>
            </TD>
            <TD>
              <para>INDEX Command</para>
            </TD>
            <TD>
              <para>INLIST( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>INSERT-SQL Command</para>
            </TD>
            <TD>
              <para>INT( ) Function</para>
            </TD>
            <TD>
              <para>ISALPHA( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISBLANK( ) Function</para>
            </TD>
            <TD>
              <para>ISDIGIT( ) Function</para>
            </TD>
            <TD>
              <para>ISEXCLUSIVE( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISLEADBYTE( ) Function</para>
            </TD>
            <TD>
              <para>ISLOWER( ) Function</para>
            </TD>
            <TD>
              <para>ISNULL( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISREADONLY( ) Function</para>
            </TD>
            <TD>
              <para>ISUPPER( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>K</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>KEY( ) Function</para>
            </TD>
            <TD>
              <para>KEYMATCH( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>L</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>LEFT( ) Function</para>
            </TD>
            <TD>
              <para>LEFTC( ) Function</para>
            </TD>
            <TD>
              <para>LIKEC( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LENC( ) Function</para>
            </TD>
            <TD>
              <para>LIKE( ) Function</para>
            </TD>
            <TD>
              <para>LOCK( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOCAL Command</para>
            </TD>
            <TD>
              <para>LOCATE Command</para>
            </TD>
            <TD>
              <para>LOOKUP( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOG( ) Function</para>
            </TD>
            <TD>
              <para>LOG10( ) Function</para>
            </TD>
            <TD>
              <para>LTRIM( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOWER( ) Function</para>
            </TD>
            <TD>
              <para>LPARAMETERS Command</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LUPDATE( ) Function</para>
            </TD>
            <TD>
              <para>LEN( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>M</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>_MLINE System Memory Variable</para>
            </TD>
            <TD>
              <para>MAX( ) Function</para>
            </TD>
            <TD>
              <para>MDX( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MDY( ) Function</para>
            </TD>
            <TD>
              <para>MEMLINES( ) Function</para>
            </TD>
            <TD>
              <para>MESSAGE( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MIN( ) Function</para>
            </TD>
            <TD>
              <para>MINUTE( ) Function</para>
            </TD>
            <TD>
              <para>MLINE( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MOD( ) Function</para>
            </TD>
            <TD>
              <para>MONTH( ) Function</para>
            </TD>
            <TD>
              <para>MTON( ) Function</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>N</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>NDX( ) Function</para>
            </TD>
            <TD>
              <para>NORMALIZE( ) Function</para>
            </TD>
            <TD>
              <para>NOT Operator</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NOTE Command</para>
            </TD>
            <TD>
              <para>NTOM( ) Function</para>
            </TD>
            <TD>
              <para>NVL( ) Function</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>O</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>OCCURS( ) Function</para>
            </TD>
            <TD>
              <para>OLDVAL( ) Function</para>
            </TD>
            <TD>
              <para>ON ERROR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ON KEY Command</para>
            </TD>
            <TD>
              <para>ON( ) Function</para>
            </TD>
            <TD>
              <para>OPEN DATABASE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OR Operator</para>
            </TD>
            <TD>
              <para>ORDER( ) Function</para>
            </TD>
            <TD>
              <para>OS( ) Function</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>P</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>PACK Command</para>
            </TD>
            <TD>
              <para>PARAMETERS( ) Function</para>
            </TD>
            <TD>
              <para>PAYMENT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PARAMETERS Command</para>
            </TD>
            <TD>
              <para>PRIMARY( ) Function</para>
            </TD>
            <TD>
              <para>PRIVATE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PI( ) Function</para>
            </TD>
            <TD>
              <para>PROGRAM( ) Function</para>
            </TD>
            <TD>
              <para>PROPER( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PROCEDURE Command</para>
            </TD>
            <TD>
              <para>PV( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PUBLIC Command</para>
            </TD>
            <TD>
              <para>PADL( ) | PADR( ) | PADC( ) Functions</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>R</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>RAND( ) Function</para>
            </TD>
            <TD>
              <para>RAT( ) Function</para>
            </TD>
            <TD>
              <para>RATC( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RATLINE( ) Function</para>
            </TD>
            <TD>
              <para>RECALL Command</para>
            </TD>
            <TD>
              <para>RECCOUNT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RECNO( ) Function</para>
            </TD>
            <TD>
              <para>RECSIZE( ) Function</para>
            </TD>
            <TD>
              <para>REGIONAL Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RELATION( ) Function</para>
            </TD>
            <TD>
              <para>REMOVE TABLE Command</para>
            </TD>
            <TD>
              <para>REPLACE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>REPLACE FROM ARRAY Command</para>
            </TD>
            <TD>
              <para>REPLICATE( ) Function</para>
            </TD>
            <TD>
              <para>RETRY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RETURN Command</para>
            </TD>
            <TD>
              <para>RIGHT( ) Function</para>
            </TD>
            <TD>
              <para>RIGHTC( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RLOCK( ) Function</para>
            </TD>
            <TD>
              <para>ROLLBACK Command</para>
            </TD>
            <TD>
              <para>ROUND( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RTOD( ) Function</para>
            </TD>
            <TD>
              <para>RTRIM( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>S</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>SCAN ... ENDSCAN Command</para>
            </TD>
            <TD>
              <para>SCATTER Command</para>
            </TD>
            <TD>
              <para>SEC( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SECONDS( ) Function</para>
            </TD>
            <TD>
              <para>SEEK Command</para>
            </TD>
            <TD>
              <para>SEEK( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SELECT Command</para>
            </TD>
            <TD>
              <para>SELECT( ) Function</para>
            </TD>
            <TD>
              <para>SELECT-SQL Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET BLOCKSIZE Command</para>
            </TD>
            <TD>
              <para>SET CARRY Command</para>
            </TD>
            <TD>
              <para>SET CENTURY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET COLLATE Command</para>
            </TD>
            <TD>
              <para>SET DATABASE Command</para>
            </TD>
            <TD>
              <para>SET DATE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET DEFAULT Command</para>
            </TD>
            <TD>
              <para>SET DELETED Command</para>
            </TD>
            <TD>
              <para>SET EXACT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET EXCLUSIVE Command</para>
            </TD>
            <TD>
              <para>SET FDOW Command</para>
            </TD>
            <TD>
              <para>SET FIELDS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET FILTER Command</para>
            </TD>
            <TD>
              <para>SET FIXED Command</para>
            </TD>
            <TD>
              <para>SET FULLPATH Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET FWEEK Command</para>
            </TD>
            <TD>
              <para>SET HOURS Command</para>
            </TD>
            <TD>
              <para>SET INDEX Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET LOCK Command</para>
            </TD>
            <TD>
              <para>SET MULTILOCKS Command</para>
            </TD>
            <TD>
              <para>SET NEAR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET NOCPTRANS Command</para>
            </TD>
            <TD>
              <para>SET NOTIFY Command</para>
            </TD>
            <TD>
              <para>SET NULL Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET OPTIMIZE Command</para>
            </TD>
            <TD>
              <para>SET ORDER Command</para>
            </TD>
            <TD>
              <para>SET PATH Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET PROCEDURE Command</para>
            </TD>
            <TD>
              <para>SET RELATION Command</para>
            </TD>
            <TD>
              <para>SET RELATION OFF Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET REPROCESS Command</para>
            </TD>
            <TD>
              <para>SET SKIP Command</para>
            </TD>
            <TD>
              <para>SET UDFPARMS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET UNIQUE Command</para>
            </TD>
            <TD>
              <para>SET VOLUME Command</para>
            </TD>
            <TD>
              <para>SET( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SETFLDSTATE( ) Function</para>
            </TD>
            <TD>
              <para>SIGN ( ) Function</para>
            </TD>
            <TD>
              <para>SIN( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SKIP Command</para>
            </TD>
            <TD>
              <para>SORT Command</para>
            </TD>
            <TD>
              <para>SPACE( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQRT( ) Function</para>
            </TD>
            <TD>
              <para>STORE Command</para>
            </TD>
            <TD>
              <para>STR( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>STRCONV( ) Function</para>
            </TD>
            <TD>
              <para>STRTRAN( ) Function</para>
            </TD>
            <TD>
              <para>STUFF( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>STUFFC( ) Function</para>
            </TD>
            <TD>
              <para>SUBSTR( ) Function</para>
            </TD>
            <TD>
              <para>SUBSTRC( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SUM Command</para>
            </TD>
            <TD>
              <para>SYS(2011) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>T</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>_TALLY System Memory Variable</para>
            </TD>
            <TD>
              <para>_TRIGGERLEVEL System Memory Variable</para>
            </TD>
            <TD>
              <para>TAGCOUNT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TABLEUPDATE( ) Function</para>
            </TD>
            <TD>
              <para>TAG( ) Function</para>
            </TD>
            <TD>
              <para>TARGET( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TAGNO( ) Function</para>
            </TD>
            <TD>
              <para>TAN( ) Function</para>
            </TD>
            <TD>
              <para>TRIM( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TIME( ) Function</para>
            </TD>
            <TD>
              <para>TOTAL Command</para>
            </TD>
            <TD>
              <para>TXNLEVEL( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TTOC( ) Function</para>
            </TD>
            <TD>
              <para>TTOD( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TYPE( ) Function</para>
            </TD>
            <TD>
              <para>TABLEREVERT( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>U</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>UNIQUE( ) Function</para>
            </TD>
            <TD>
              <para>UNLOCK Command</para>
            </TD>
            <TD>
              <para>USE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>UPDATE Command</para>
            </TD>
            <TD>
              <para>UPPER( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>USED( ) Function</para>
            </TD>
            <TD>
              <para>UPDATE - SQL Command</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>V</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>VAL( ) Function</para>
            </TD>
            <TD>
              <para>VERSION( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>W</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>WEEK( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Y</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>YEAR( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Z</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>ZAP Command</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>