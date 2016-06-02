---
title: Pin Reporting Services items to Power BI Dashboards
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d96c3f7-2fd4-40f7-8d1c-14a7f54cdb15
---
# Pin Reporting Services items to Power BI Dashboards
  [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] enables users to pin [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report items from the report viewer toolbar to a [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] dashboard as a new tile.   To pin, your administrator needs to first integrate your report server with Azure Active Directory and [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)].  
  
 ![rs_powerbi_icon](../../Images\Image\ImageNotContaina/ssrs_powerbi_icon.png "ssrs_powerbi_icon")  
  
 [!INCLUDE[applies](../../Token\Other/applies_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native Mode
  
##  <a name="bkmk_requirements_to_pin"></a> Requirements to Pin  
  
-   The report server is configured for [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] integration. For more information, see [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md). If the report server has not been configured, you will not see the **Pin to Power BI Dashboard** button the toolbar.  
  
     ![ssRS_Report_PowerBI](../../Images\Image\ImageNotContaina/ssRS_Report_PowerBI.png)  
  
-   You pin from the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report viewer in t[!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)]he , for example http:\/\/myserver\/Reports.  You cannot pin from [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)], from report designer in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], or from a report server url.  For example  http:\/\/myserver\/Report`Server`.  
  
-   Your browser needs to be configured to allow pop\-ups from your report server site.  
  
-   Reports need to be configured for stored credentials if you want the pinned item to refresh.  When you pin an item, a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscription is automatically created to manage the data refresh of the item to the dashboard.  If the report does not use stored credentials, the when the  subscription runs, you will see an error message similar to  the following on the **My subscriptions** page.  
  
        PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credential.
 
    See the section "Configure stored credentials for a report\-specific data source \(Native mode\)" in [Store Credentials in a Reporting Services Data Source](../../Topics\TopicNameContainA/Store-Credentials-in-a-Reporting-Services-Data-Source.md)  
  
##  <a name="bkmk_supported_items"></a> Items You Can Pin  
 The following report items can be pinned to a [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] dashboard.  You cannot pin items that are nested inside a data region. For example you cannot pin an item that is nested inside a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] table or list.  
  
-   Charts  
  
-   Gauge panels  
  
-   Maps  
  
-   Images  
  
-   Items need to be in the report body.  You cannot pin items that are in the page header or page footer.  
  
-   You can pin individual items that are inside a top level rectangle but you cannot pin them all as a single group.  
  
##  <a name="bkmk_to_pin"></a> To Pin a Report Item  
  
-   Verify you  are signed into [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)]. In the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] [!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)], click the menu item **My Settings** and sign in. See  [My Settings for Power BI Integration &#40;web portal&#41;](assetId:///85c2fac7-80bf-45b7-8654-764b5f5231f5) for more information.  
  
     ![ssRS_WebPortal_MySettings](../../Images\Image\ImageNotContaina/ssRS_WebPortal_MySettings.png)  
  
-   Navigate to the [!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)] folder  that contains your report, and then view the report.  
  
-   While viewing the report, click the **Pin to Power BI** button the toolbar.  You will be prompted to sign in, if you are not already signed in.  If the [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] button is not visible, the report server has not been integrated with [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)]. For more information, see [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md).  
  
     ![ssRS_Report_PowerBI](../../Images\Image\ImageNotContaina/ssRS_Report_PowerBI.png)  
  
-   Click the report item you want to pin to [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)]. You can only pin one item at a time.  The report viewer presents a shaded view of your report and the report items you can pin are highlighted while the items that you cannot pin, will be shaded dark.  
  
-   **\(1\)** select the group that contains the dashboard you want to pin to, **\(2\)** select the dashboard you want to pin the item too and **\(3\)** select how frequently you want the tile updated in the dashboard.   ![note](../../Images\Image\ImageNotContaina/ssrs_fyi_note.png "ssrs_fyi_note") The refresh is managed by  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscriptions and after the item is pinned, you can edit the subscription and configure a different  refresh schedule.  
  
     ![ssRS_Pin_to_PowerBI](../../Images\Image\ImageNotContaina/ssRS_Pin_to_PowerBI.png)  
  
-   Click **Pin**  
  
     In the **Pin Successful** dialog, you can click the link **See it in Power BI** to navigate to the dashboard and see the item you just pinned.  
  
-   Click **Close** to return the report to the normal view.  
  
##  <a name="bkmk_in_the_dashboard"></a> In the Dashboard.  
 After your report item is pinned  in the dashboard, the tile looks like other dashboard tiles and there is no visible indication the tile came from [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. The following list summarizes how tile properties are populated from the report item.  
  
||  
|-|  
|From the [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] dashboard the pinned report item behaves like other tiles:<br /><br /> **\(1\)** You can pin the tile to other dashboards.<br /><br /> **\(2\)**In the **Tile Details** you will notice the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report title is used for the default title of the tile .<br /><br /> **\(2\)** The tile subtitle is based on the date and time the tile was pinned or the data was last refreshed from [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. The refresh schedule is managed by the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscription that was automatically created when you pinned the report item.<br /><br /> **\(4\)** If you click the tile itself, [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] uses the **\(3\) custom link** to navigate to the [!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)] page of the registered report server. the link was set when the item was pinned from [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. If you do not have internet connectivity to the report server, you will see an error in the browser.|  
|![ssrs_pinned_tile_details](../../Images\Image\ImageNotContaina/ssrs_pinned_tile_details.png "ssrs_pinned_tile_details")|  
  
##  <a name="bkmk-troubleshoot"></a> Troubleshoot Issues  
  
-   **No [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] button on the report viewer toolbar:**  This indicates the report server has not been integrated with [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)]. For more information, see [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md).  
  
-   **Cannot Pin**: When you attempt to pin an item, you see the following error message: See the section [Items You Can Pin](#bkmk_supported_items).  
  
    -   Cannot Pin: There are no report items on this page that you can pin to [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)].  
  
-   **Pinned items show stale data** in a [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] dashboard and it did update for a period of time.  The user credentials token has expired and you need to sign in again.  The user credential registration with Azure and [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] is good for 90 days. In t[!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)]he , click **My Settings**. For more information, see [My Settings for Power BI Integration &#40;web portal&#41;](assetId:///85c2fac7-80bf-45b7-8654-764b5f5231f5).  
  
     ![ssRS_Report_PowerBI](../../Images\Image\ImageNotContaina/ssRS_Report_PowerBI.png)  
  
-   **Pinned items show stale data** in a [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] dashboard and it has not refreshed even once.  The issue is the report is not configured to use stored credentials. A report must used stored credentials because the action of pinning a report item creates a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscription to manage the refresh schedule of the tiles. [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] subscriptions require stored credentials. If you review  the **My Subscriptions** page, you see an error message similar to the following:  
  
    -   PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The current action cannot be completed. The user data source credentials do not meet the requirements to run this report or shared dataset. Either the user data source credentials are not sto...  
  
-   **Expired Power BI credentials:**  You attempt to pin an item and see the following error message. In the [!INCLUDE[ssRSWebPortal](../../Token\Other/ssRSWebPortal.md)], click **My Settings** and on the My Settings  page, click **Sign in**. See  [My Settings for Power BI Integration &#40;web portal&#41;](assetId:///85c2fac7-80bf-45b7-8654-764b5f5231f5) for more information.  
  
    -   **Cannot Pin** Unexpected Server Error: Missing, invalid or expired Power BI credentials.  
  
     ![ssRS_Report_PowerBI](../../Images\Image\ImageNotContaina/ssRS_Report_PowerBI.png)  
  
-   **Cannot Pin**: If you attempt to pin an item to a dashboard that is in a read\-only state, you will see an error message similar to the following:  
  
    -   Server Error : The item 'Dashboard deleted 015cf022\-8e2f\-462e\-88e5\-75ab0a04c4d0' cannot be found. \(rsItemNotFound\)  
  
##  <a name="bkmk_subscription_management"></a> Subscription Management  
 In addition to the subscription related issues described in the troubleshooting section, the following information will help you maintain [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] related subscriptions.  
  
 Creating the  
  
-   **Item name changed:** If a pinned report item is renamed or deleted, the [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)] tile will no longer update and you will see an error message similar to the following.  If you rename the item back the original name, the subscription will start working again and the tile will be refreshed on the subscriptions schedule.  
  
    -   PowerBI Delivery error: dashboard: SSRS items, visual: Image1, error: Error: Report item 'Image1' cannot be found.  
  
     You could also edit the subscription properties and change the **Report Visual Name** to the appropriate report item name. ![change the visual used for the power bi refresh](../../Images\Image\ImageNotContaina/ssrs_powerbi_subscription_visual.png "ssrs_powerbi_subscription_visual")  
  
-   **Delete a tile**. If you delete a tile in [!INCLUDE[sspowerbi](../../Token\Other/sspowerbi_md.md)], the associated subscription is not deleted in [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] and on the **My subscriptions**page, you see an error similar to the following. You can delete the subscription.  
  
    -   PowerBI Delivery error: dashboard: SSRS items, visual: Image3, error: The item 'Tile deleted af7131d9\-5eaf\-480f\-ba45\-943a07d19c9f' cannot be found.  

## Video

<iframe width="560" height="315" src="https://www.youtube.com/embed/QhPQObqmMPc" frameborder="0" allowfullscreen></iframe>

## See Also  
 [Power BI Report Server Integration &#40;Configuration Manager&#41;](../Topic/Power%20BI%20Report%20Server%20Integration%20\(Configuration%20Manager\).md)   
 [My Settings for Power BI Integration &#40;web portal&#41;](assetId:///85c2fac7-80bf-45b7-8654-764b5f5231f5)  
 [Dashboards in Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
  
  