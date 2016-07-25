---
title: "Value Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 707be908-20ef-4bd6-a12c-8dc87fadd6ed
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
# Value Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property with <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> and <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> objects by displaying field and property values for the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table.</para>
    <code>// BeginValueJ
import java.io.*;
import com.ms.wfc.data.*;
import com.ms.com.*;

public class ValueX
{
   // Main Function
   public static void main (String[] args)
   {
      ValueX();
      System.exit(0);
   }
   static void ValueX()
   {
      // Define ADO Objects.
      Recordset rstEmployees = null;
      Field    fldLoop     = null;
      AdoProperty  prpLoop   = null;

      // Declarations.
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';" +
         "Initial Catalog='Pubs';Integrated Security='SSPI';";
      int intLoop;
      BufferedReader in = new 
         BufferedReader(new InputStreamReader(System.in));
      Variant varPropertyValue;
      String strMessage;

      try
      {
         // Open a Recordset with data from Employees table.
         rstEmployees = new Recordset();
         rstEmployees.open("employee", strCnn, 
            AdoEnums.CursorType.FORWARDONLY, AdoEnums.LockType.READONLY, 
            AdoEnums.CommandType.TABLE);

         System.out.println("Field values in rstEmployees\n");

         // Enumerate the Fields collection of the Employees
         // table.
         for(intLoop = 0;
            intLoop&lt;rstEmployees.getFields().getCount();intLoop++)
         {
            fldLoop = rstEmployees.getFields().getItem(intLoop);
            // Because Value is the default property of a
            // Field object, the use of the actual keyword
            // here is optional.
            System.out.println("\t" + fldLoop.getName() + " = " + 
               fldLoop.getValue());
         }
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
         System.out.println("Property values in rstEmployees\n");

         // Enumerate the Properties collection of the
         // Recordset object.
         int intCount = 0;
         for(intLoop = 0;
            intLoop&lt;rstEmployees.getProperties().getCount();intLoop++)
         {
            prpLoop = rstEmployees.getProperties().getItem(intLoop);
            // Because Value is the default property of a
            // Field object, the use of the actual keyword
            // here is optional.
            strMessage = "\t" + prpLoop.getName() + " =  ";
            varPropertyValue = prpLoop.getValue();
            short vttype =varPropertyValue.getvt();
            switch (vttype)
            {
            case Variant.VariantBoolean :
               {
                  if (varPropertyValue.getBoolean())
                     strMessage +="True";
                  else
                     strMessage +="False";
               }
               break;
            case Variant.VariantInt :
               strMessage += varPropertyValue.getInt();
               break;
            default :
               break;
            }
            System.out.println(strMessage);
            intCount++;
            // Loop used to display records
            if (intCount % 15 == 0)
            {
               System.out.println("\nPress &lt;Enter&gt; to continue..");
               in.readLine();
               intCount = 0;
            }

         }
         // Cleanup objects before exit.
         rstEmployees.close();
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }
      // System read requires this catch.
      catch(java.io.IOException je)
      {
         PrintIOError(je);
      }
      catch(AdoException ae)
      {
         // Notify the user of any errors that result from ADO.

         // As passing a recordset, check for null pointer first.
         if(rstEmployees != null)
         {
            PrintProviderError(rstEmployees.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
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
   static void PrintProviderError(Connection cnn1)
   {
      // Print Provider Errors from Connection Object.
      // ErrItem is an item object in the Connections Errors Collection.
      com.ms.wfc.data.Error               ErrItem = null;
      long                                 nCount = 0;
      int                                       i = 0;

      nCount = cnn1.getErrors().getCount();

      // If there are any errors in the collection, print them.
      if ( nCount &gt; 0)
      {
         // Collection ranges from 0 to nCount-1.
         for ( i=0;i&lt;nCount; i++)
         {
            ErrItem = cnn1.getErrors().getItem(i);
            System.out.println("\t Error Number: " + ErrItem.getNumber() 
               + "\t" + ErrItem.getDescription());
         }
      }
   }
   // PrintIOError Function
   static void PrintIOError(java.io.IOException je)
   {
      System.out.println("Error: \n");
      System.out.println("\t Source: " + je.getClass() + "\n");
      System.out.println("\t Description: "+ je.getMessage() + "\n");
   }
}
// EndValueJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
<link xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>