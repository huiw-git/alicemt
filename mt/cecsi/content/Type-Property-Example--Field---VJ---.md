---
title: "Type Property Example (Field) (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65e19302-4682-41c8-ac7f-de1a4e23eb2b
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
# Type Property Example (Field) (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property by displaying the name of the constant that corresponds to the value of the <legacyBold>Type</legacyBold> property of all the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects in the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table. The FieldType function is required for this procedure to run.</para>
    <code>// BeginFieldTypeJ
import java.io.*;
import com.ms.wfc.data.*;

public class TypeFieldX
{

   // The main entry point of the application.

   public static void main (String[] args)
   {
      TypeFieldX();
      System.exit(0);
   }
   
   // TypeFieldX Function
   static void TypeFieldX()
   {
      // Define ADO Objects.
      Recordset rstEmployees = null;
      Field fldLoop = null;

      // Declarations.
      String strCnn = "Provider='sqloledb';Data Source='MySqlServer';"+
                "Initial Catalog='Pubs';Integrated Security='SSPI';";
      int intLoop;
      int intRecordCount = 0;
      BufferedReader in = 
         new BufferedReader(new InputStreamReader(System.in));

      try
      {
         // Open the Recordset with data from Employees table.
         rstEmployees = new Recordset();
         rstEmployees.open("employee", strCnn, 
            AdoEnums.CursorType.FORWARDONLY, AdoEnums.LockType.READONLY, 
            AdoEnums.CommandType.TABLE);

         System.out.println("Fields in the Employees table:\n");

         // Enumerate fields collection of Employees table.
         for(intLoop = 0;intLoop &lt; 
            rstEmployees.getFields().getCount();intLoop++)
         {
            intRecordCount++;
            // Loop needed for display of records
            if((intRecordCount % 6)==0)
            {
               System.out.println("Press &lt;Enter&gt; to continue..");
               in.readLine();
            }

            fldLoop = rstEmployees.getFields().getItem(intLoop);
            System.out.println("  Name:" + fldLoop.getName() + "\n"+
               "  Type:" + FieldType(fldLoop.getType()) + "\n");

         }
         System.out.println("Press &lt;Enter&gt; to continue");
         in.readLine();
      }
      catch(AdoException ae)
      {
         // Notify the user of any errors that result from ADO.

         // As passing a Recordset, check for the null pointer first.
         if(rstEmployees != null)
         {
            PrintProviderError(rstEmployees.getActiveConnection());
         }
         else
         {
            System.out.println("Exception: " + ae.getMessage());
         }
      }
      // System read requires this catch.
      catch(java.io.IOException je)
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
   // FieldType Function
   static String FieldType( int intType )
   {
      String strLoop = null;

         switch(intType)
         {
         case AdoEnums.DataType.CHAR:
            strLoop = "adChar";
            break;
         case AdoEnums.DataType.VARCHAR:
            strLoop ="adVarChar";
            break;
         case AdoEnums.DataType.SMALLINT:
            strLoop = "adSmallInt";
            break;
         case AdoEnums.DataType.UNSIGNEDTINYINT:
            strLoop = "adUnsignedTinyInt" ;
            break;
         case AdoEnums.DataType.DBTIMESTAMP:
            strLoop = "adDBTimeStamp";
            break;
         default:
            break;
         }

      return strLoop;
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
// EndFieldTypeJ
</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>