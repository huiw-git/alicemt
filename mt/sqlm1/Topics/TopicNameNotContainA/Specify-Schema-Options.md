---
title: Specify Schema Options
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
---
# Specify Schema Options
  This topic describes how to specify schema options in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. When you are publishing a table or view, you can control the object creation options that are replicated for the published object. You can set these option when the article is created, and you can also change them at a later time. If you do not explicitly specify these options for an article, a default set of options will be defined.  
  
> [!NOTE]  
>  The default schema options when using replication stored procedures may differ from the default options when articles are added using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].  
  
 **In This Topic**  
  
-   **Before you begin:**  
  
     [Limitations and Restrictions](#Restrictions)  
  
     [Recommendations](#Recommendations)  
  
-   **To specify schema options, using:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact\-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Before You Begin  
  
###  <a name="Restrictions"></a> Limitations and Restrictions  
  
-   If you change schema options after a publication is created, you must generate a new snapshot.  
  
###  <a name="Recommendations"></a> Recommendations  
  
-   For the complete list of schema options, see the **@schema\_option** parameter of [sp_addarticle &#40;Transact-SQL&#41;](../Topic/sp_addarticle%20\(Transact-SQL\).md) and [sp_addmergearticle &#40;Transact-SQL&#41;](../Topic/sp_addmergearticle%20\(Transact-SQL\).md).  
  
##  <a name="SSMSProcedure"></a> Using SQL Server Management Studio  
 Specify schema options, such as whether to copy constraints and triggers to Subscribers, on the **Properties** tab of the **Article Properties \- \<Article\>** dialog box. This tab is available in the New Publication Wizard and the **Publication Properties \- \<Publication\>** dialog box. For more information about using the wizard and accessing the dialog box, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md) and [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
#### To specify schema options  
  
1.  On the **Articles** Page of the New Publication Wizard or **Publication Properties \- \<Publication\>** dialog box, select an article, and then click **Article Properties**.  
  
2.  Select which articles schema option changes should apply to:  
  
    -   Click **Set Properties of Highlighted \<ObjectType\> Article** to launch the **Article Properties \- \<ObjectName\>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.  
  
    -   Click **Set Properties of All \<ObjectType\> Articles** to launch the **Properties for All \<ObjectType\> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.  
  
        > [!NOTE]  
        >  Property changes made in the **Properties for All \<ObjectType\> Articles** dialog box override any made previously in the **Article Properties \- \<ObjectName\>** dialog box. If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first. Then set the properties for the individual objects.  
  
3.  In the **Copy Objects and Settings to Subscriber** and **Destination Object** sections of the **Properties** tab of the **Article Properties \- \<Article\>** dialog box, specify values for the options.  
  
4.  Modify any properties if necessary, and then click **OK**.  
  
5.  If you are in the **Publication Properties \- \<Publication\>** dialog box, click **OK** to save and close the dialog box.  
  
##  <a name="TsqlProcedure"></a> Using Transact\-SQL  
 Schema options are specified as a hexadecimal value that is the [| \(Bitwise OR\)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) result of one or more options. For more information, see [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md) and [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md).  
  
> [!NOTE]  
>  You must convert schema option values from **binary** to **int** before performing a bitwise operation. For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](../Topic/CAST%20and%20CONVERT%20\(Transact-SQL\).md).  
  
#### To specify schema options when defining an article for a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_addarticle](../Topic/sp_addarticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication**, a name for the article for **@article**, the database object being published for **@source\_object**, the type of database object for **@type**, and the [| \(Bitwise OR\)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) result of one or more schema options for **@schema\_option**. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
#### To specify schema options when defining an article for a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_addmergearticle](../Topic/sp_addmergearticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication**, a name for the article for **@article**, the database object being published for **@source\_object**, and the [| \(Bitwise OR\)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) result of one or more schema options for **@schema\_option**. For more information, see [Define an Article](../../Topics\TopicNameNotContainA/Define-an-Article.md).  
  
#### To change schema options for an existing article in a snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_helparticle](../Topic/sp_helparticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication** and the name of the article for **@article**. Note the value of the **schema\_option** column in the result set.  
  
2.  Execute a [& \(Bitwise AND\)](../Topic/&%20\(Bitwise%20AND\)%20\(Transact-SQL\).md) operation using the value from step 1 and the desired schema option value to determine if the option is set.  
  
    -   If the result is **0**, the option is not set.  
  
    -   If the result is the option value, the option is already set.  
  
3.  If the option is not set, execute a [| \(Bitwise OR\)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) operation using the value from step 1 and the desired schema option value.  
  
4.  At the Publisher on the publication database, execute [sp\_changearticle](../Topic/sp_changearticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication**, the name of the article for **@article**, a value of **schema\_option** for **@property**, and the hexadecimal result from step 3 for **@value**.  
  
5.  Run the Snapshot Agent to generate a new snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
#### To change schema options for an existing article in a merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_helpmergearticle](../Topic/sp_helpmergearticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication** and the name of the article for **@article**. Note the value of the **schema\_option** column in the result set.  
  
2.  Execute a [& \(Bitwise AND\)](../Topic/&%20\(Bitwise%20AND\)%20\(Transact-SQL\).md) operation using the value from step 1 and the desired schema option value to determine if the option is set.  
  
    -   If the result is **0**, the option is not set.  
  
    -   If the result is the option value, the option is already set.  
  
3.  If the option is not set, execute a [| \(Bitwise OR\)](../Topic/%7C%20\(Bitwise%20OR\)%20\(Transact-SQL\).md) operation using the value from step 1 and the desired schema option value.  
  
4.  At the Publisher on the publication database, execute [sp\_changemergearticle](../Topic/sp_changemergearticle%20\(Transact-SQL\).md). Specify the name of the publication to which the article belongs for **@publication**, the name of the article for **@article**, a value of **schema\_option** for **@property**, and the hexadecimal result from step 3 for **@value**.  
  
5.  Run the Snapshot Agent to generate a new snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
## See Also  
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Article Options for Transactional Replication](../../Topics\TopicNameNotContainA/Article-Options-for-Transactional-Replication.md)  
  
  