---
title: "AbsolutePage, PageCount, and PageSize Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05f9f20e-0697-46bf-b004-76d7fc2e5d52
caps.latest.revision: 9
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
# AbsolutePage, PageCount, and PageSize Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink>, <legacyLink xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount</legacyLink>, and <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink> properties to display names and hire dates from the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table, five records at a time.</para>
    <code>// BeginAbsolutePageJ
// The WFC class includes the ADO objects.

import com.ms.wfc.data.*;
import java.io.* ;

public class AbsolutePageX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      AbsolutePageX();
      System.exit(0);
   }

   // AbsolutePageX function

   static void AbsolutePageX()
   {
      // Define ADO Objects.
      Recordset rstEmployees = null;

      // Declarations.
      BufferedReader in = new BufferedReader (new 
         InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
         + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      String strName;
      String strFName;
      String strLName;
      String strHDate;
      int intPage;
      int intRecord;

      try
      {
         rstEmployees = new Recordset();

         // Use client cursor to enable AbsolutePosition property.
         rstEmployees.setCursorLocation( AdoEnums.CursorLocation.CLIENT);

         // Open a recordset using client cursor for the Employees table.
         rstEmployees.open("employee", strCnn,
            AdoEnums.CursorType.FORWARDONLY,
            AdoEnums.LockType.READONLY,
            AdoEnums.CommandType.TABLE);

         // Display names and hire dates, five records at a time.

         rstEmployees.setPageSize(5);
         int intPageCount = rstEmployees.getPageCount();
         for ( intPage = 1; intPage &lt;= intPageCount; intPage++)
         {
            strName = "";
            rstEmployees.setAbsolutePage(intPage);
            for ( intRecord = 1; intRecord &lt;= rstEmployees.getPageSize(); 
               intRecord++)
            {
               strFName = rstEmployees.getField("fname").getString();
               strLName = rstEmployees.getField("lname").getString();
               strHDate = rstEmployees.getField("hire_date").getString();

               strHDate = strHDate.substring(5,7) + "/" + 
                  strHDate.substring(8,10) +
                  "/" + strHDate.substring(2,4);

               strName = strName + "\n" + strFName + " " + strLName + 
                  "  " + strHDate;
               rstEmployees.moveNext();
               if ( rstEmployees.getEOF())
                  break;
            }
            System.out.println(strName);
            // Get user input to display next records.

            System.out.println("\n\nPress &lt;Enter&gt; key to Continue.");
            line = in.readLine();
         }
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if (rstEmployees.getActiveConnection()==null)
            System.out.println("Exception: " + ae.getMessage());

         // As passing a Recordset, check for null pointer first.
         if (rstEmployees != null)
         {
            PrintProviderError(rstEmployees.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }
      // System read requires this catch.
      catch( java.io.IOException je)
      {
         PrintIOError(je);
      }
      finally
      {
         // Cleanup objects before exit.   
         if (rstEmployees != null)
            if (rstEmployees.getState() == 1)
               rstEmployees.close();
      }
   }

   // PrintProviderError Function

   static void PrintProviderError( Connection Cnn1 )
   {
      // Print Provider errors from Connection object.
      // ErrItem is an item object in the Connection's Errors collection.
      com.ms.wfc.data.Error  ErrItem = null;
      long nCount = 0;
      int  i      = 0;

      nCount = Cnn1.getErrors().getCount();

      // If there are any errors in the collection, print them.
      if( nCount &gt; 0);
      {
         // Collection ranges from 0 to nCount - 1
         for (i = 0; i&lt; nCount; i++)
         {
            ErrItem = Cnn1.getErrors().getItem(i);
            System.out.println("\t Error number: " + ErrItem.getNumber()
               + "\t" + ErrItem.getDescription() );
         }
      }

   }

   //.PrintIOError Function
   
   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}
// EndAbsolutePageJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage Property</link>
<link xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount Property</link>
<link xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>