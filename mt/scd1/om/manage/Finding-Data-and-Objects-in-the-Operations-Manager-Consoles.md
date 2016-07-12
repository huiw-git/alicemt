---
title: Finding Data and Objects in the Operations Manager Consoles
ms.custom: na
ms.prod: system-center-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - operations-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d47793da-7d78-4794-b471-8dca0673d88e
manager:cfreeman
---
# Finding Data and Objects in the Operations Manager Consoles
[!INCLUDE[om12long](../../om/manage/includes/om12long_md.md)], with the appropriate management packs imported, will provide you with a comprehensive view of what is going on with your monitored applications, hardware, and processes. This can result in a very large volume of data being displayed in the Operations console. Learning how to quickly locate the data you need is essential to efficient interaction with the console. You can use the **Scope**, **Find**, and **Search** buttons on the Operations console toolbar to filter your view of monitoring data so that you can find the exact monitoring object or group of objects that you need. You can also filter your data based on the number of hours or days you would like to show.  
  
> [!NOTE]  
> Any time that you do not see the information you expect in the results pane, check the scope and time filters to ensure that the correct objects and time period are set for the results you need.  
  
The **Scope**, **Search**, **Find**, and **Time** tools apply a temporary filter to the data you are viewing in the console. While you can locate a specific object using Search or Find, you can also use Scope or Time to display a set of objects that meet a set of criteria. The following table shows the differences between the different filtering options.  
  
|Filter|When to use|For more information, see|  
|----------|---------------|-----------------------------|  
|Scope|Use to limit the data in a view to only those objects that meet your criteria. This scope remains in place until you clear it.|-   [How to Change Scope](../../om/manage/Finding-Data-and-Objects-in-the-Operations-Manager-Consoles.md#bkmk_howtochangescope)<br />-   [Define a Scope Using Operations Manager Groups](../../om/manage/Define-a-Scope-Using-Operations-Manager-Groups.md)|  
|Search|Use to display a list of objects that meet your criteria. You can then act on those objects; however, when you navigate away from this list, the filter is removed, and any view will show all objects \(not just those from your search criteria\).|-   [How to Use Find and Search](../../om/manage/Finding-Data-and-Objects-in-the-Operations-Manager-Consoles.md#bkmk_howtousefindandsearch)<br />-   [Using Advanced Search](../../om/manage/Using-Advanced-Search.md)<br />-   [Examples of Using Advanced Search in Operations Manager](../../om/manage/Examples-of-Using-Advanced-Search-in-Operations-Manager.md)|  
|Find|Use to display a known single object.|[How to Use Find and Search](../../om/manage/Finding-Data-and-Objects-in-the-Operations-Manager-Consoles.md#bkmk_howtousefindandsearch)|  
|Time|Use to limit the data displayed to only that data \(such as alerts\) that has been generated within a defined time frame.|[How to Change the Time Criteria](../../om/manage/Finding-Data-and-Objects-in-the-Operations-Manager-Consoles.md#bkmk_howtochangethetimecriteria)|  
  
## <a name="bkmk_howtochangescope"></a>How to Change Scope  
Changing the scope of the monitoring view enables you to view only those objects that meet a certain criteria, such as management servers. For example, if you want to view only those computers in your environment that are running Windows XP, you can apply a scope that uses “Windows XP” as the criteria; no other computers are displayed.  
  
#### To change the scope of the monitoring view  
  
1.  In the Operations console, click **Monitoring** to display the objects in your monitoring environment.  
  
2.  Click the **Scope** button on the Operations Manager toolbar. If this button is not available, check to make sure that you have an object, not a folder, selected in the Monitoring pane. The **Change View Scope** dialog box displays a list of existing groups and distributed applications.  
  
    ![Dialog box to change scope](../../om/manage/media/Scoping.gif "Scoping")  
  
3.  If the list is too long, you can find a specific group or distributed application by entering a word or phrase in the **Look for** field. After you make a selection, click **OK**. Now only the objects that meet the scope criteria are shown in the Results pane.  
  
## <a name="bkmk_howtousefindandsearch"></a>How to Use Find and Search  
Use the **Find** button when the list of objects in the Results pane is too long to quickly pick out a particular object. Use the **Search** button when you want to find all objects that meet a certain criteria.  
  
#### To use Find to locate an object within a list  
  
1.  In the Operations console, click **Monitoring**.  
  
2.  Select a view that is available in the Monitoring workspace. This displays a list of objects in the Results pane.  
  
3.  Check to see whether a **Look for** box is at the top of the Results pane. If there is no **Look for** box, click the **Find** button on the toolbar. In **Look for**, type a word, such as the name of an object, that you want to find in the list, and then click **Find**.  
  
    The object that you are looking for is displayed.  
  
4.  Click **Clear** to go back to the original list of objects.  
  
#### To use Search to create a list of objects  
  
1.  In the Operations console, click **Monitoring**.  
  
2.  Click the **Search** button on the toolbar.  
  
3.  In the **Search** window, type the word or phrase that describes the set of objects you want to find. A list of objects that meet your criteria is displayed. The list is sorted by object type.  
  
## <a name="bkmk_howtochangethetimecriteria"></a>How to Change the Time Criteria  
Changing the time criteria of the monitoring view enables you to view only those objects that meet a certain criteria, such as **Last 12 hours**. When you change the time criteria, you limit the display to only that time period. For example, if you want to view the last week of data, you can change the time criteria to **Last 1 week**.  
  
You can filter your view to the following time periods:  
  
-   Last 1 hour  
  
-   Last 2 hours  
  
-   Last 4 hours  
  
-   Last 8 hours  
  
-   Last 12 hours  
  
-   Last 1 day  
  
-   Last 2 days  
  
-   Last 3 days  
  
-   Last 4 days  
  
-   Last 5 days  
  
-   Last 6 days  
  
-   Last 1 week  
  
-   Last 2 weeks  
  
-   Last 3 weeks  
  
-   Last 1 month  
  
-   All  
  
#### To change the time criteria  
  
1.  In the Operations console, click **Monitoring** to display the objects in your monitoring environment.  
  
2.  Click the **Calendar** button on the toolbar. If this button is not available, check to make sure that you have an object, not a folder, selected in the navigation pane.  
  
3.  Select the time criteria you are interested in.  
  
    Now only the objects that meet the time criteria are shown in the Results pane.  
  
