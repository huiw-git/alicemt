---
title: "GetRows Method Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44dde820-9596-439c-97a8-037d40d873f0
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
# GetRows Method Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink> method to retrieve a specified number of rows from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and to fill an array with the resulting data. The <legacyBold>GetRows</legacyBold> method will return less than the desired number of rows in two cases: either if <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> has been reached, or if <legacyBold>GetRows</legacyBold> tried to retrieve a record that was deleted by another user. The function returns <legacyBold>False</legacyBold> only if the second case occurs. The GetRowsOK function is required for this procedure to run.</para>
    <code>// BeginGetRowsJ
// The WFC class includes the ADO objects.

import com.ms.wfc.data.*;
import java.io.* ;
import com.ms.com.*;

public class GetRowsX 
{
    // The main entry point for the application.

   static Variant avarRecords = null;

   public static void main (String[] args)
   {
      GetRowsX();
      System.exit(0);
   }

   // GetRowsX  function

   static void GetRowsX()
   {

      // Define ADO Objects.
      Recordset rstEmployees = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
            + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      int intRows;
      int intRecord;
      int intUBound;
      int intDisplaysize = 15;

      try
      {
         // Open recordset with names and hire dates from Employees table.
         rstEmployees = new Recordset();
         rstEmployees.open("SELECT fName, lName, hire_date " +
                        "FROM Employee ORDER BY lName", strCnn,
                        AdoEnums.CursorType.FORWARDONLY,
                        AdoEnums.LockType.READONLY,
                        AdoEnums.CommandType.TEXT);

         while(true)
         {
            // Get user input for number of rows.
            System.out.println(
            "\nEnter number of rows to retrieve. (&lt;= 0 to Exit)");
            line = in.readLine().trim();

            // Convert string entry to int.
            intRows = Integer.parseInt(line);

            // Exit the application if intRows is negative or zero.
            if(intRows &lt;= 0)
               break;

            // If GetRowsOK is successful, print the results,
            // noting if the end of the file was reached.
            if(GetRowsOK(rstEmployees,intRows))
            {
               SafeArray sa = avarRecords.toSafeArray();
               intUBound = sa.getUBound(2);
               if ( intRows &gt; (intUBound + 1))
                  System.out.println("\n(Not enough records in " +
                     "Recordset to retrieve " + intRows + " rows.)");
               System.out.println("\n" + (intUBound+ 1) +
                              " records found.\n");

               // Print the retrieved data.

               for ( intRecord = sa.getLBound();
                   intRecord  &lt;= intUBound; intRecord++)
               {

                  System.out.println(
                     " " + sa.getString(0, intRecord) + " " +
                     sa.getString(1, intRecord) + ", " +
                     sa.getString(2, intRecord));
                  if ( ((intRecord +1) % intDisplaysize) == 0)
                  {
                     System.out.println("\nPress &lt;Enter&gt; to continue..");
                     in.readLine();
                  }

               }
            }
            else
            {
               // Assuming the GetRows error was due to data
               // changes by another user, use Requery to
               // refresh the Recordset and start over.
               System.out.println("\nGetRows failed--retry? (Y/N)");
               if(in.readLine().trim().toUpperCase().equals("Y"))
                  rstEmployees.requery();
               else
               {
                  System.out.println("GetRows failed!");
                  break;
               }
            }

            // Because using GetRows leaves the current
            // record pointer at the last record accessed,
            // move the pointer back to the beginning of the
            // Recordset before looping back for another search.
            rstEmployees.moveFirst();
         }

         // Cleanup objects before exit.
         rstEmployees.close();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

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

      // Display Error that the application has attempted to convert
      // a string of inappropriate format to one of the numeric types.
      catch(java.lang.NumberFormatException ne)
      {
         System.out.println(
            "Exception: Must specify an Integer value." );
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rstEmployees != null)
            if (rstEmployees.getState() == 1)
               rstEmployees.close();
      }

   }

   // GetRowsOK Function

   static boolean GetRowsOK(Recordset rstTemp,int intNumber)
      {
      // Store results of GetRows method in array.
      avarRecords = rstTemp.getRows(intNumber);

      // Return False only if fewer than the desired
      // number of rows were returned, but not because the
      // end of the Recordset was reached.
      if ( intNumber &gt; (avarRecords.toSafeArray().getUBound(2)+ 1)
               &amp;&amp; !(rstTemp.getEOF()))
         return false;
      else
         return true;

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

   // PrintIOError Function

   static void PrintIOError( java.io.IOException je)
   {
      System.out.println("Error \n");
      System.out.println("\tSource = " + je.getClass() + "\n");
      System.out.println("\tDescription = " + je.getMessage() + "\n");
   }
}
// EndGetRowsJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF, EOF Properties</link>
<link xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>