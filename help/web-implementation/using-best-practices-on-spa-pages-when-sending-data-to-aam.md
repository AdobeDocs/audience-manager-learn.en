---
title: Use best practices on SPA pages when sending data to AAM
description: Learn best practices for sending data from single-page applications (SPA) to Adobe Audience Manager (AAM). This article focuses on using Experience Platform tags, the recommended implementation method.
feature: Implementation Basics
topics: spa
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1390
topic: SPA
role: Developer, Data Engineer
level: Experienced
exl-id: 99ec723a-dd56-4355-a29f-bd6d2356b402
---
# Use best practices on SPA pages when sending data to AAM {#using-best-practices-on-spa-pages-when-sending-data-to-aam}

This document describes several best practices for sending data from single-page applications (SPA) to Adobe Audience Manager (AAM). This article focuses on using [!UICONTROL Experience Platform tags], the recommended implementation method.

## Initial notes

* The items below are going to assume that you are using Platform tags to implement on your site. The considerations still exist if you are not using Platform tags, but you would need to adapt them to your implementation method.
* All SPAs are different, so you might need to tweak some of the following items to best meet your requirements, but Adobe wants to share some best practices that you need to think about as you are sending data from SPA pages to Audience Manager.

## Simple diagram of working with SPAs and AAM in Experience Platform tags (formerly, Launch){#simple-diagram-of-working-with-spas-and-aam-in-experience-platform-launch}

![spa for aam in tags](assets/spa_for_aam_in_launch.png)

>[!NOTE]
>As stated, this is a simplified diagram of how SPA pages are handled in an Adobe Audience Manager implementation (without Adobe Analytics) using Platform tags. As you can see, it is fairly straight-forward, with the big decision being how you are going to communicate a view change (or an action) to Platform tags.

## Triggering tags from the SPA page {#triggering-launch-from-the-spa-page}

Two of the more common methods for triggering a rule in Platform tags (and therefore sending data into Audience Manager), are:

* Setting JavaScript custom events (see example [HERE](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html) with Adobe Analytics)
* Using a [!UICONTROL Direct Call Rule]

In this Audience Manager example, you use a [!UICONTROL Direct Call rule] in Platform tags to trigger the hit going into Audience Manager. As you’ll see in the next sections, this becomes useful by setting the [!UICONTROL Data Layer] to a new value, so that it can be picked up by the [!UICONTROL Data Element] in Platform tags.

## Demo page {#demo-page}

Here is a small page that demonstrates changing a value in the data layer and sending it into Audience Manager, as you may do on a SPA page. This functionality can be modeled for more elaborate changes needed. You can find this demo page [HERE](https://aam.enablementadobe.com/SPA-Launch.html).

## Setting the data layer {#setting-the-data-layer}

As mentioned, when new content is loaded on the page or when someone performs an action on the site, the data layer needs to be set dynamically in the head of the page BEFORE Platform tags are called and runs the [!UICONTROL rules], so that Platform tags can pick up the new values from the data layer and push them into Audience Manager.

If you go to the demo site listed above and look at the page source, you will see:

* The data layer is in the head of the page, before the call to Platform tags
* The JavaScript in the simulated SPA link changes the [!UICONTROL Data Layer], then calls Platform tags (the `_satellite.track()` call). If you were using JavaScript custom events instead of this [!UICONTROL Direct Call Rule], the lesson is the same. First change the [!DNL data layer], and then call Platform tags.

>[!VIDEO](https://video.tv.adobe.com/v/23322/?quality=12)

## Additional resources {#additional-resources}

* [SPA discussion on the Adobe forums](https://forums.adobe.com/thread/2451022)
* [Reference Architecture sites to show how to implement SPA in Platform tags](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-SPA-tutorial-implement.html)
* [Using best practices when tracking SPA in Adobe Analytics](https://helpx.adobe.com/analytics/kt/using/spa-analytics-best-practices-feature-video-use.html)
* [Demo site used for this article](https://aam.enablementadobe.com/SPA-Launch.html)
