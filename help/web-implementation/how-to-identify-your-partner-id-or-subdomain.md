---
title: How to identify your partner ID or subdomain
description: Learn how to identify your partner ID or subdomain when implementing some Experience Cloud features, and about two places you can get this ID in the Audience Manager UI.
feature: Implementation Basics
topics: 
activity: implement
doc-type: technical video
team: Technical Marketing
kt: 2359
role: Developer, Data Engineer
level: Intermediate
exl-id: d3f4a12d-acc5-47b7-a38a-a6a14152bf3a
---
# How to identify your Audience Manager Subdomain {#how-to-identify-your-audience-manager-partner-id-or-subdomain}

When implementing some Experience Cloud features, you need to know what your Audience Manager `Subdomain` is (also sometimes referred to as your `client ID` or `Partner ID`). In this video, we will show you two places you can get this info in the Audience Manager UI.

## Giving away the ending… {#giving-away-the-ending}

In case you would rather just jump in and find it without watching this short video, you can find your `Partner Subdomain` in two places in the UI:

1. If you have already created a [!UICONTROL rule-based] trait, click **[!UICONTROL Get Trait URL]**
    [!UICONTROL Get Trait URL] is next to the trait in the list of traits in that folder, and the URL will include your subdomain in the URL.
1. If you go into the **[!UICONTROL Tools]** > **[!UICONTROL Tags]** interface and click **[!UICONTROL Get code]** for your container, the subdomain is toward the end of the Akamai line

If you can’t quickly find it with those quick references, the video is a short time commitment. :)

>[!VIDEO](https://video.tv.adobe.com/v/25922/?quality=12)

>[!IMPORTANT]
>
>There is a numeric ID assigned to each customer of the Adobe Experience Cloud, and this is often referred to as the "PID", or Partner ID. This is not the ID we are talking about in this article and video. Instead, the "partner subdomain", which is sometimes referred to as the partner ID, is usually a version of the client name, and is the subdomain of the server to which the data is sent. For example, if your company is "Bob's Knobs" (all things doorknobs, of course, haha), then it is likely that your partner subdomain would be "bobsknobs", whereas the "PID" would be something more like "12345". You don't typically need to know your PID, but your subdomain is important to know, so that you can configure your Audience Manager implementation.
>
