---
title: Specify a Merge Article Resolver
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
---
# Specify a Merge Article Resolver
  This topic describes how to specify a merge article resolver in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Recommendations](#Recommendations)  
  
-   **To specify a merge article resolver, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   Merge replication allows the following types of article resolvers:  
  
    -   The default resolver. The behavior of the default resolver depends on whether the subscription is a client subscription or a server subscription. For more information about specifying subscription type, see [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../Topic/Specify%20a%20Merge%20Subscription%20Type%20and%20Conflict%20Resolution%20Priority%20\(SQL%20Server%20Management%20Studio\).md).  
  
    -   A custom resolver you have written, which can be a business logic handler \(written in managed code\) or a custom COM\-based resolver. For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md). If you need to implement custom logic that is executed for each replicated row, not just for conflicting rows, see [Implement a Business Logic Handler for a Merge Article](../../Topics\TopicNameContainA/Implement-a-Business-Logic-Handler-for-a-Merge-Article.md).  
  
    -   A standard COM\-based resolver, which is included with [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   To use a resolver other than the default resolver, you must copy the resolver to the computer on which the Merge Agent runs and register it \(if you are using a business logic handler, it must also be registered at the Publisher\). The Merge Agent runs at:  
  
    -   The Distributor for a push subscription  
  
    -   The Subscriber for a pull subscription  
  
    -   The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Internet Information Services \(IIS\) server for a pull subscription that uses Web synchronization  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 After the resolver is registered, specify that an article should use the resolver on the **Resolver** tab of the **Article Properties \- \<Article\>** dialog box, which is available in the New Publication Wizard and the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To specify a resolver  
  
1.  On the **Articles** page of the New Publication Wizard or the **Publication Properties \- \<Publication\>** dialog box, select a table.  
  
2.  Click **Article Properties**, and then click **Set Properties of Highlighted Table Article**.  
  
3.  On the **Article Properties \- \<Article\>** page, click the **Resolver** tab.  
  
4.  Select **Use a custom resolver \(registered at the Distributor\)**, and then in the list, click the resolver.  
  
5.  If the resolver requires input \(such as a column name\), specify it in the **Enter information needed by the resolver** text box.  
  
6.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
7.  Repeat this process for each article that requires a resolver.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
  
#### To register a custom conflict resolver  
  
1.  If you plan to register your own custom conflict resolver, create one of the following types:  
  
    -   Managed code\-based resolver as a business logic handler. For more information, see [Implement a Business Logic Handler for a Merge Article](../../Topics\TopicNameContainA/Implement-a-Business-Logic-Handler-for-a-Merge-Article.md).  
  
    -   Stored procedure\-based resolver and COM\-based resolver. For more information, see [Implement a Custom Conflict Resolver for a Merge Article](../../Topics\TopicNameContainA/Implement-a-Custom-Conflict-Resolver-for-a-Merge-Article.md).  
  
2.  To determine if the desired resolver is already registered, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](../Topic/sp_enumcustomresolvers%20\(Transact-SQL\).md) at the Publisher on any database. This displays a description of the custom resolver as well as the class identifier \(CLSID\) for each COM\-based resolver registered at the Distributor or information on the managed assembly for each business logic handler registered at the Distributor.  
  
3.  If the desired custom resolver is not already registered, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](../Topic/sp_registercustomresolver%20\(Transact-SQL\).md) at the Distributor. Specify a name for the resolver for **@article\_resolver**; for a business logic handler, this is the friendly name of the assembly. For COM\-based resolvers, specify the CLSID of the DLL for **@resolver\_clsid**, and for a business logic handler, specify a value of **true** for **@is\_dotnet\_assembly**, the name of the assembly for **@dotnet\_assembly\_name**, and the fully\-qualified name of the class that overrides [BusinessLogicModule](assetId:///T:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule) for **@dotnet\_class\_name**.  
  
    > [!NOTE]  
    >  If a business logic handler assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache \(GAC\), you need to specify the full path with the assembly name for **@dotnet\_assembly\_name**.  
  
4.  If the resolver is a COM\-based resolver:  
  
    -   Copy the custom resolver DLL to the Distributor for push subscriptions or to the Subscriber for pull subscriptions.  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] custom resolvers can be found in the [!INCLUDE[ssInstallPath](../../Token\Other/ssInstallPath_md.md)]COM directory.  
  
    -   Use regsvr32.exe to register the custom resolver DLL with the operating system. For example, executing the following from the command prompt registers the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Additive Conflict Resolver:  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  If the resolver is a business logic handler, deploy the assembly in the same folder as the Merge Agent executable \(replmerg.exe\), in the same folder as an application that invokes the Merge Agent, or in the folder specified for the **@dotnet\_assembly\_name** parameter in step 3.  
  
    > [!NOTE]  
    >  The default installation location of the Merge Agent executable is [!INCLUDE[ssInstallPath](../../Token\Other/ssInstallPath_md.md)]COM.  
  
#### To specify a custom resolver when defining a merge article  
  
1.  If you plan to use a custom conflict resolver, create and register the resolver using the above procedure.  
  
2.  At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](../Topic/sp_enumcustomresolvers%20\(Transact-SQL\).md) and note the name of the desired custom resolver in the **value** field of result set.  
  
3.  At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify the name of the resolver from step 2 for **@article\_resolver** and any required input to the custom resolver using the **@resolver\_info** parameter. For stored procedure\-based custom resolvers, **@resolver\_info** is the name of the stored procedure. For more information about required input for resolvers supplied by [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)], see [Microsoft COM-Based Resolvers](../../Topics\TopicNameNotContainA/Microsoft-COM-Based-Resolvers.md).  
  
#### To specify or change a custom resolver for an existing merge article  
  
1.  To determine if a custom resolver has been defined for an article, or to get the name of the resolver, execute [sp_helpmergearticle &#40;Transact-SQL&#41;](../Topic/sp_helpmergearticle%20\(Transact-SQL\).md). If there is a custom resolver defined for the article, its name will be displayed in the **article\_resolver** field. Any input supplied to the resolver will be displayed in the **resolver\_info** field of the result set.  
  
2.  At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](../Topic/sp_enumcustomresolvers%20\(Transact-SQL\).md) and note the name of the desired custom resolver in the **value** field of the result set.  
  
3.  At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify a value of **article\_resolver**, including the full path for business logic handlers, for **@property**, and the name of the desired custom resolver from step 2 for **@value**.  
  
4.  To change any required input for the custom resolver, execute [sp_changemergearticle &#40;Transact-SQL&#41;](../Topic/sp_changemergearticle%20\(Transact-SQL\).md) again. Specify a value of **resolver\_info** for **@property** and any required input to the custom resolver for **@value**. For stored procedure\-based custom resolvers, **@resolver\_info** is the name of the stored procedure. For more information about required input, see [Microsoft COM-Based Resolvers](../../Topics\TopicNameNotContainA/Microsoft-COM-Based-Resolvers.md).  
  
#### To unregister a custom conflict resolver  
  
1.  At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](../Topic/sp_enumcustomresolvers%20\(Transact-SQL\).md) and note the name of the custom resolver to remove in the **value** field of the result set.  
  
2.  Execute [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../Topic/sp_unregistercustomresolver%20\(Transact-SQL\).md) at the Distributor. Specify the full name of the custom resolver from step 1 for **@article\_resolver**.  
  
###  <a name="TsqlExample"></a> Examples \(Transact\-SQL\)  
 This example creates a new article and specifies that the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Averaging Conflict Resolver be used to calculate the average of the **UnitPrice** column when conflicts occur.  
  
 [!CODE [HowTo#sp_addmerge_resolver](../CodeSnippet/SQL15/replication/howto#sp_addmerge_resolver)]  
  
 This example changes an article to specify using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Additive Conflict Resolver to calculate the sum of the **UnitsOnOrder** column when conflicts occur.  
  
 [!CODE [HowTo#sp_changemerge_resolver](../CodeSnippet/SQL15/replication/howto#sp_changemerge_resolver)]  
  
## See Also  
 [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md)   
 [Implement a Business Logic Handler for a Merge Article](../../Topics\TopicNameContainA/Implement-a-Business-Logic-Handler-for-a-Merge-Article.md)  
  
  