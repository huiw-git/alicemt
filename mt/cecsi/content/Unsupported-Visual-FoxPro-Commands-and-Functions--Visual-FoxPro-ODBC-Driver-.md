---
title: Unsupported Visual FoxPro Commands and Functions (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: afdb6b7e-738d-42ca-8053-67ae50873ca6
translation.priority.ht: 
  - en-gb
---
# Unsupported Visual FoxPro Commands and Functions (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists FoxPro commands and functions that are not supported by the Visual FoxPro ODBC Driver but are supported by Microsoft® Visual FoxPro®.</para>
    <para>If your application interacts with data whose rules, triggers, default values, or stored procedures call these Visual FoxPro commands or functions, the driver can generate an error.</para>
  </introduction>
  <section>
    <title>Unsupported Visual FoxPro Commands and Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>#DEFINE ... #UNDEF</para>
            </TD>
            <TD>
              <para>#IF ... #ENDIF Preprocessor Directive</para>
            </TD>
            <TD>
              <para>#IFDEF | #IFNDEF</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>#INCLUDE Preprocessor Directive</para>
            </TD>
            <TD>
              <para>:: Scope Resolution Operator</para>
            </TD>
            <TD>
              <para>! Command (see RUN | ! Command)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>? | ?? Command</para>
            </TD>
            <TD>
              <para>??? Command</para>
            </TD>
            <TD>
              <para>\ | \\ Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>@ ... BOX Command</para>
            </TD>
            <TD>
              <para>@ ... CLASS Command</para>
            </TD>
            <TD>
              <para>@ ... CLEAR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>@ ... EDIT - Edit Boxes Command</para>
            </TD>
            <TD>
              <para>@ ... FILL Command</para>
            </TD>
            <TD>
              <para>@ ... GET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>@ ... MENU Command</para>
            </TD>
            <TD>
              <para>@ ... PROMPT Command</para>
            </TD>
            <TD>
              <para>@ ... SAY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>@ ... SCROLL Command</para>
            </TD>
            <TD>
              <para>@ ... TO Command</para>
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
    <title>A</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>ACCEPT Command</para>
            </TD>
            <TD>
              <para>ACLASS( ) Function</para>
            </TD>
            <TD>
              <para>ACTIVATE MENU Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ACTIVATE POPUP Command</para>
            </TD>
            <TD>
              <para>ACTIVATE SCREEN Command</para>
            </TD>
            <TD>
              <para>ACTIVATE WINDOW Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ActivateCell Method</para>
            </TD>
            <TD>
              <para>ADD CLASS Command</para>
            </TD>
            <TD>
              <para>ADIR( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AFONT( ) Function</para>
            </TD>
            <TD>
              <para>AINSTANCE( ) Function</para>
            </TD>
            <TD>
              <para>_ALIGNMENT System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AMEMBERS( ) Function</para>
            </TD>
            <TD>
              <para>ANSITOOEM( ) Function</para>
            </TD>
            <TD>
              <para>APRINTERS( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ASELOBJ( ) Function</para>
            </TD>
            <TD>
              <para>ASSIST Command</para>
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
              <para>BAR( ) Function</para>
            </TD>
            <TD>
              <para>BARCOUNT( ) Function</para>
            </TD>
            <TD>
              <para>BARPROMPT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_BEAUTIFY System Memory Variable</para>
            </TD>
            <TD>
              <para>_BOX System Memory Variable</para>
            </TD>
            <TD>
              <para>BROWSE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_BROWSER System Memory Variable</para>
            </TD>
            <TD>
              <para>BUILD APP Command</para>
            </TD>
            <TD>
              <para>BUILD EXE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BUILD PROJECT Command</para>
            </TD>
            <TD>
              <para>_BUILDER System Memory Variable</para>
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
              <para>_CALCVALUE System Memory Variable</para>
            </TD>
            <TD>
              <para>_CLIPTEXT System Memory Variable</para>
            </TD>
            <TD>
              <para>_CONVERTER System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_CUROBJ System Memory Variable</para>
            </TD>
            <TD>
              <para>CALL Command</para>
            </TD>
            <TD>
              <para>CANCEL Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CAPSLOCK( ) Function</para>
            </TD>
            <TD>
              <para>CD Command</para>
            </TD>
            <TD>
              <para>CHANGE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CHDIR Command</para>
            </TD>
            <TD>
              <para>CHRSAW( ) Function</para>
            </TD>
            <TD>
              <para>CLOSE MEMO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CNTBAR( ) Function</para>
            </TD>
            <TD>
              <para>CNTPAD( ) Function</para>
            </TD>
            <TD>
              <para>COL( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COMPILE Command</para>
            </TD>
            <TD>
              <para>COMPILE DATABASE Command</para>
            </TD>
            <TD>
              <para>COMPILE FORM Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COMPOBJ( ) Function</para>
            </TD>
            <TD>
              <para>Container Object</para>
            </TD>
            <TD>
              <para>Control Object</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>COPY FILE Command</para>
            </TD>
            <TD>
              <para>COPY MEMO Command</para>
            </TD>
            <TD>
              <para>CREATE CLASS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CREATE CLASSLIB Command</para>
            </TD>
            <TD>
              <para>CREATE COLOR SET Command</para>
            </TD>
            <TD>
              <para>CREATE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CREATE CONNECTION Command</para>
            </TD>
            <TD>
              <para>CREATE DATABASE Command</para>
            </TD>
            <TD>
              <para>CREATE FORM Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CREATE FROM Command</para>
            </TD>
            <TD>
              <para>CREATE LABEL Command</para>
            </TD>
            <TD>
              <para>CREATE MENU Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CREATE PROJECT Command</para>
            </TD>
            <TD>
              <para>CREATE QUERY Command</para>
            </TD>
            <TD>
              <para>CREATE REPORT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CREATE SCREEN Command</para>
            </TD>
            <TD>
              <para>CREATE SQL VIEW Command</para>
            </TD>
            <TD>
              <para>CREATE TRIGGER Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CREATE VIEW Command</para>
            </TD>
            <TD>
              <para>CREATEOBJECT( ) Function</para>
            </TD>
            <TD>
              <para>CURDIR( ) Function</para>
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
              <para>_DBLCLICK System Memory Variable</para>
            </TD>
            <TD>
              <para>_DIARYDATE System Memory Variable</para>
            </TD>
            <TD>
              <para>DBSETPROP( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DDE Functions</para>
            </TD>
            <TD>
              <para>DEACTIVATE MENU Command</para>
            </TD>
            <TD>
              <para>DEACTIVATE POPUP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DEACTIVATE WINDOW Command</para>
            </TD>
            <TD>
              <para>DECLARE - DLL Command</para>
            </TD>
            <TD>
              <para>DECLARE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DEFINE BAR Command</para>
            </TD>
            <TD>
              <para>DEFINE BOX Command</para>
            </TD>
            <TD>
              <para>DEFINE CLASS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DEFINE MENU Command</para>
            </TD>
            <TD>
              <para>DEFINE PAD Command</para>
            </TD>
            <TD>
              <para>DEFINE POPUP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DEFINE WINDOW Command</para>
            </TD>
            <TD>
              <para>DELETE CONNECTION Command</para>
            </TD>
            <TD>
              <para>DELETE DATABASE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DELETE FILE Command</para>
            </TD>
            <TD>
              <para>DELETE TRIGGER Command</para>
            </TD>
            <TD>
              <para>DELETE VIEW Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DIR Command</para>
            </TD>
            <TD>
              <para>DIRECTORY Command</para>
            </TD>
            <TD>
              <para>DISPLAY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DISPLAY CONNECTIONS Command</para>
            </TD>
            <TD>
              <para>DISPLAY DATABASE Command</para>
            </TD>
            <TD>
              <para>DISPLAY DLLS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DISPLAY FILES Command</para>
            </TD>
            <TD>
              <para>DISPLAY MEMORY Command</para>
            </TD>
            <TD>
              <para>DISPLAY OBJECTS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DISPLAY PROCEDURES Command</para>
            </TD>
            <TD>
              <para>DISPLAY STATUS Command</para>
            </TD>
            <TD>
              <para>DISPLAY STRUCTURE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DISPLAY TABLES Command</para>
            </TD>
            <TD>
              <para>DISPLAY VIEWS Command</para>
            </TD>
            <TD>
              <para>DO FORM Command</para>
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
              <para>EDIT Command</para>
            </TD>
            <TD>
              <para>ERROR Command</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ERASE Command</para>
            </TD>
            <TD>
              <para>EXTERNAL Command</para>
            </TD>
            <TD>
              <para>EXPORT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>EJECT Command</para>
            </TD>
            <TD>
              <para>EJECT PAGE Command</para>
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
              <para>_FOXDOC System Memory Variable</para>
            </TD>
            <TD>
              <para>_FOXGRAPH System Memory Variable</para>
            </TD>
            <TD>
              <para>FEOF( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FCLOSE( ) Function</para>
            </TD>
            <TD>
              <para>FCREATE( ) Function</para>
            </TD>
            <TD>
              <para>FGETS( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FERROR( ) Function</para>
            </TD>
            <TD>
              <para>FFLUSH( ) Function</para>
            </TD>
            <TD>
              <para>FKLABEL( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FILER Command</para>
            </TD>
            <TD>
              <para>FIND Command</para>
            </TD>
            <TD>
              <para>FOPEN( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FKMAX( ) Function</para>
            </TD>
            <TD>
              <para>FONTMETRIC( ) Function</para>
            </TD>
            <TD>
              <para>FSEEK( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FPUTS( ) Function</para>
            </TD>
            <TD>
              <para>FREAD( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>FWRITE( ) Function</para>
            </TD>
            <TD>
              <para>FCHSIZE( ) Function</para>
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
    <title>G</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>_GENGRAPH System Memory Variable</para>
            </TD>
            <TD>
              <para>_GENMENU System Memory Variable</para>
            </TD>
            <TD>
              <para>_GENPD System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_GENSCRN System Memory Variable</para>
            </TD>
            <TD>
              <para>_GENXTAB System Memory Variable</para>
            </TD>
            <TD>
              <para>GETBAR( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>GETCOLOR( ) Function</para>
            </TD>
            <TD>
              <para>GETDIR( ) Function</para>
            </TD>
            <TD>
              <para>GETEXPR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>GETFILE( ) Function</para>
            </TD>
            <TD>
              <para>GETFONT( ) Function</para>
            </TD>
            <TD>
              <para>GETOBJECT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>GETPAD( ) Function</para>
            </TD>
            <TD>
              <para>GETPICT( ) Function</para>
            </TD>
            <TD>
              <para>GETPRINTER( ) Function</para>
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
              <para>HELP Command</para>
            </TD>
            <TD>
              <para>HIDE MENU Command</para>
            </TD>
            <TD>
              <para>HIDE POPUP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HIDE WINDOW Command</para>
            </TD>
            <TD>
              <para>HOME( ) Function</para>
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
    <title>I</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>IMESTATUS( ) Function</para>
            </TD>
            <TD>
              <para>IMPORT Command</para>
            </TD>
            <TD>
              <para>INPUT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>INDEX ON Command</para>
            </TD>
            <TD>
              <para>INKEY( ) Function</para>
            </TD>
            <TD>
              <para>ISCOLOR( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>INSERT Command</para>
            </TD>
            <TD>
              <para>INSMODE( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISMOUSE( ) Function</para>
            </TD>
            <TD>
              <para>_INDENT System Memory Variable</para>
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
    <title>J</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>JOIN Command</para>
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
    <title>K</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>KEYBOARD Command</para>
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
    <title>L</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>_LMARGIN System Memory Variable</para>
            </TD>
            <TD>
              <para>LABEL Command</para>
            </TD>
            <TD>
              <para>LASTKEY( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LINENO( ) Function</para>
            </TD>
            <TD>
              <para>LIST Commands</para>
            </TD>
            <TD>
              <para>LIST CONNECTIONS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LOAD Command</para>
            </TD>
            <TD>
              <para>LOCFILE( ) Function</para>
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
              <para>MCOL( ) Function</para>
            </TD>
            <TD>
              <para>MD Command</para>
            </TD>
            <TD>
              <para>MENU TO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MEMORY( ) Function</para>
            </TD>
            <TD>
              <para>MENU Command</para>
            </TD>
            <TD>
              <para>MKDIR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MENU( ) Function</para>
            </TD>
            <TD>
              <para>MESSAGEBOX( ) Function</para>
            </TD>
            <TD>
              <para>MODIFY CONNECTION Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MODIFY CLASS Command</para>
            </TD>
            <TD>
              <para>MODIFY COMMAND Command</para>
            </TD>
            <TD>
              <para>MODIFY FORM Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MODIFY DATABASE Command</para>
            </TD>
            <TD>
              <para>MODIFY FILE Command</para>
            </TD>
            <TD>
              <para>MODIFY MEMO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MODIFY GENERAL Command</para>
            </TD>
            <TD>
              <para>MODIFY LABEL Command</para>
            </TD>
            <TD>
              <para>MODIFY PROJECT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MODIFY MENU Command</para>
            </TD>
            <TD>
              <para>MODIFY PROCEDURE Command</para>
            </TD>
            <TD>
              <para>MODIFY SCREEN Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MODIFY QUERY Command</para>
            </TD>
            <TD>
              <para>MODIFY REPORT Command</para>
            </TD>
            <TD>
              <para>MODIFY WINDOW Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MODIFY STRUCTURE Command</para>
            </TD>
            <TD>
              <para>MODIFY VIEW Command</para>
            </TD>
            <TD>
              <para>MOVE WINDOW Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MOUSE Command</para>
            </TD>
            <TD>
              <para>MOVE POPUP Command</para>
            </TD>
            <TD>
              <para>MROW( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MRKBAR( ) Function</para>
            </TD>
            <TD>
              <para>MRKPAD( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MWINDOW( ) Function</para>
            </TD>
            <TD>
              <para>MDOWN( ) Function</para>
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
    <title>N</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>NUMLOCK( ) Function</para>
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
    <title>O</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>OBJNUM( ) Function</para>
            </TD>
            <TD>
              <para>OBJTOCLIENT( ) Function</para>
            </TD>
            <TD>
              <para>ON BAR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OEMTOANSI( ) Function</para>
            </TD>
            <TD>
              <para>ON APLABOUT Command</para>
            </TD>
            <TD>
              <para>ON EXIT MENU Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ON ESCAPE Command</para>
            </TD>
            <TD>
              <para>ON EXIT BAR Command</para>
            </TD>
            <TD>
              <para>ON KEY = Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ON EXIT PAD Command</para>
            </TD>
            <TD>
              <para>ON EXIT POPUP Command</para>
            </TD>
            <TD>
              <para>ON PAD Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ON KEY LABEL Command</para>
            </TD>
            <TD>
              <para>ON MACHELP Command</para>
            </TD>
            <TD>
              <para>ON SELECTION BAR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ON PAGE Command</para>
            </TD>
            <TD>
              <para>ON READERROR Command</para>
            </TD>
            <TD>
              <para>ON SELECTION POPUP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ON SELECTION MENU Command</para>
            </TD>
            <TD>
              <para>ON SELECTION PAD Command</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ON SHUTDOWN Command</para>
            </TD>
            <TD>
              <para>OBJVAR( ) Function</para>
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
    <title>P</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>_PADVANCE System Memory Variable</para>
            </TD>
            <TD>
              <para>_PAGENO System Memory Variable</para>
            </TD>
            <TD>
              <para>_PBPAGE System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_PCOLNO System Memory Variable</para>
            </TD>
            <TD>
              <para>_PCOPIES System Memory Variable</para>
            </TD>
            <TD>
              <para>_PDRIVER System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_PDSETUP System Memory Variable</para>
            </TD>
            <TD>
              <para>_PECODE System Memory Variable</para>
            </TD>
            <TD>
              <para>_PEJECT System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_PEPAGE System Memory Variable</para>
            </TD>
            <TD>
              <para>_PLENGTH System Memory Variable</para>
            </TD>
            <TD>
              <para>_PLINENO System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_PLOFFSET System Memory Variable</para>
            </TD>
            <TD>
              <para>_PPITCH System Memory Variable</para>
            </TD>
            <TD>
              <para>_PQUALITY System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_PRETEXT System Memory Variable</para>
            </TD>
            <TD>
              <para>_PSCODE System Memory Variable</para>
            </TD>
            <TD>
              <para>_PSPACING System Memory Variable</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>_PWAIT System Memory Variable</para>
            </TD>
            <TD>
              <para>PACK DATABASE Command</para>
            </TD>
            <TD>
              <para>PAD( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PCOL( ) Function</para>
            </TD>
            <TD>
              <para>PEMSTATUS( ) Function</para>
            </TD>
            <TD>
              <para>PLAY MACRO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>POP KEY Command</para>
            </TD>
            <TD>
              <para>POP MENU Command</para>
            </TD>
            <TD>
              <para>POP POPUP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>POPUP( ) Function</para>
            </TD>
            <TD>
              <para>PRINTJOB ... ENDPRINTJOB Command</para>
            </TD>
            <TD>
              <para>PRINTSTATUS( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PRMBAR( ) Function</para>
            </TD>
            <TD>
              <para>PRMPAD( ) Function</para>
            </TD>
            <TD>
              <para>PROMPT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PROW( ) Function</para>
            </TD>
            <TD>
              <para>PRTINFO( ) Function</para>
            </TD>
            <TD>
              <para>PUSH KEY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>PUSH MENU Command</para>
            </TD>
            <TD>
              <para>PUSH POPUP Command</para>
            </TD>
            <TD>
              <para>PUTFILE( ) Function</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Q</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>QUIT Command</para>
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
    <title>R</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>_RMARGIN System Memory Variable</para>
            </TD>
            <TD>
              <para>RD Command</para>
            </TD>
            <TD>
              <para>READKEY( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>READ Command</para>
            </TD>
            <TD>
              <para>READ MENU Command</para>
            </TD>
            <TD>
              <para>RELEASE BAR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>REFRESH() Function</para>
            </TD>
            <TD>
              <para>REINDEX Command</para>
            </TD>
            <TD>
              <para>RELEASE LIBRARY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RELEASE CLASSLIB Command</para>
            </TD>
            <TD>
              <para>RELEASE Command</para>
            </TD>
            <TD>
              <para>RELEASE PAD Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RELEASE MENUS Command</para>
            </TD>
            <TD>
              <para>RELEASE MODULE Command</para>
            </TD>
            <TD>
              <para>RELEASE WINDOWS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RELEASE POPUPS Command</para>
            </TD>
            <TD>
              <para>RELEASE PROCEDURE Command</para>
            </TD>
            <TD>
              <para>RENAME Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>REMOVE CLASS Command</para>
            </TD>
            <TD>
              <para>RENAME CLASS Command</para>
            </TD>
            <TD>
              <para>RENAME VIEW Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RENAME CONNECTION Command</para>
            </TD>
            <TD>
              <para>RENAME TABLE Command</para>
            </TD>
            <TD>
              <para>RESTORE FROM Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>REPORT Command</para>
            </TD>
            <TD>
              <para>REQUERY( ) Function</para>
            </TD>
            <TD>
              <para>RESTORE WINDOW Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESTORE MACROS Command</para>
            </TD>
            <TD>
              <para>RESTORE SCREEN Command</para>
            </TD>
            <TD>
              <para>RGBSCHEME( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RESUME Command</para>
            </TD>
            <TD>
              <para>RGB( ) Function</para>
            </TD>
            <TD>
              <para>RUN | ! Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RMDIR Command</para>
            </TD>
            <TD>
              <para>ROW( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>RUNSCRIPT Command</para>
            </TD>
            <TD>
              <para>RDLEVEL( ) Function</para>
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
              <para>SAVE MACROS Command</para>
            </TD>
            <TD>
              <para>SAVE SCREEN Command</para>
            </TD>
            <TD>
              <para>SAVE TO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SAVE WINDOWS Command</para>
            </TD>
            <TD>
              <para>SCHEME( ) Function</para>
            </TD>
            <TD>
              <para>SCOLS( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SCROLL Command</para>
            </TD>
            <TD>
              <para>_SCREEN System Memory Variable</para>
            </TD>
            <TD>
              <para>SET Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET ALTERNATE Command</para>
            </TD>
            <TD>
              <para>SET ANSI Command</para>
            </TD>
            <TD>
              <para>SET APLABOUT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET AUTOSAVE Command</para>
            </TD>
            <TD>
              <para>SET BELL Command</para>
            </TD>
            <TD>
              <para>SET BLINK Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET BORDER Command</para>
            </TD>
            <TD>
              <para>SET BRSTATUS Command</para>
            </TD>
            <TD>
              <para>SET CLASSLIB Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET CLEAR Command</para>
            </TD>
            <TD>
              <para>SET CLOCK Command</para>
            </TD>
            <TD>
              <para>SET COLOR OF Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET COLOR OF SCHEME Command</para>
            </TD>
            <TD>
              <para>SET COLOR SET Command</para>
            </TD>
            <TD>
              <para>SET COLOR TO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET COMPATIBLE Command</para>
            </TD>
            <TD>
              <para>SET CONFIRM Command</para>
            </TD>
            <TD>
              <para>SET CONSOLE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET CPCOMPILE</para>
            </TD>
            <TD>
              <para>SET CPDIALOG</para>
            </TD>
            <TD>
              <para>SET CURRENCY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET CURSOR Command</para>
            </TD>
            <TD>
              <para>SET DATASESSION Command</para>
            </TD>
            <TD>
              <para>SET DEBUG Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET DECIMALS Command</para>
            </TD>
            <TD>
              <para>SET DELIMITERS Command</para>
            </TD>
            <TD>
              <para>SET DEVELOPMENT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET DEVICE Command</para>
            </TD>
            <TD>
              <para>SET DISPLAY Command</para>
            </TD>
            <TD>
              <para>SET DOHISTORY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET ECHO Command</para>
            </TD>
            <TD>
              <para>SET ESCAPE Command</para>
            </TD>
            <TD>
              <para>SET FORMAT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET FUNCTION Command</para>
            </TD>
            <TD>
              <para>SET HEADINGS Command</para>
            </TD>
            <TD>
              <para>SET HELP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET HELPFILTER Command</para>
            </TD>
            <TD>
              <para>SET INTENSITY Command</para>
            </TD>
            <TD>
              <para>SET KEY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET KEYCOMP Command</para>
            </TD>
            <TD>
              <para>SET LOGERRORS Command</para>
            </TD>
            <TD>
              <para>SET MACDESKTOP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET MACHELP Command</para>
            </TD>
            <TD>
              <para>SET MACKEY Command</para>
            </TD>
            <TD>
              <para>SET MARGIN Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET MARK OF Command</para>
            </TD>
            <TD>
              <para>SET MARK TO Command</para>
            </TD>
            <TD>
              <para>SET MEMOWIDTH Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET MESSAGE Command</para>
            </TD>
            <TD>
              <para>SET MOUSE Command</para>
            </TD>
            <TD>
              <para>SET ODOMETER Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET OLEOBJECT Command</para>
            </TD>
            <TD>
              <para>SET PALETTE Command</para>
            </TD>
            <TD>
              <para>SET PDSETUP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET POINT Command</para>
            </TD>
            <TD>
              <para>SET PRINTER Command</para>
            </TD>
            <TD>
              <para>SET READBORDER Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET REFRESH Command</para>
            </TD>
            <TD>
              <para>SET RESOURCE Command</para>
            </TD>
            <TD>
              <para>SET SAFETY Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET SCOREBOARD Command</para>
            </TD>
            <TD>
              <para>SET SECONDS Command</para>
            </TD>
            <TD>
              <para>SET SEPARATOR Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET SHADOWS Command</para>
            </TD>
            <TD>
              <para>SET SKIP OF Command</para>
            </TD>
            <TD>
              <para>SET SPACE Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET STATUS Command</para>
            </TD>
            <TD>
              <para>SET STATUS BAR Command</para>
            </TD>
            <TD>
              <para>SET STEP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET STICKY Command</para>
            </TD>
            <TD>
              <para>SET SYSFORMATS Command</para>
            </TD>
            <TD>
              <para>SET SYSMENU Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET TALK Command</para>
            </TD>
            <TD>
              <para>SET TEXTMERGE Command</para>
            </TD>
            <TD>
              <para>SET TEXTMERGE DELIMITERS Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET TOPIC Command</para>
            </TD>
            <TD>
              <para>SET TOPIC ID Command</para>
            </TD>
            <TD>
              <para>SET TRBETWEEN Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET TYPEAHEAD Command</para>
            </TD>
            <TD>
              <para>SET VIEW Command</para>
            </TD>
            <TD>
              <para>SET WINDOW OF MEMO Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SET XCMDFILE Command</para>
            </TD>
            <TD>
              <para>_SHELL System Memory Variable</para>
            </TD>
            <TD>
              <para>SHOW GET Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SHOW GETS Command</para>
            </TD>
            <TD>
              <para>SHOW MENU Command</para>
            </TD>
            <TD>
              <para>SHOW OBJECT Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SHOW POPUP Command</para>
            </TD>
            <TD>
              <para>SHOW WINDOW Command</para>
            </TD>
            <TD>
              <para>SIZE POPUP Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SIZE WINDOW Command</para>
            </TD>
            <TD>
              <para>SKPBAR( ) Function</para>
            </TD>
            <TD>
              <para>SKPPAD( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SOUNDEX( ) Function</para>
            </TD>
            <TD>
              <para>_SPELLCHK System Memory Variable</para>
            </TD>
            <TD>
              <para>SQL functions</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SROWS( ) Function</para>
            </TD>
            <TD>
              <para>_STARTUP System Memory Variable</para>
            </TD>
            <TD>
              <para>SUSPEND Command</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SYS() Functions except SYS(2011)</para>
            </TD>
            <TD>
              <para>SYSMETRIC( ) Function</para>
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
              <para>_TABS System Memory Variable</para>
            </TD>
            <TD>
              <para>TEXT ... ENDTEXT Command</para>
            </TD>
            <TD>
              <para>TXTWIDTH( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TRANSFORM( ) Function</para>
            </TD>
            <TD>
              <para>_TRANSPORT System Memory Variable</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>TYPE Command</para>
            </TD>
            <TD>
              <para>_THROTTLE System Memory Variable</para>
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
              <para>UPDATED( ) Function</para>
            </TD>
            <TD>
              <para>USE Command</para>
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
              <para>VALIDATE DATABASE Command</para>
            </TD>
            <TD>
              <para>VARREAD( ) Function</para>
            </TD>
            <TD>
              <para>VERSION( ) Function</para>
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
              <para>_WINDOWS System Memory Variable</para>
            </TD>
            <TD>
              <para>_WIZARD System Memory Variable</para>
            </TD>
            <TD>
              <para>WCHILD( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WAIT Command</para>
            </TD>
            <TD>
              <para>WBORDER( ) Function</para>
            </TD>
            <TD>
              <para>WFONT( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WCOLS( ) Function</para>
            </TD>
            <TD>
              <para>WEXIST( ) Function</para>
            </TD>
            <TD>
              <para>WLROW( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WITH ... ENDWITH Command</para>
            </TD>
            <TD>
              <para>WLAST( ) Function</para>
            </TD>
            <TD>
              <para>WONTOP( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WMAXIMUM( ) Function</para>
            </TD>
            <TD>
              <para>WLCOL( ) Function</para>
            </TD>
            <TD>
              <para>WREAD( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WOUTPUT( ) Function</para>
            </TD>
            <TD>
              <para>WMINIMUM( ) Function</para>
            </TD>
            <TD>
              <para>WVISIBLE( ) Function</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WPARENT( ) Function</para>
            </TD>
            <TD>
              <para>WTITLE( ) Function</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WROWS( ) Function</para>
            </TD>
            <TD>
              <para>_WRAP System Memory Variable</para>
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
              <para>ZOOM WINDOW Command</para>
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