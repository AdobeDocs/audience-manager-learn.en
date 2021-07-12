---
title: Migrating from Tracking Server to Report Suite-Level Server-Side Forwarding
description: This article and video will show you how to enable server-side forwarding of Analytics Data to Audience Manager at a report suite level instead of at a tracking server level.
product: audience manager
feature: Adobe Analytics Integration
topics: 
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 1776
role: Developer, Data Engineer
level: Intermediate
exl-id: 08b81e52-a28a-43e4-a284-df2460a43016
---
# Migrating from [!UICONTROL Tracking Server] to [!UICONTROL Report Suite]-Level [!UICONTROL Server-Side Forwarding] {#migrating-from-tracking-server-to-report-suite-level-server-side-forwarding}

This article and video will show you how to enable [!UICONTROL server-side forwarding] of [!DNL Analytics] Data to Audience Manager at a [!UICONTROL report suite] level instead of at a [!UICONTROL tracking server] level.

## Introduction {#introduction}

If you have Adobe Audience Manager AND Adobe Analytics, you can implement “[!UICONTROL Server-side Forwarding]” of the [!DNL Analytics] data to Audience Manager. This means that, instead of your page sending 2 hits (one to [!DNL Analytics] and one to Audience Manager), it can simply send a hit to [!DNL Analytics], and [!DNL Analytics] will forward that data to Audience Manager. If you already have this up and running, and if you had it enabled/implemented before October 2017, your [!UICONTROL server-side forwarding] might be based on your “[!UICONTROL Tracking Server]”, which had to be enabled by Adobe Customer Care or Adobe Consulting. As of October 2017, you can now configure [!UICONTROL server-side forwarding] yourself, and do it at a [!UICONTROL Report Suite] level (forwarding PER [!UICONTROL Report Suite]). There are significant benefits to this, which will be discussed below.

## [!UICONTROL Tracking Server] Forwarding {#tracking-server-forwarding}

Your [!UICONTROL tracking server] is the location to which you are sending your [!DNL Analytics] data, and also the domain at which the image request and cookie is written. It should be set in DTM or [!DNL Experience Platform Launch], or in the [!DNL AppMeasurement.js] file, and will typically look like this, with your site or business name replacing “mysite”:

`s.trackingServer = "mysite.sc.omtrdc.net";`

If [!UICONTROL server-side forwarding] is set up to forward at the [!UICONTROL tracking server] level, any hit that is being sent to this [!UICONTROL tracking server] (IF the Experience Cloud ID Service is also enabled) will be forwarded to Audience Manager. This had to be enabled by Adobe Customer Care or Adobe Consulting. They are also the ones who can disable it, AFTER you have switched over to [!UICONTROL report suite] forwarding, as described below.

If you are unsure if [!DNL tracking server forwarding] is enabled for you, contact Adobe Customer Care or Adobe Consulting, and they should be able to let you know.

## [!UICONTROL Report Suite]-Level [!UICONTROL Server-Side Forwarding] {#report-suite-level-server-side-forwarding}

One of the biggest benefits to moving to [!UICONTROL report suite] forwarding from [!UICONTROL tracking server] forwarding is that you will now be able to use “Audience Analytics”, which is the ability to forward Audience Manager [!UICONTROL segments] back into Adobe Analytics for detailed [!UICONTROL segment] analysis. This great feature is NOT supported if you are still on [!UICONTROL tracking server] forwarding and not [!UICONTROL report suite] forwarding. See more information about Audience Analytics in the [documentation](https://marketing.adobe.com/resources/help/en_US/analytics/audiences/).

>[!VIDEO](https://video.tv.adobe.com/v/23701/?quality=12)

## Important Tip {#additional-resources}

As stated in the video above, once you have all of the [!UICONTROL report suites] set to forward that you want to forward to Audience Manager, you should contact Adobe Customer Care or Adobe Consulting and have them disable the [!UICONTROL tracking server] forwarding. It is not an emergency for you to do this, because having both [!UICONTROL tracking server] forwarding and [!UICONTROL report suite] forwarding will NOT result in duplicate hits. However, it is best practice to only have [!UICONTROL report suite] forwarding on. If you leave [!UICONTROL tracking server] forwarding on, not only might it forward data from [!UICONTROL report suites] that you do not want forwarded, but in the future, after you (and everyone at your company) has forgotten that [!UICONTROL tracking server] forwarding is on, you might think that data is not forwarding for a specific [!UICONTROL report suite] (because it is not turned on at the report suite level), but the data is still being forwarded anyway because of the [!UICONTROL tracking server]. Then you will waste time and money figuring out why it is forwarding and also paying for AAM server calls that you didn’t expect. So it’s just a good idea to disable [!UICONTROL tracking server] forwarding as soon as you have all of the [!UICONTROL report suites] set to forward that make sense for your business needs.
