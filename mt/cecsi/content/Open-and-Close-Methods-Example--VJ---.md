---
title: "Open and Close Methods Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b7dd9f8-4751-48fb-a75d-c6f75d80d928
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
# Open and Close Methods Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyBold>Open</legacyBold> and <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> methods on both <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> objects that have been opened.</para>
    <code>// BeginOpenJ
import com.ms.wfc.data.*;
import java.io.* ;
import com.ms.com.*;

public class OpenX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      OpenX();
      System.exit(0);
   }

   // OpenX function

   static void OpenX()
   {

      // Define ADO Objects.
      Connection cnConn1 = null;
      Recordset rstEmployees = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
                  + "Initial Catalog='Pubs';Integrated Security='SSPI';";
      Variant varDate;
      String strHDate;

      try
      {
         // Open connection.
         cnConn1 = new Connection();
         cnConn1.open(strCnn);

         // Open Employees table.
         rstEmployees = new Recordset();
         rstEmployees.setCursorType(AdoEnums.CursorType.KEYSET);
         rstEmployees.setLockType(AdoEnums.LockType.OPTIMISTIC);
         rstEmployees.open("Employee", cnConn1,
                    AdoEnums.CursorType.KEYSET,
                    AdoEnums.LockType.OPTIMISTIC,
                    AdoEnums.CommandType.TABLE);

         // Assign the first employee record's hire date
         // to a variable, then change the hire date.
         varDate = rstEmployees.getField("hire_date").getOriginalValue();
         System.out.println("Original data\n");
         System.out.println("\tName - Hire Date");
         strHDate = rstEmployees.getField("hire_date").getString();
         strHDate = strHDate.substring(5,7) + "/" + 
            strHDate.substring(8,10)
             + "/" + strHDate.substring(2,4);
         System.out.println("\t" + 
            rstEmployees.getField("fName").getString()+ " "
             + rstEmployees.getField("lName").getString()+ " - "
             + strHDate);
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
         rstEmployees.getField("hire_date").setString("1/1/1900");
         rstEmployees.update();
         System.out.println("Changed data\n");
         System.out.println("\tName - Hire Date");
         strHDate = rstEmployees.getField("hire_date").getString();
         strHDate = strHDate.substring(5,7) + "/" + 
            strHDate.substring(8,10)
             + "/" + strHDate.substring(0,4);
         System.out.println("\t" + 
            rstEmployees.getField("fName").getString()+ " "
             + rstEmployees.getField("lName").getString()+ " - "
             + strHDate);
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();

         // Requery Recordset and reset the hire date.
         rstEmployees.requery();
         rstEmployees.getField("hire_date").setValue(varDate);
         rstEmployees.update();
         System.out.println("Data after reset\n");
         System.out.println("\tName - Hire Date");
         strHDate = rstEmployees.getField("hire_date").getString();
         strHDate = strHDate.substring(5,7) + "/" + 
            strHDate.substring(8,10)
             + "/" + strHDate.substring(2,4);
         System.out.println("\t" + 
            rstEmployees.getField("fName").getString()+ " "
             + rstEmployees.getField("lName").getString()+ " - "
             + strHDate);
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
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
      
      finally
      {
         // Cleanup objects before exit.   
         if (rstEmployees != null)
            if (rstEmployees.getState() == 1)
               rstEmployees.close();
         // Cleanup objects before exit.   
         if (cnConn1 != null)
            if (cnConn1.getState() == 1)
               cnConn1.close();
      }

   }

   // PrintProviderError Function

   static void PrintProviderError( Connection Cnn1 )
   {
      // Print Provider errors from Connection object.
      // ErrItem is an item object in the Connections Errors collection.
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
// EndOpenJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close Method</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>