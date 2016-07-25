---
title: "Handler Property Example (VJ++)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21e85d66-37db-4ce1-ad24-4344f43cebde
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
# Handler Property Example (VJ++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This example demonstrates the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS DataControl</legacyLink> object <legacyLink xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler</legacyLink> property. (See <legacyLink xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</legacyLink> for more details.)</para>
    <para>Assume the following sections in the parameter file, Msdfmap.ini, located on the server:</para>
    <code>[connect AuthorDataBase]
Access=ReadWrite
Connect="DSN=Pubs"
[sql AuthorById]
SQL="SELECT * FROM Authors WHERE au_id = ?"</code>
    <para>Your code looks like the following. The command assigned to the <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink> property will match the <legacyItalic>AuthorById</legacyItalic> identifier and will retrieve a row for author Michael O'Leary. Although the <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property in your code specifies the Northwind data source, that data source will be overwritten by the Msdfmap.ini <legacyItalic>connect</legacyItalic> section. The <legacyBold>DataControl</legacyBold> object's <legacyLink xlink:href="a29e3fb9-306d-497a-9a59-1856a914e5e9">Recordset</legacyLink> property is assigned to a disconnected <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object purely as a coding convenience.</para>
    <code>// BeginHandlerJ
import com.ms.wfc.data.*;
import com.ms.wfc.data.rds.*;
import java.io.* ;

public class HandlerX
{
   // The main entry point for the application.

   public static void main (String[] args)
   {
      HandlerX();
      System.exit(0);
   }

   // HandlerX function

   static void HandlerX()
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
         dc.setServer("MyServer");
         dc.setConnect("Data Source=Northwind");
         dc.setSQL("AuthorById(267-41-2394)");
         dc.Refresh();                  // Retrieve the record.
         // Use another recordset as a convenience.
         rstAuthors = (Recordset)dc.getRecordset();
         System.out.println("Author is '" +
                        rstAuthors.getField("au_fname").getString() +
                        " " +
                        rstAuthors.getField("au_lname").getString() +
                        "'");

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
// EndHandlerJ</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>