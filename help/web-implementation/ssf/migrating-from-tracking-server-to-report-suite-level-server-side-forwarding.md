---
title: Migrating from Tracking Server to Report Suite-Level Server-Side Forwarding
seo-title: Migrating from Tracking Server to Report Suite-Level Server-Side Forwarding
description: This article and video will show you how to enable server-side forwarding of Analytics Data to Audience Manager at a report suite level instead of at a tracking server level.
seo-description: This article and video will show you how to enable server-side forwarding of Analytics Data to Audience Manager at a report suite level instead of at a tracking server level.
uuid: 489eaf4f-54e8-4de4-bd3a-3a2f59c0069b
products: SG_ANALYTICS
products: SG_AUDIENCEMANAGER
discoiquuid: 4a3fcbae-5415-4b81-bf7c-973f52e0e57a
targetaudience: target-audience new;target-audience ongoing
index: y
internal: n
snippet: y
---

# Migrating from Tracking Server to Report Suite-Level Server-Side Forwarding {#migrating-from-tracking-server-to-report-suite-level-server-side-forwarding}

This article and video will show you how to enable server-side forwarding of Analytics Data to Audience Manager at a report suite level instead of at a tracking server level.

## Introduction {#introduction}

If you have Adobe Audience Manager AND Adobe Analytics, you can implement “Server-side Forwarding” of the Analytics data to Audience Manager. This means that, instead of your page sending 2 hits (one to Analytics and one to Audience Manager), it can simply send a hit to Analytics, and Analytics will forward that data to Audience Manager. If you already have this up and running, and if you had it enabled/implemented before October 2017, your server-side forwarding might be based on your “Tracking Server”, which had to be enabled by Adobe Customer Care or Adobe Consulting. As of October 2017, you can now configure server-side forwarding yourself, and do it at a Report Suite level (forwarding PER Report Suite). There are significant benefits to this, which will be discussed below.

## Tracking Server Forwarding {#tracking-server-forwarding}

Your tracking server is the location to which you are sending your Analytics data, and also the domain at which the image request and cookie is written. It should be set in DTM or Launch by Adobe, or in the AppMeasurement.js file, and will typically look like this, with your site or business name replacing “mysite”:

`s.trackingServer = "mysite.sc.omtrdc.net";`

If server-side forwarding is set up to forward at the tracking server level, any hit that is being sent to this tracking server (IF the Experience Cloud ID Service is also enabled) will be forwarded to Audience Manager. This had to be enabled by Adobe Customer Care or Adobe Consulting. They are also the ones who can disable it, AFTER you have switched over to report suite forwarding, as described below.

If you are unsure if tracking server forwarding is enabled for you, contact Adobe Customer Care or Adobe Consulting, and they should be able to let you know.

## Report Suite-Level Server-Side Forwarding {#report-suite-level-server-side-forwarding}

One of the biggest benefits to moving to report suite forwarding from tracking server forwarding is that you will now be able to use “Audience Analytics”, which is the ability to forward Audience Manager segments back into Adobe Analytics for detailed segment analysis. This great feature is NOT supported if you are still on tracking server forwarding and not report suite forwarding. See more information about Audience Analytics in the [documentation](https://marketing.adobe.com/resources/help/en_US/analytics/audiences/).

>[!VIDEO](https://video.tv.adobe.com/v/23701/?quality=12)

## Important Tip {#additional-resources}

As stated in the video above, once you have all of the report suites set to forward that you want to forward to Audience Manager, you should contact Adobe Customer Care or Adobe Consulting and have them disable the tracking server forwarding. It is not an emergency for you to do this, because having both tracking server forwarding and report suite forwarding will NOT result in duplicate hits. However, it is best practice to only have report suite forwarding on. If you leave tracking server forwarding on, not only might it forward data from report suites that you do not want forwarded, but in the future, after you (and everyone at your company) has forgotten that tracking server forwarding is on, you might think that data is not forwarding for a specific report suite (because it is not turned on at the report suite level), but the data is still being forwarded anyway because of the tracking server. Then you will waste time and money figuring out why it is forwarding and also paying for AAM server calls that you didn’t expect. So it’s just a good idea to disable tracking server forwarding as soon as you have all of the report suites set to forward that make sense for your business needs.