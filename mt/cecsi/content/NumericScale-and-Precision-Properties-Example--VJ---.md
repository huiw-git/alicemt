---
title: "NumericScale and Precision Properties Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca9f10d2-b5d1-449b-807b-649ef4fbf0bb
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
# NumericScale and Precision Properties Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale</legacyLink> and <legacyLink xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision</legacyLink> properties to display the numeric scale and precision of fields in the <legacyBold><legacyItalic>Discounts</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database.</para>
    <code>// BeginNumericScaleJ
import com.ms.wfc.data.*;
import java.io.* ;

public class NumericScaleX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      NumericScaleX();
      System.exit(0);
   }

   // NumericScaleX function

   static void NumericScaleX()
   {

      // Define ADO Objects.
      Recordset rstDiscounts = null;
      Field fldTemp = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"
          + "Initial Catalog='Pubs';Integrated Security='SSPI';";
      int intLoop;

      try
      {
         rstDiscounts = new Recordset();

         // Open recordset.
         rstDiscounts.open("Discounts", strCnn,
                    AdoEnums.CursorType.FORWARDONLY,
                    AdoEnums.LockType.READONLY,
                    AdoEnums.CommandType.TABLE);

         // Display numeric scale and precision of
         // numeric and small integer fields.
         for ( intLoop=0; intLoop &lt; 
            rstDiscounts.getFields().getCount();intLoop++)
         {
            fldTemp = rstDiscounts.getFields().getItem(intLoop);
            if((fldTemp.getType()== AdoEnums.DataType.NUMERIC) |
               (fldTemp.getType()== AdoEnums.DataType.SMALLINT))
            {
               System.out.println("\nField: "
                  + fldTemp.getName());
               System.out.println("\nNumeric scale: "
                  + fldTemp.getNumericScale());
               System.out.println("\nPrecision: "
                  + fldTemp.getPrecision());
               System.out.println("\n\nPress &lt;Enter&gt; to continue..");
               in.readLine();
            }
         }

      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstDiscounts != null)
         {
            PrintProviderError(rstDiscounts.getActiveConnection());
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
         if (rstDiscounts != null)
            if (rstDiscounts.getState() == 1)
               rstDiscounts.close();
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
// EndNumericScaleJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale Property</link>
<link xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>