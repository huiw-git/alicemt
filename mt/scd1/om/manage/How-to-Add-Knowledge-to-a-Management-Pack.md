---
title: How to Add Knowledge to a Management Pack
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c3e73e3a-fe17-4fd4-8c8e-401b02f8dc35
---
# How to Add Knowledge to a Management Pack
[!INCLUDE[om12long](../../om/manage/includes/om12long_md.md)] management packs include knowledge for rules, monitors, and alerts that helps you identify problems, causes, and resolutions.  
  
Knowledge is referred to as *product knowledge* or *company knowledge*. Product knowledge is embedded in a rule or monitor when it is authored. Company knowledge is added by management group administrators to expand the troubleshooting information and provide company\-specific information for operators. Administrators can use company knowledge to document any overrides implemented for a monitor or rule, along with the explanation for the customization and any other information that might be useful.  
  
Operations Manager stores company knowledge in a management pack. Sealed management packs cannot be modified, so Operations Manager saves customizations such as company knowledge in a custom management pack. By default, Operations Manager saves all customizations to the Default Management Pack. As a best practice, you should instead create a separate management pack for each sealed management pack you want to customize.  
  
> [!TIP]  
> To avoid losing your company knowledge, be sure to back up management packs as part of your general backup routine.  
  
To add or edit company knowledge, the computer must meet the following software requirements:  
  
-   The Operations console must be installed on a 32\-bit computer. Adding and editing company knowledge must be done on this computer.  
  
-   Microsoft Office Word 2003 with the .NET Programmability feature, or Microsoft Office Word 2007 or Office Word 2010 Professional edition \(Standard edition is not supported\)  
  
    > [!NOTE]  
    > Only the 32\-bit version of Word 2010 is supported. The knowledge template will not work with the 64\-bit version of Word 2010.  
  
-   Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime at [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=74969](http://go.microsoft.com/fwlink/?LinkId=74969). You must use this version of the Visual Studio 2005 Tools for Office.  
  
To add or edit company knowledge, you must have the Author or Administrator user role.  
  
### To edit company knowledge  
  
1.  Log on to the computer with an account that is a member of the Operations Manager Author or Administrator role.  
  
2.  Click **Authoring**.  
  
3.  Locate the monitor or rule to be documented.  
  
4.  Click **Properties** under **Actions**, or right\-click the monitor name and select **Properties** from the shortcut menu.  
  
5.  Click the **Company Knowledge** tab.  
  
6.  In the **Management pack** section, select a management pack in which to save the company knowledge.  
  
7.  Click **Edit** to launch Microsoft Office Word.  
  
8.  Add or edit text as desired.  
  
    The company knowledge tab displays only the sections of the Word document with custom text.  
  
9. On the **File** menu, click **Save** to save your changes.  
  
    > [!IMPORTANT]  
    > Do not close Word.  
  
10. Return to the company knowledge tab and click **Save**, and then click **Close**. This will close both the properties dialog box and Word.  
  
## See Also  
[Creating a Management Pack for Overrides](../../om/manage/Creating-a-Management-Pack-for-Overrides.md)  
[Management Packs Installed with Operations Manager](../../om/manage/Management-Packs-Installed-with-Operations-Manager.md)  
[What Is in an Operations Manager Management Pack?](../../om/manage/What-Is-in-an-Operations-Manager-Management-Pack-.md)  
[Management Pack Life Cycle](../../om/manage/Management-Pack-Life-Cycle.md)  
[How to Import an Operations Manager Management Pack](../../om/manage/How-to-Import-an-Operations-Manager-Management-Pack.md)  
[How to Remove an Operations Manager Management Pack](../../om/manage/How-to-Remove-an-Operations-Manager-Management-Pack.md)  
[How to Export an Operations Manager Management Pack](../../om/manage/How-to-Export-an-Operations-Manager-Management-Pack.md)  
  
