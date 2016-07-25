---
title: "CursorType, LockType, and EditMode Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c222016e-415d-485e-86c5-e29feac4297a
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
# CursorType, LockType, and EditMode Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates setting the <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> and <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink> properties before opening a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. It also shows the value of the <legacyLink xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode</legacyLink> property under various conditions. The EditModeOutput function is required for this procedure to run.</para>
    <code>// BeginEditModeJ
import com.ms.wfc.data.*;
import java.io.* ;

public class EditModeX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      EditModeX ();
      System.exit(0);
   }

   // EditModeX function

   static void EditModeX ()
   {

      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstEmployees = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String line = null;
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
            + "Initial Catalog='Pubs';Integrated Security='SSPI';";

      try
      {
         // Open recordset with data from Employees table.

         cnConn1 = new Connection();
         cnConn1.open(strCnn);
         rstEmployees = new Recordset();
         rstEmployees.setActiveConnection(cnConn1);
         rstEmployees.setCursorLocation(AdoEnums.CursorLocation.CLIENT);
         rstEmployees.setCursorType(AdoEnums.CursorType.STATIC);
         rstEmployees.setLockType(AdoEnums.LockType.BATCHOPTIMISTIC);
         rstEmployees.open("employee", cnConn1,
            AdoEnums.CursorType.STATIC,
            AdoEnums.LockType.BATCHOPTIMISTIC,
            AdoEnums.CommandType.TABLE);

         // Show the EditMode property under different editing states.

         rstEmployees.addNew();
         rstEmployees.getField("emp_id").setString("T-T55555M");
         rstEmployees.getField("fname").setString("temp_fname");
         rstEmployees.getField("lname").setString("temp_lname");
         EditModeOutput("After AddNew:", rstEmployees.getEditMode());
         rstEmployees.updateBatch();
         EditModeOutput("After Update:", rstEmployees.getEditMode());
         rstEmployees.getField("fname").setString("test");
         EditModeOutput("After Edit:", rstEmployees.getEditMode());

         System.out.println("\n\nPress &lt;Enter&gt; to continue..");
         in.readLine();

         // Delete new record because this is a demonstration.
         cnConn1.execute(
            "DELETE FROM employee WHERE emp_id = 'T-T55555M'");

         // Cleanup objects before exit.
         rstEmployees.close();
         cnConn1.close();

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // Check for null pointer for connection object.
         if (cnConn1==null)
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

   // EditModeOutput Function

   static void EditModeOutput(String strTemp, int intEditMode)
   {
      String strMessage="";
      // Print report based on the value of the EditMode
      // property.

      System.out.println("\n" + strTemp);
      strMessage ="\n\tEditMode = ";
      switch(intEditMode)
      {
      case AdoEnums.EditMode.NONE :
         strMessage+="adEditNone";
         break;
      case AdoEnums.EditMode.INPROGRESS :
         strMessage+="adEditInProgress";
         break;
      case AdoEnums.EditMode.ADD :
         strMessage+="adEditAdd";
         break;
      default :
         break;
      }
      System.out.println(strMessage);
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
// EndEditModeJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType Property</link>
<link xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode Property</link>
<link xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>