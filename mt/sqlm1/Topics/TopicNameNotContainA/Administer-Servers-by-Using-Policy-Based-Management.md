---
title: Administer Servers by Using Policy-Based Management
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef2a7b3b-614b-405d-a04a-2464a019df40
---
# Administer Servers by Using Policy-Based Management
  Policy\-Based Management is a system for managing one or more instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. When [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] policy administrators use Policy\-Based Management, they use [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to create policies to manage entities on the server, such as the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], databases, or other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] objects.  
  
## Benefits of Policy\-Based Management  
 Policy\-Based Management is helpful in resolving the issues presented in the following scenarios:  
  
-   A company policy prohibits enabling Database Mail or SQL Mail. A policy is created to check the server state of those two features. An administrator compares the server state to the policy. If the server state is out of compliance, the administrator chooses the Configure mode and the policy brings the server state into compliance.  
  
-   The [!INCLUDE[ssSampleDBobject](../../Token\Other/ssSampleDBobject_md.md)] database has a naming convention that requires all stored procedures to start with the letters AW\_. A policy is created to enforce this policy. An administrator tests this policy and receives a list of stored procedures that are out of compliance. If future stored procedures do not comply with this naming convention, the creation statements for the stored procedures fail.  
  
> [!NOTE]  
>  Be aware that policies can affect how some [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features work. For example, change data capture and transactional replication both use the systranschemas table, which does not have an index. If you enable a policy that all tables must have an index, enforcing compliance of the policy will cause these features to fail.  
  
 Policies are created and managed by using [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)]. The process includes the following steps:  
  
1.  Select a Policy\-Based Management facet that contains the properties to be configured.  
  
2.  Define a condition that specifies the state of a management facet.  
  
3.  Define a policy that contains the condition, additional conditions that filter the target sets, and the evaluation mode.  
  
4.  Check whether an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is in compliance with the policy.  
  
 For failed policies, Object Explorer indicates a critical health warning as a red icon next to the target and the nodes that are higher in the Object Explorer tree.  
  
> [!NOTE]  
>  When the system computes the object set for a policy, by default the system objects are excluded.  For example, if the object set of the policy refers to all tables, the policy will not apply to system tables. If users want to evaluate a policy against system objects, they can explicitly add system objects to the object set. However, though all policies are supported for **check on schedule** evaluation mode, for performance reason, not all policies with arbitrary object sets are supported for **check on change** evaluation mode. For more information, see [http:\/\/blogs.msdn.com\/b\/sqlpbm\/archive\/2009\/04\/13\/policy\-evaluation\-modes.aspx](http://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)  
  
## Policy\-Based Management Concepts  
 Policy\-Based Management has three components:  
  
-   Policy management  
  
     Policy administrators create policies.  
  
-   Explicit administration  
  
     Administrators select one or more managed targets and explicitly check that the targets comply with a specific policy, or explicitly make the targets comply with a policy.  
  
-   Evaluation modes  
  
     There are four evaluation modes, three of which can be automated:  
  
    -   **On demand**. This mode evaluates the policy when directly specified by the user.  
  
    -   **On change: prevent**. This automated mode uses DDL triggers to prevent policy violations.  
  
        > [!IMPORTANT]  
        >  If the nested triggers server configuration option is disabled, **On change: prevent** will not work correctly. Policy\-Based Management relies on DDL triggers to detect and roll back DDL operations that do not comply with policies that use this evaluation mode. Removing the Policy\-Based Management DDL triggers or disabling nest triggers, will cause this evaluation mode to fail or perform unexpectedly.  
  
    -   **On change: log only**. This automated mode uses event notification to evaluate a policy when a relevant change is made.  
  
    -   **On schedule**. This automated mode uses a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent job to periodically evaluate a policy.  
  
     When automated policies are not enabled, Policy\-Based Management will not affect system performance.  
  
## Policy\-Based Management Terms  
 Policy\-Based Management managed target  
 Entities that are managed by Policy\-Based Management, such as an instance of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], a database, a table, or an index. All targets in a server instance form a target hierarchy. A target set is the set of targets that results from applying a set of target filters to the target hierarchy, for example, all the tables in the database owned by the HumanResources schema.  
  
 Policy\-Based Management facet  
 A set of logical properties that model the behavior or characteristics for certain types of managed targets. The number and characteristics of the properties are built into the facet and can be added or removed by only the maker of the facet. A target type can implement one or more management facets, and a management facet can be implemented by one or more target types. Some properties of a facet can only apply to a specific version..  
  
 Policy\-Based Management condition  
 A Boolean expression that specifies a set of allowed states of a Policy\-Based Management managed target with regard to a management facet. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tries to observe collations when evaluating a condition. When [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] collations do not exactly match Windows collations, test your condition to determine how the algorithm resolves conflicts.  
  
 Policy\-Based Management policy  
 A Policy\-Based Management condition and the expected behavior, for example, evaluation mode, target filters, and schedule. A policy can contain only one condition. Policies can be enabled or disabled. Policies are stored in the msdb database.  
  
 Policy\-Based Management policy category  
 A user\-defined category to help manage policies. Users can classify policies into different policy categories. A policy belongs to one and only one policy category. Policy categories apply to databases and servers. At the database level, the following conditions apply:  
  
-   Database owners can subscribe a database to a set of policy categories.  
  
-   Only policies from its subscribed categories can govern a database.  
  
-   All databases implicitly subscribe to the default policy category.  
  
 At the server level, policy categories can be applied to all databases.  
  
 Effective policy  
 The effective policies of a target are those policies that govern this target. A policy is effective with regard to a target only if all the following conditions are satisfied:  
  
-   The policy is enabled.  
  
-   The target belongs to the target set of the policy.  
  
-   The target or one of the targets ancestors subscribes to the policy group that contains this policy.  
  
## Policy\-Based Management Tasks  
 Policy\-Based Management is a policy based system for managing one or more instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Use Policy\-Based Management to create conditions that contain condition expressions. Then, create policies that apply the conditions to database target objects.  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Describes how Policy\-Based Management policies are stored.|Policy\-Based Management Storage|  
|Describes how to configure alerts to notify policy administrators of policy failures.|[Configure Alerts to Notify Policy Administrators of Policy Failures](../../Topics\TopicNameNotContainA/Configure-Alerts-to-Notify-Policy-Administrators-of-Policy-Failures.md)|  
|Describes how to create, view, modify, and delete a Policy\-based Management condition.|[Create a New Policy-Based Management Condition](../../Topics\TopicNameContainA/Create-a-New-Policy-Based-Management-Condition.md)<br /><br /> [Delete a Policy-Based Management Condition](../../Topics\TopicNameContainA/Delete-a-Policy-Based-Management-Condition.md)<br /><br /> [View or Modify the Properties of a Policy-Based Management Condition](../../Topics\TopicNameContainA/View-or-Modify-the-Properties-of-a-Policy-Based-Management-Condition.md)|  
|Describes how to create, view, modify, and delete a Policy\-Based Management policy.|[Create a Policy-Based Management Policy](../../Topics\TopicNameContainA/Create-a-Policy-Based-Management-Policy.md)<br /><br /> [Delete a Policy-Based Management Policy](../../Topics\TopicNameContainA/Delete-a-Policy-Based-Management-Policy.md)<br /><br /> [View or Modify the Properties of a Policy-Based Management Policy](../../Topics\TopicNameContainA/View-or-Modify-the-Properties-of-a-Policy-Based-Management-Policy.md)|  
|Describes how to export and import a Policy\-based Management policy.|[Export a Policy-Based Management Policy](../../Topics\TopicNameContainA/Export-a-Policy-Based-Management-Policy.md)<br /><br /> [Import a Policy-Based Management Policy](../../Topics\TopicNameContainA/Import-a-Policy-Based-Management-Policy.md)|  
|Describes how to verify that a server instance, database, server object, or database object complies with a policy.|[Evaluate a Policy-Based Management Policy from an Object](../../Topics\TopicNameContainA/Evaluate-a-Policy-Based-Management-Policy-from-an-Object.md)<br /><br /> [Evaluate a Policy-Based Management Policy from That Policy](../../Topics\TopicNameContainA/Evaluate-a-Policy-Based-Management-Policy-from-That-Policy.md)<br /><br /> [Evaluate a Policy-Based Management Policy on a Schedule](../../Topics\TopicNameContainA/Evaluate-a-Policy-Based-Management-Policy-on-a-Schedule.md)|  
|Describes how to view and copy a Policy\-based Management facet state to a file.|[Working with Policy-Based Management Facets](../../Topics\TopicNameNotContainA/Working-with-Policy-Based-Management-Facets.md)|  
|Provides a set of policy files that you can import as best practice policies, and describes how to evaluate the policies against a target set that includes instances, instance objects, databases, or database objects.|[Monitor and Enforce Best Practices by Using Policy-Based Management](../../Topics\TopicNameNotContainA/Monitor-and-Enforce-Best-Practices-by-Using-Policy-Based-Management.md)|  
|Provides the F1 Help topics for the **PolicyManagement** node of Object Explorer in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)].|[Policy Management Node &#40;Object Explorer&#41;](../Topic/Policy%20Management%20Node%20\(Object%20Explorer\).md)|  
  
## See Also  
 [Policy-Based Management Views &#40;Transact-SQL&#41;](../Topic/Policy-Based%20Management%20Views%20\(Transact-SQL\).md)  
  
  