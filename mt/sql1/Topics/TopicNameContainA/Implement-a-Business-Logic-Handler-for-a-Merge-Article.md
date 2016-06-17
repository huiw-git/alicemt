---
title: Implement a Business Logic Handler for a Merge Article
H1: na
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
---
# Implement a Business Logic Handler for a Merge Article
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction address="Intro">
    <?Comment Margi: Optional comment:Topic Title:CombinedHowToTopicTemplate_(DxEditorTags)DxStudioSource:16b50312-61e4-4eae-b1f4-2a964f6e171f.dxml------------------Content Source(s): 2011-10-25T21:01:00Z?>
    <para>This topic describes how to implement a business logic handler for a merge article in <token>ssCurrent</token> by using replication programming or Replication Management Objects (RMO). </para>
    <para>The <codeEntityReference autoUpgrade="true">N:Microsoft.SqlServer.Replication.BusinessLogicSupport</codeEntityReference> namespace implements an interface that enables you to write complex business logic to handle events that occur during the merge replication synchronization process. Methods in the business logic handler can be invoked by the replication process for each changed row that is replicated during synchronization. </para>
    <para>The general process for implementing a business logic handler is:</para>
    <list class="ordered">
      <listItem>
        <para>Create the business logic hander assembly.</para>
      </listItem>
      <listItem>
        <para>Register the assembly at the Distributor.</para>
      </listItem>
      <listItem>
        <para>Deploy the assembly at the server on which the Merge Agent runs. For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor. When you are using Web synchronization, the agent runs on the Web server.</para>
      </listItem>
      <listItem>
        <para>Create an article that uses the business logic handler or modify an existing article to use the business logic handler.</para>
      </listItem>
    </list>
    <para>The business logic handler you specify is executed for every row that is synchronized. Complex logic and calls to other applications or network services can impact performance. For more information about business logic handlers, see <link xlink:href="9d4da2ef-c17f-4a31-a1f6-5c3b7ca85f71">Executing Business Logic During Merge Synchronization</link>.</para>
    <para>
      <embeddedLabel>In This Topic</embeddedLabel>
    </para>
    <?Comment Margi: IF YOU USE THIS TEMPLATE TO CREATE TOPICS FOR .CHM FILES:Use internal links instead of Legacy Links in this list. Here's the code for these internal links:Before you begin: Limitations and Restrictions,Prerequisites,Recommendations,SecurityToReplaceThisText, using: SQL Server Management Studio,Transact-SQL,PowerShellFollow Up: AfterReplaceThisText 2011-10-25T21:01:00Z  Id='1?>
    <list class="bullet">
      <?CommentEnd Id='1'
    ?>
      <listItem>
        <para>
          <embeddedLabel>To implement a business logic handler for a merge article, using: </embeddedLabel>
        </para>
        <para>
          <legacyLink xlink:href="#ReplProg">Replication Programming</legacyLink>
        </para>
        <para>
          <legacyLink xlink:href="#RMOProcedure">Replication Management Objects (RMO)</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="ReplProg">
    <title>Using Replication Programming</title>
    <content>
      <procedure>
        <title>To create and deploy a business logic handler</title>
        <steps class="ordered">
          <step>
            <content>
              <para>In <token>msCoName</token> Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler. </para>
            </content>
          </step>
          <step>
            <content>
              <para>Add references to the project for the following namespaces.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Assembly Reference</para>
                    </TD>
                    <TD>
                      <para>Location</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <codeEntityReference autoUpgrade="true">N:Microsoft.SqlServer.Replication.BusinessLogicSupport</codeEntityReference>
                      </para>
                    </TD>
                    <TD>
                      <para>
                        <token>ssInstallPath</token>COM (default installation)</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <codeEntityReference autoUpgrade="true">N:System.Data</codeEntityReference>
                      </para>
                    </TD>
                    <TD>
                      <para>GAC (component of the .NET Framework)</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <codeEntityReference autoUpgrade="true">N:System.Data.Common</codeEntityReference>
                      </para>
                    </TD>
                    <TD>
                      <para>GAC (component of the .NET Framework)</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </step>
          <step>
            <content>
              <para>Add a class that overrides the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule</codeEntityReference> class.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Implement the <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates</codeEntityReference> property to indicate the types of changes that are handled. </para>
            </content>
          </step>
          <step>
            <content>
              <para>Override one or more of the following methods of the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule</codeEntityReference> class:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)</codeEntityReference> - invoked when a data change is committed during synchronization.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)</codeEntityReference> - invoked when an error occurs when a DELETE statement is being uploaded or downloaded.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)</codeEntityReference> - invoked when DELETE statements are being uploaded or downloaded.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)</codeEntityReference> - invoked when an error occurs when an INSERT statement is being uploaded or downloaded.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)</codeEntityReference> - invoked when INSERT statements are being uploaded or downloaded.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)</codeEntityReference> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)</codeEntityReference> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)</codeEntityReference> - invoked when an error occurs when an UPDATE statement is being uploaded or downloaded.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)</codeEntityReference> - invoked when UPDATE statements are being uploaded or downloaded.  </para>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>Build the project to create the business logic handler assembly.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Deploy the assembly in the directory that contains the Merge Agent executable file (replmerg.exe), which for a default installation is <token>ssInstallPath</token>COM, or install it in the .NET global assembly cache (GAC). You should only install the assembly in the GAC if applications other than the Merge Agent require access to the assembly. The assembly can be installed into the GAC using the Global Assembly Cache tool (<legacyBold>Gacutil.exe)</legacyBold> provided in the .NET Framework SDK. </para>
              <alert class="note">
                <para>A business logic handler must be deployed on every server on which the Merge Agent runs, which includes the IIS server that hosts the replisapi.dll when using Web synchronization.  </para>
              </alert>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To register a business logic handler</title>
        <steps class="ordered">
          <step>
            <content>
              <para>At the Publisher, execute <link xlink:href="81bd0d3a-48dc-42b1-b662-c630f61fc630">sp_enumcustomresolvers (Transact-SQL)</link> to verify that the assembly has not already been registered as a business logic handler.</para>
            </content>
          </step>
          <step>
            <content>
              <para>At the Distributor, execute <link xlink:href="6d2b0472-0e1f-4005-833c-735d1940fe93">sp_registercustomresolver (Transact-SQL)</link>, specifying a friendly name for the business logic handler for <legacyBold>@article_resolver</legacyBold>, a value of <languageKeyword>true</languageKeyword> for <legacyBold>@is_dotnet_assembly</legacyBold>, the name of the assembly for <legacyBold>@dotnet_assembly_name</legacyBold>, and the fully-qualified name of the class that overrides <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule</codeEntityReference> for <legacyBold>@dotnet_class_name</legacyBold>. </para>
              <alert class="note">
                <para>If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for <legacyBold>@dotnet_assembly_name</legacyBold>. When using Web synchronization, you must specify the location of assembly at the Web server.</para>
              </alert>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To use a business logic handler with a new table article</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Execute <link xlink:href="0df654ea-24e2-4c61-a75a-ecaa7a140a6c">sp_addmergearticle (Transact-SQL)</link> to define an article, specifying the friendly name of the business logic handler for <legacyBold>@article_resolver</legacyBold>. For more information, see <link xlink:href="220584d8-b291-43ae-b036-fbba3cc07a2e">Define an Article</link>. </para>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To use a business logic handler with an existing table article</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Execute <link xlink:href="0dc3da5c-4af6-45be-b5f0-074da182def2">sp_changemergearticle (Transact-SQL)</link>, specifying <legacyBold>@publication</legacyBold>, <legacyBold>@article</legacyBold>, a value of <legacyBold>article_resolver</legacyBold> for <legacyBold>@property</legacyBold>, and the friendly name of the business logic handler for <legacyBold>@value</legacyBold>.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
    <sections>
      <section address="TsqlExample">
        <title>Examples (Replication Programming)</title>
        <content>
          <?Comment Margi: Optional, For simple Transact-SQL tasks, an inline C1 example is preferable. 2011-10-25T21:01:00Z?>
          <para>This example shows a business logic handler that creates an audit log.</para>
          <codeReference>HowTo#rmo_BusinessLogicCode</codeReference>
          <codeReference>HowTo#rmo_vb_BusinessLogicCode</codeReference>
          <para>The following example registers a business logic handler assembly at the Distributor and changes an existing merge article to use this custom business logic.</para>
          <codeReference>HowTo#sp_RegisterBLH_10</codeReference>
          
        </content>
      </section>
    </sections>
  </section>
  <section address="RMOProcedure">
    <title>Using Replication Management Objects (RMO)</title>
    <content>
      <procedure>
        <title>To create a business logic handler</title>
        <steps class="ordered">
          <step>
            <content>
              <para>In <token>msCoName</token> Visual Studio, create a new project for the .NET assembly that contains the code that implements the business logic handler. </para>
            </content>
          </step>
          <step>
            <content>
              <para>Add references to the project for the following namespaces.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Assembly Reference</para>
                    </TD>
                    <TD>
                      <para>Location</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>
                        <codeEntityReference autoUpgrade="true">N:Microsoft.SqlServer.Replication.BusinessLogicSupport</codeEntityReference>
                      </para>
                    </TD>
                    <TD>
                      <para>
                        <token>ssInstallPath</token>COM (default installation)</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <codeEntityReference autoUpgrade="true">N:System.Data</codeEntityReference>
                      </para>
                    </TD>
                    <TD>
                      <para>GAC (component of the .NET Framework)</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>
                        <codeEntityReference autoUpgrade="true">N:System.Data.Common</codeEntityReference>
                      </para>
                    </TD>
                    <TD>
                      <para>GAC (component of the .NET Framework)</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </step>
          <step>
            <content>
              <para>Add a class that overrides the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule</codeEntityReference> class.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Implement the <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates</codeEntityReference> property to indicate the types of changes that are handled. </para>
            </content>
          </step>
          <step>
            <content>
              <para>Override one or more of the following methods of the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule</codeEntityReference> class:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Guid)</codeEntityReference> - invoked when a data change is committed during synchronization.</para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)</codeEntityReference> - invoked if an error occurs while a DELETE statement is being uploaded or downloaded.</para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Int32@,System.String@)</codeEntityReference> - invoked when DELETE statements are being uploaded or downloaded.</para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)</codeEntityReference> - invoked if an error occurs when an INSERT statement is being uploaded or downloaded.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)</codeEntityReference> - invoked when INSERT statements are being uploaded or downloaded.</para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler(System.Data.DataSet,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)</codeEntityReference> - invoked when conflicting UPDATE statements occur at the Publisher and Subscriber.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,Microsoft.SqlServer.Replication.BusinessLogicSupport.ConflictLogType@,System.String@,System.Int32@,System.String@)</codeEntityReference> - invoked when UPDATE statements conflict with DELETE statements at the Publisher and Subscriber.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,Microsoft.SqlServer.Replication.BusinessLogicSupport.ErrorLogType@,System.String@,System.Int32,System.String,System.Int32@,System.String@)</codeEntityReference> - invoked if an error occurs when an UPDATE statement is being uploaded or downloaded.  </para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler(Microsoft.SqlServer.Replication.BusinessLogicSupport.SourceIdentifier,System.Data.DataSet,System.Data.DataSet@,System.Int32@,System.String@)</codeEntityReference> - invoked when UPDATE statements are being uploaded or downloaded.  </para>
                </listItem>
              </list>
              <alert class="note">
                <para>Any article conflicts not explicitly handled by your custom business logic are handled by the default resolver for the article.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Build the project to create the business logic handler assembly.</para>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To register a business logic handler</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Create a connection to the Distributor by using the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Management.Common.ServerConnection</codeEntityReference> class.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Create an instance of the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.ReplicationServer</codeEntityReference> class. Pass the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Management.Common.ServerConnection</codeEntityReference> from step 1.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Call <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers</codeEntityReference> and check the returned <codeEntityReference autoUpgrade="true">T:System.Collections.ArrayList</codeEntityReference> object to ensure that the assembly has not already been registered as a business logic handler.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Create an instance of the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.BusinessLogicHandler</codeEntityReference> class. Specify the following properties:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName</codeEntityReference> - the name of the .NET assembly. If the assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the GAC, you must include the full path with the assembly name. You must include the full path with the assembly name when using a business logic handler with Web synchronization.</para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName</codeEntityReference> - the fully-qualified name of the class that overrides <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule</codeEntityReference> and implements the business logic handler.</para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName</codeEntityReference> - a friendly name you use when you access the business logic handler.</para>
                </listItem>
                <listItem>
                  <para>
                    <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly</codeEntityReference> - a value of <languageKeyword>true</languageKeyword>. </para>
                </listItem>
              </list>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To deploy a business logic handler</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Deploy the assembly on the server where the Merge Agent runs in the file location specified when the business logic handler was registered at the Distributor. For a pull subscription the agent runs on the Subscriber, and for a push subscription the agent runs on the Distributor. When you are using Web synchronization, the agent runs on the Web server. If the full path was not included with the assembly name when the business logic handler was registered, deploy the assembly in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent. You may install the assembly in the GAC if there are multiple applications that use the same assembly.</para>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To use a business logic handler with a new table article</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Create a connection to the Publisher by using the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Management.Common.ServerConnection</codeEntityReference> class.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Create an instance of the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.MergeArticle</codeEntityReference> class. Set the following properties:</para>
              <list class="bullet">
                <listItem>
                  <para>The name of the article for <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.Article.Name</codeEntityReference>.</para>
                </listItem>
                <listItem>
                  <para>The name of the publication for <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.Article.PublicationName</codeEntityReference>.</para>
                </listItem>
                <listItem>
                  <para>The name of the publication database for <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.Article.DatabaseName</codeEntityReference>.</para>
                </listItem>
                <listItem>
                  <para>The friendly name of the business logic handler (<codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName</codeEntityReference>) for <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver</codeEntityReference>.</para>
                </listItem>
              </list>
            </content>
          </step>
          <step>
            <content>
              <para>Call the <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.Article.Create</codeEntityReference> method. For more information, see <link xlink:href="220584d8-b291-43ae-b036-fbba3cc07a2e">Define an Article</link>.</para>
            </content>
          </step>
        </steps>
      </procedure>
      <procedure>
        <title>To use a business logic handler with an existing table article</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Create a connection to the Publisher by using the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Management.Common.ServerConnection</codeEntityReference> class.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Create an instance of the <codeEntityReference autoUpgrade="true">T:Microsoft.SqlServer.Replication.MergeArticle</codeEntityReference> class.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Set the <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.Article.Name</codeEntityReference>, <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.Article.PublicationName</codeEntityReference>, and <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.Article.DatabaseName</codeEntityReference> properties. </para>
            </content>
          </step>
          <step>
            <content>
              <para>Set the connection from step 1 for the <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext</codeEntityReference> property. </para>
            </content>
          </step>
          <step>
            <content>
              <para>Call the <codeEntityReference autoUpgrade="true">M:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties</codeEntityReference> method to get the properties of the object. If this method returns <languageKeyword>false</languageKeyword>, either the article properties in step 3 were defined incorrectly or the article does not exist. For more information, see <link xlink:href="e71831fa-3d39-4e4a-9706-4d3a497082cc">View and Modify Article Properties</link>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Set the friendly name of the business logic handler for <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver</codeEntityReference>. This is the value of the <codeEntityReference autoUpgrade="true">P:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName</codeEntityReference> property specified when registering the business logic handler. </para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
    <sections>
      <section address="PShellExample">
        <title>Examples (RMO)</title>
        <content>
          <para>This example is a business logic handler that logs information about inserts, updates, and deletes at the Subscriber.</para>
          <codeReference>HowTo#rmo_BusinessLogicCode</codeReference>
          <codeReference>HowTo#rmo_vb_BusinessLogicCode</codeReference>
          <para>This example registers a business logic handler at the Distributor.</para>
          <codeReference>HowTo#rmo_RegisterBLH_10</codeReference>
          <codeReference>HowTo#rmo_vb_RegisterBLH_10</codeReference>
          <para>This example changes an existing article to use the business logic handler.</para>
          <codeReference>HowTo#rmo_ChangeMergeArticle_BLH</codeReference>
          <codeReference>HowTo#rmo_vb_ChangeMergeArticle_BLH</codeReference>
          
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="76bd8524-ebc1-4d80-b5a2-4169944d6ac0">Implement a Stored Procedure-Based Custom Conflict Resolver for a Merge Article</link>
<link xlink:href="edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6">How to: Debug a Business Logic Handler (Replication Programming)</link>
<link xlink:href="1ab2635d-0992-4c99-b17d-041d02ec9a7c">Replication Security Best Practices</link>
<link xlink:href="37476d50-fb47-49e3-9504-3b163ac381d8">Programming with Replication Management Objects</link></relatedTopics>
</developerConceptualDocument>



