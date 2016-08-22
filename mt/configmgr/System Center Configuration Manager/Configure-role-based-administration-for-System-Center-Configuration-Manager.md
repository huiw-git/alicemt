---
title: "Configure role-based administration for System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 57413dd3-b2f8-4a5f-b27f-8464d357caff
caps.latest.revision: 7
caps.handback.revision: 0
---
# Configure role-based administration for System Center Configuration Manager
In [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)], role-based administration combines security roles, security scopes, and assigned collections to define the administrative scope for each administrative user. An administrative scope includes the objects that an administrative user can view in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, and the tasks related to those objects that the administrative user has permission to perform. Role-based administration configurations are applied at each site in a hierarchy.  
  
 If you're not yet familiar with concepts for role-based administration, see [Fundamentals of role-based administration for System Center Configuration Manager](../System Center Configuration Manager/Fundamentals-of-role-based-administration-for-System-Center-Configuration-Manager.md)  
  
 The information in the following procedures can help you create and configure role-based administration and related security settings.  
  
-   [Create custom security roles](#BKMK_CreateSecRole)  
  
-   [Configure security roles](#BKMK_ConfigSecRole)  
  
-   [Configure security scopes for an object](#BKMK_ConfigSecScope)  
  
-   [Configure collections to manage security](#BKMK_ConfigColl)  
  
-   [Create a new administrative user](#BKMK_Create_AdminUser)  
  
-   [Modify the administrative scope of an administrative user](#BKMK_ModAdminUser)  
  
##  <a name="BKMK_CreateSecRole"></a> Create custom security roles  
 [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides several built-in security roles. If you require additional security roles, you can create a custom security role by creating a copy of an existing security role, and then modifying the copy. You might create a custom security role to grant administrative users the additional security permissions they require that are not included in a currently assigned security role. By using a custom security role, you can grant them only the permissions they require, and avoid assigning a security role that grants more permissions than they require.  
  
 Use the following procedure to create a new security role by using an existing security role as a template.  
  
#### To create custom security roles  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Security**, and then click **Security Roles**.  
  
     Use one of the following processes to create the new security role:  
  
    -   To create a new custom security role, perform the following actions:  
  
        1.  Select an existing security role to use as the source for the new security role.  
  
        2.  On the **Home** tab, in the **Security Role** group, click **Copy**. This creates a copy of the source security role.  
  
        3.  In the Copy Security Role wizard, specify a **Name** for the new custom security role.  
  
        4.  In **Security operation assignments**, expand each **Security Operations** node to display the available actions.  
  
        5.  To change the setting for a security operation, click the down arrow in the **Value** column, and then select either **Yes** or **No**.  
  
            > [!CAUTION]  
            >  When you configure a custom security role, ensure not to grant permissions that are not required by administrative users that are associated with the new security role. For example, the **Modify** value for the **Security Roles** security operation grants administrative users permission to edit any accessible security role, even if they are not associated with that security role.  
  
        6.  After you configure the permissions, click **OK** to save the new security role.  
  
    -   To import a security role that was exported from another [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy, perform the following actions:  
  
        1.  On the **Home** tab, in the **Create** group, click **Import Security Role**.  
  
        2.  Specify the .xml file that contains the security role configuration that you want to import, and click **Open** to complete the procedure and save the security role.  
  
            > [!NOTE]  
            >  After you import a security role, you can edit the security role properties to change the object permissions that are associated with the security role.  
  
##  <a name="BKMK_ConfigSecRole"></a> Configure security roles  
 The groups of security permissions that are defined for a security role are called security operation assignments. Security operation assignments represent a combination of object types and actions that are available for each object type. You can modify which security operations are available for any custom security role, but you cannot modify the built-in security roles that [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides.  
  
 Use the following procedure to modify the security operations for a security role.  
  
#### To modify security roles  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Security**, and then click **Security Roles**.  
  
3.  Select the custom security role that you want to modify.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  Click the **Permissions** tab.  
  
6.  In **Security operation assignments**, expand each **Security Operations** node to display the available actions.  
  
7.  To change the setting for a security operation, click the down arrow in the **Value** column, and then select either **Yes** or **No**.  
  
    > [!CAUTION]  
    >  When you configure a custom security role, ensure not to grant permissions that are not required by administrative users that are associated with the new security role. For example, the **Modify** value for the **Security Roles** security operation grants administrative users permission to edit any accessible security role, even if they are not associated with that security role.  
  
8.  When you have finished configuring security operation assignments, click **OK** to save the new security role.  
  
##  <a name="BKMK_ConfigSecScope"></a> Configure security scopes for an object  
 You manage the association of a security scope for an object from the object and not from the security scope. The only direct configurations that security scopes support are changes to its name and description. To change the name and description of a security scope when you view the security scope properties, you must have the **Modify** permission for the **Security Scopes** securable object.  
  
 When you create a new object in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], the new object is associated with each security scope that is associated with the security roles of the account that is used to create the object when those security roles provide the **Create** permission, or **Set Security Scope** permission. Only after the object is created, can you change the security scopes it is associated with.  
  
 For example, you are assigned a security role that grants you permission to create a new boundary group. When you create a new boundary group, you have no option to which you can assign specific security scopes. Instead, the security scopes available from the security roles you are associated with are automatically assigned to the new boundary group. After you save the new boundary group, you can edit the security scopes associated with the new boundary group.  
  
 Use the following procedure to configure the security scopes assigned to an object.  
  
#### To configure security scopes for an object  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, select an object that supports assignment to a security scope.  
  
2.  On the **Home** tab, in the **Classify** group, click **Set Security Scopes**.  
  
3.  In the **Set Security Scopes** dialog box, select or clear the security scopes that this object is associated with. Each object that supports security scopes must be assigned to at least one security scope.  
  
4.  Click **OK** to save the assigned security scopes.  
  
    > [!NOTE]  
    >  When you create a new object, you can assign the object to multiple security scopes. To modify the number of security scopes associated with the object, you must change this assignment after the object is created.  
  
##  <a name="BKMK_ConfigColl"></a> Configure collections to manage security  
 There are no procedures to configure collections for role-based administration. Collections do not have a role-based administration configuration; instead, you assign collections to an administrative user when you configure the administrative user. The collection security operations that are enabled in the users assigned security roles determine the permissions an administrative user has for collections and collection resources (collection members).  
  
 When an administrative user has permissions to a collection, they also have permissions to collections that are limited to that collection. For example, your organization uses a collection named All Desktops, and there exist a collection named All North America Desktops that is limited to the All Desktops collection. If an administrative user has permissions to All Desktops, they also have those same permissions to the All North America Desktops collection. In addition, an administrative user cannot use the **Delete** or **Modify** permission on collection that is directly assigned to them, but can use these permissions on the collections that are limited to that collection. Using the previous example, the administrative user can delete or modify the All North America Desktops collection, but cannot delete or modify the All Desktops collection.  
  
##  <a name="BKMK_Create_AdminUser"></a> Create a new administrative user  
 To grant individuals or members of a security group access to manage [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)], create an administrative user in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and specify the Windows account of the User or User Group. Each administrative user in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] must be assigned at least one security role and one security scope. You can also assign collections to limit the administrative scope of the administrative user.  
  
 Use the following procedures to create new administrative users.  
  
#### To create a new administrative user  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Security**, and then click **Administrative Users**.  
  
3.  On the **Home** tab, in the **Create** group, click **Add User or Group**.  
  
4.  Click **Browse** and then select the user account or group to use for this new administrative user.  
  
    > [!NOTE]  
    >  For console-based administration, only domain users or security groups can be specified as an administrative user.  
  
5.  For **Associated security roles**, click **Add** to open a list of the available security roles, select the check box for one or more security roles, and then click **OK**.  
  
6.  Select one of the following two options to define the securable object behavior for the new user:  
  
    -   **All securable objects that are relevant to their associated security roles**: This option associates the administrative user with the **All** security scope and the root level, built-in collections for **All Systems**, and **All Users** and User Groups. The security roles assigned to the user define access to objects. New objects that this administrative user creates are assigned to the **Default** security scope.  
  
    -   **Only securable objects in specified security scopes or collections**: By default, this option associates the administrative user with the **Default** security scope and the **All Systems** and **All Users and User Groups** collections. However, the actual security scopes and collections are limited to those that are associated with the account that you used to create the new administrative user. This option supports the addition or removal of security scopes and collections to customize the administrative scope of the administrative user.  
  
    > [!IMPORTANT]  
    >  The preceding options associate each assigned security scope and collection to each security role assigned to the administrative user. A third option, **Only securable objects as determined by the security roles of the administrative user**, can be used to associate individual security roles to specific security scopes and collections. This third option is available after you create the new administrative user, when you modify the administrative user.  
  
7.  Depending on your selection in step 6, take the following action:  
  
    -   If you selected **All securable objects that are relevant to their associated security roles**, click **OK** to complete this procedure.  
  
    -   If you selected **Only securable objects in specified security scopes or collections**, you can click **Add** to select additional collections and security scopes, or select one or more objects in the list, and then click **Remove** to remove them. Click **OK** to complete this procedure.  
  
##  <a name="BKMK_ModAdminUser"></a> Modify the administrative scope of an administrative user  
 You can modify the administrative scope of an administrative user by adding or removing security roles, security scopes, and collections that are associated with the user. Each administrative user must be associated with at least one security role and one security scope. You might have to assign one or more collections to the administrative scope of the user. Most security roles interact with collections and do not function correctly without an assigned collection.  
  
 When you modify an administrative user, you can change the behavior for how securable objects are associated with the assigned security roles. The three behaviors that you can select are as follows:  
  
-   **All securable objects that are relevant to their associated security roles**: This option associates the administrative user with the **All** scope and the root level built-in collections for **All Systems**, and **All Users and User Groups**. The security roles that are assigned to the user define access to objects.  
  
-   **Only securable objects in specified security scopes or collections**: This option associates the administrative user to the same security scopes and collections that are associated to the account you use to configure the administrative user. This option supports the addition or removal of security roles and collections to customize the administrative scope of the administrative user.  
  
-   **Only securable objects as determined by the security roles of the administrative user**: This option lets you create specific associations between individual security roles and specific security scopes and collections for the user.  
  
    > [!NOTE]  
    >  This option is available only when you modify the properties of an administrative user.  
  
 The current configuration for the securable object behavior changes the process that you use to assign additional security roles. Use the following procedures that are based on the different options for securable objects to help you manage an administrative user.  
  
 Use the following procedure to view and manage the configuration for securable objects for an administrative user:  
  
#### To view and manage the securable object behavior for an administrative user  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Security**, and then click **Administrative Users**.  
  
3.  Select the administrative user that you want to modify.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  Click the **Security Scopes** tab to view the current configuration for securable objects for this administrative user.  
  
6.  To modify the securable object behavior, select a new option for securable object behavior. After you change this configuration, reference the appropriate procedure for further guidance to configure security scopes and collections, and security roles for this administrative user.  
  
7.  Click **OK** to complete the procedure.  
  
 Use the following procedure to modify an administrative user that has the securable object behavior set to **All securable objects that are relevant to their associated security roles**:  
  
#### Option: All securable objects that are relevant to their associated security roles  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Security**, and then click **Administrative Users**.  
  
3.  Select the administrative user that you want to modify.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  Click the **Security Scopes** tab to confirm that the administrative user is configured for **All securable objects that are relevant to their associated security roles**.  
  
6.  To modify the assigned security roles, click the **Security Roles** tab.  
  
    -   To assign additional security roles to this administrative user, click **Add**, select the check box for each additional security role that you want to assign, and then click **OK**.  
  
    -   To remove security roles, select one or more security roles from the list, and then click **Remove**.  
  
7.  To modify the securable object behavior, click the **Security Scopes** tab and select a new option for the securable object behavior. After you change this configuration, reference the appropriate procedure for further guidance to configure security scopes and collections, and security roles for this administrative user.  
  
    > [!NOTE]  
    >  When the securable object behavior is set to **All securable objects that are relevant to their associated security roles**, you cannot add or remove specific security scopes and collections.  
  
8.  Click **OK** to complete this procedure.  
  
 Use the following procedure to modify an administrative user that has the securable object behavior set to **Only securable objects in specified security scopes or collections**.  
  
#### Option: Only securable objects in specified security scopes or collections  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Security**, and then click **Administrative Users**.  
  
3.  Select the administrative user that you want to modify.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  Click the **Security Scopes** tab to confirm that the user is configured for **Only securable objects in specified security scopes or collections**.  
  
6.  To modify the assigned security roles, click the **Security Roles** tab.  
  
    -   To assign additional security roles to this user, click **Add**, select the check box for each additional security role that you want to assign, and then click **OK**.  
  
    -   To remove security roles, select one or more security roles from the list, and then click **Remove**.  
  
7.  To modify the security scopes and collections associated with security roles, click the **Security Scopes** tab.  
  
    -   To associate new security scopes or collections with all security roles that are assigned to this administrative user, click **Add** and select one of the four options. If you select **Security Scope** or **Collection**, select the check box for one or more objects to complete that selection, and then click **OK**.  
  
    -   To remove a security scope or collection, select the object, and then click **Remove**.  
  
8.  Click **OK** to complete this procedure.  
  
 Use the following procedure to modify an administrative user that has the securable object behavior set to **Only securable objects as determined by the security roles of the administrative user**.  
  
#### Option: Only securable objects as determined by the security roles of the administrative user  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Security**, and then click **Administrative Users**.  
  
3.  Select the administrative user that you want to modify.  
  
4.  On the **Home** tab, in the **Properties** group, click **Properties**.  
  
5.  Click the **Security Scopes** tab to confirm that the administrative user is configured for **Only securable objects in specified security scopes or collections**.  
  
6.  To modify the assigned security roles, click the **Security Roles** tab.  
  
    -   To assign additional security roles to this administrative user, click **Add**. On the **Add Security Role** dialog box, select one or more available security roles, click **Add**, and select an object type to associate with the selected security roles. If you select **Security Scope** or **Collection**, select the check box for one or more objects to complete that selection, and then click **OK**.  
  
        > [!NOTE]  
        >  You must configure at least one security scope before the selected security roles can be assigned to the administrative user. When you select multiple security roles, each security scope and collection that you configure is associated with each of the selected security roles.  
  
    -   To remove security roles, select one or more security roles from the list, and then click **Remove**.  
  
7.  To modify the security scopes and collections associated with a specific security role, click the **Security Scopes** tab, select the security role, and then click **Edit**.  
  
    -   To associate new objects with this security role, click **Add**, and select an object type to associate with the selected security roles. If you select **Security Scope** or **Collection**, select the check box for one or more objects to complete that selection, and then click **OK**.  
  
        > [!NOTE]  
        >  You must configure at least a one security scope.  
  
    -   To remove a security scope or collection that is associated with this security role, select the object, and then click **Remove**.  
  
    -   When you have finished modifying the associated objects, click **OK**.  
  
8.  Click **OK** to complete this procedure.  
  
    > [!CAUTION]  
    >  When a security role grants administrative users the collection deployment permission, those administrative users can distribute objects from any security scope for which they have object **read** permissions, even if that security scope is associated with a different security role.  
  
## See Also  
 [Configure sites and hierarchies for System Center Configuration Manager](../System Center Configuration Manager/Configure-sites-and-hierarchies-for-System-Center-Configuration-Manager.md)