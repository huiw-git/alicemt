---
title: Supported ODBC API Functions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b28a8ed6-09b1-4acf-bf3e-f90bb32422de
translation.priority.ht: 
  - en-gb
---
# Supported ODBC API Functions
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The purpose of leveling is to inform the application what features are available to it from the driver. The Microsoft ODBC Desktop Database Drivers support all Core and Level 1 functions. </para>
    <para>For more information about conformance levels for functions and grammar, see <legacyLink xlink:href="f776d467-5d5d-4761-9043-3dad5f73c610">Conformance Levels</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
    <para>Support of ODBC API functions can be dependent on the driver used. The following table summarizes the support for functions. The leftmost column provides a link to the general reference page for each function. These reference pages are listed alphabetically in the <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink> section, under <legacyLink xlink:href="b33c3c43-ae66-44a3-be17-9cd82624dd96">ODBC Programmer's Reference</legacyLink>. The columns to the right provide links to driver-specific notes about each supported function. These driver-specific topics are listed in the "Other Programming Details" section for each driver. Alternatively, if the same remarks about a function apply to all the ODBC Desktop Database Drivers, the rightmost column provides a link to a topic that summarizes the Desktop Database Drivers' support for that function. These topics are listed at the end of the current section ("Supported ODBC API Functions").</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC Function</para>
          </TD>
          <TD>
            <para>Access Driver-specific notes</para>
          </TD>
          <TD>
            <para>dBASE Driver-specific notes</para>
          </TD>
          <TD>
            <para>Paradox Driver-specific notes</para>
          </TD>
          <TD>
            <para>Text File Driver-specific notes</para>
          </TD>
          <TD>
            <para>Excel Driver-specific notes</para>
          </TD>
          <TD>
            <para>Notes relevant to all drivers</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="40489bc5-3e2a-425e-892d-e0dc037f4d7a">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="3ece37af-db56-47fc-bc9d-6a7d0d8a00ec">SQLColAttributes</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="adb6f81d-e8c7-4748-9b1d-f7a053788bbc">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="ed44de2b-0b01-4dce-a340-f5eb3aac30b7">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="bbeef024-d470-4d28-b61b-26997ef41007">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="132fd1c0-1921-4a7d-910e-aedf1bff5453">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="7c4833e3-ff0c-4313-9ab8-21379ceab656">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="3ece37af-db56-47fc-bc9d-6a7d0d8a00ec">SQLColumns</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="adb6f81d-e8c7-4748-9b1d-f7a053788bbc">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="ed44de2b-0b01-4dce-a340-f5eb3aac30b7">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="bbeef024-d470-4d28-b61b-26997ef41007">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="132fd1c0-1921-4a7d-910e-aedf1bff5453">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="7c4833e3-ff0c-4313-9ab8-21379ceab656">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="f8d6e342-c010-434e-b1cd-f5371fb50a14">SQLConfigDataSource</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="59e84c4e-debe-49d7-b97b-84c736b0c793">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="9d133e9b-7545-464d-aa3c-677fa7e2a41d">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="c837aa31-068e-4fa3-bc00-aae09bec21de">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="c2ba486e-5e01-4e67-adb1-68511f5f0206">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="d7769021-bd18-4d8e-96e0-e184a82d6ca3">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="285cb1ea-f461-4596-97f2-fc57af05dede">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="e6e92199-7bb6-447c-8987-049a4c6ce05d">SQLGetCursorName</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="76399d74-1121-4c63-92ee-7d2984ac74af">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="c226aba7-a2f4-4b32-b640-92654b40e5a7">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="42ffdc9c-281b-4df5-ac6d-7b34f15ecd4c">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="43aab762-68f4-4128-b8f5-8878ea5f1258">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="fed4aea2-6d3d-4199-a5db-3d033eb63927">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="d69c2668-4260-4722-8c34-1c51caac307f">SQLGetStmtOption</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="f9ed31af-2fa9-4a0c-9639-08b63199b092">All drivers</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="bdedb044-8924-4ca4-85f3-8b37578e0257">SQLGetTypeInfo</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="a28b16eb-ca36-4297-9297-ecd7c107a84e">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="6e9ce02b-97c7-4c1a-91e0-829df7459c84">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="e65063c7-ba9e-4cf0-ac13-4bb5bd2937db">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="05a58975-093c-4bd9-bd72-b5f0026a6e36">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="708845be-e6a1-4677-8113-c52819a43fa4">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="bf169ed5-4d55-412c-b184-12065a726e89">SQLMoreResults</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="676da17b-daea-487f-b2d8-e579db6547cc">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="dbc8f17b-2913-4bdf-841c-d79213993cd8">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="4ca37b28-a6df-465b-8988-d422d37fc025">SQLProcedureColumns</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="34fee995-5848-4ecb-bda0-fc362a77b2d9">Access</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="d0d9ef10-2fd4-44a5-9334-649f186f4ba0">SQLProcedures</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="c996ad6f-e790-40f4-a962-843422496149">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="8cd2c2a2-25c8-4aff-951c-b593bbfc90ad">SQLSetConnectOption</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="58399bc4-d0b1-4eaa-a474-c92b2d5855ea">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="b1924c33-6820-4566-b716-6897807edd0f">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="050ee2be-594e-4dbd-af67-8b6aae756cd1">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="b631a20c-2f60-4102-a61d-93b8780a4620">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="528d21d1-4516-4497-9da4-7b87d77e622a">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="4e055946-12d4-4589-9891-41617a50f34e">SQLSetCursorName</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="9bd7c87b-d99d-4e23-b2db-868d3b461c94">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="8ef027ec-8512-48fe-8fe2-2ff7cd81e331">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="2a825ba7-7942-4c23-bcdb-c80dc12f8c86">SQLSetScrollOptions</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="51d643ed-015b-4639-969a-9491d9875aca">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="9cbe2b62-4cf7-43ab-8fb4-9a53df2c6b3f">SQLSetStmtOption</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="98db9631-eb9b-4962-abe4-96f495133a5d">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="bb2d9f21-bda0-4e50-a8be-f710db660034">SQLSpecialColumns</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="3de66fdf-053b-4354-979d-e76a5a5e975f">All drivers</legacyLink>             </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="45210682-cfea-4e5d-9951-bcf1cbe10f41">SQLStatistics</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="6117ac77-1020-4f0c-8eed-e671c34c1f21">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="631cec1b-66b7-4103-b9a7-ffd81da3c442">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="886cab83-d599-4fbc-9c88-e8cb833aac4b">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="311afc01-d656-425f-be43-4a8e7cbc9a97">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="02506664-8dcc-4bd0-a8bb-d49fcbdd5722">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SQLTables</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="94423cf9-341a-4db6-bb10-8f5448df7fc3">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="45938efb-b678-47d8-9345-644fa26ad679">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="d68adad6-97bd-4b47-bcf9-0102aafb00d4">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="9410b686-4b5b-4b51-b5ef-f9d2e7a48faa">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="496249e0-8eff-4c60-8358-5543bc3ead9c">SQLTransact</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="892b79c7-9e20-4d1f-bc60-d4b25694ca25">Access</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="159ca21a-ccc4-45e2-97ca-2a9387efa7df">dBASE</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="1d7f0c4c-f092-4bbb-9643-f7c9d07ed1af">Paradox</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="0349bd4e-f402-4a69-b215-046210a433de">Text File</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyLink xlink:href="821b4535-cec3-4e59-b681-87faf9d51575">Excel</legacyLink>             </para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following topics provide remarks about ODBC functions. These remarks apply to all ODBC Desktop Database Drivers.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3">SQLGetData (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f9ed31af-2fa9-4a0c-9639-08b63199b092">SQLGetStmtOption(Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="676da17b-daea-487f-b2d8-e579db6547cc">SQLMoreResults (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="dbc8f17b-2913-4bdf-841c-d79213993cd8">SQLPrepare (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="c996ad6f-e790-40f4-a962-843422496149">SQLProcedures (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9bd7c87b-d99d-4e23-b2db-868d3b461c94">SQLSetCursorName (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="8ef027ec-8512-48fe-8fe2-2ff7cd81e331">SQLSetPos (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="51d643ed-015b-4639-969a-9491d9875aca">SQLSetScrollOptions (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="98db9631-eb9b-4962-abe4-96f495133a5d">SQLSetStmtOption (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="3de66fdf-053b-4354-979d-e76a5a5e975f">SQLSpecialColumns (Desktop Database Drivers)</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>