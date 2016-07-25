---
title: "InternetTimeout Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 757adb1b-d184-4887-bbe2-0f1bb6433f69
caps.latest.revision: 12
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
# InternetTimeout Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This example demonstrates the <legacyLink xlink:href="4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549">InternetTimeout</legacyLink> property, which exists on the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl</legacyLink> and <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace</legacyLink> objects. In this case, the <legacyBold>InternetTimout</legacyBold> property is demonstrated on the <legacyBold>DataControl</legacyBold> object and the timeout is set to 20 seconds.</para>
    <code>// BeginInternetTimeoutJ
// The WFC class includes the ADO objects.
import com.ms.wfc.data.*;
import com.ms.wfc.data.rds.*;
import java.io.* ;

public class InternetTimeoutX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      InternetTimeoutX();
      System.exit(0);
   }

   // InternetTimeoutX function

   static void InternetTimeoutX()
   {

      // Define ADO Objects.
      Recordset rstAuthors = null;

      // Declarations.
      BufferedReader in = 
         new BufferedReader (new InputStreamReader(System.in));
      int intCount = 0;
      int intDisplaysize = 15;

      try
      {
         IBindMgr dc = (IBindMgr) new DataControl();
         dc.setServer("http://MyServer");
         dc.setConnect("DSN=pubs");
         dc.setSQL("SELECT * FROM Authors");
         dc.setInternetTimeout(20000);   // Wait at least 20 seconds.
         dc.Refresh();
         rstAuthors = (Recordset)dc.getRecordset();
         while(!rstAuthors.getEOF())
         {
            System.out.println(rstAuthors.getField
               ("au_fname").getString() + " " + 
               rstAuthors.getField("au_lname").getString());
            intCount++;
            if(intCount % intDisplaysize == 0)
            {
               System.out.println("\nPress &lt;Enter&gt; to continue..");
               in.readLine();
               intCount = 0;
            }
            rstAuthors.moveNext();
         }
         
         System.out.println("\nPress &lt;Enter&gt; to continue..");
         in.readLine();
      }
      catch( AdoException ae )
      {
         // Notify user of any errors that result from ADO.

         // As passing a Recordset, check for null pointer first.
         if (rstAuthors != null)
         {
            PrintProviderError(rstAuthors.getActiveConnection());
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
      catch(java.lang.UnsatisfiedLinkError e)
      {
         System.out.println("Exception: " + e.getMessage());
      }
      catch(java.lang.NullPointerException ne)
      {
         System.out.println(
         "Exception: Attempt to use null where an object is required.");
      }   
      
      finally
      {
         // Cleanup objects before exit.   
         if (rstAuthors != null)
            if (rstAuthors.getState() == 1)
               rstAuthors.close();
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
// EndInternetTimeoutJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549">InternetTimeout Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>