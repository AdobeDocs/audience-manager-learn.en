---
title: Migrate your site's Audience Manager implementation from client-side DIL to server-side forwarding
description: Learn how to migrate your site's Audience Manager (AAM) implementation from client-side DIL to server-side forwarding. This tutorial applies if you have both AAM and Adobe Analytics, and you send hits from the page to AAM using DIL (Data Integration Library) code, and you also send hits from the page to Adobe Analytics.
product: audience manager
feature: Adobe Analytics Integration
topics: 
activity: implement
doc-type: tutorial
team: Technical Marketing
kt: 1778
role: Developer, Data Engineer
level: Intermediate
exl-id: bcb968fb-4290-4f10-b1bb-e9f41f182115
---
# Migrate your site's Audience Manager implementation from client-side DIL to server-side forwarding {#migrating-your-site-s-aam-implementation-from-client-side-dil-to-server-side-forwarding}

This tutorial applies to you if you have both Adobe Audience Manager (AAM) and Adobe Analytics, and you are currently sending a hit from the page to AAM using DIL ([!DNL Data Integration Library]) code, and also sending a hit from the page to Adobe Analytics. Since you have both of these solutions, and since they are both part of the Adobe Experience Cloud, you have the opportunity to follow the best practice of turning on server-side forwarding, which enables the [!DNL Analytics] data collection servers to forward site analytics data in real time to Audience Manager, instead of having client-side code send an additional hit from the page to AAM. This tutorial walks you through the steps of making the switch from the older client-side DIL implementation to the newer server-side forwarding method.

## Client-side (DIL) vs. server-side {#client-side-dil-vs-server-side}

When comparing and contrasting these two methods of getting Adobe Analytics data into AAM, it might first be helpful to visualize the differences in the following image:

![client-side to server-side](assets/client-side_vs_server-side_aam_implementation.png)

### Client-side DIL implementation {#client-side-dil-implementation}

If you use this method to get Adobe Analytics data into AAM, you have two hits coming from your Web pages: One going to [!DNL Analytics], and one going to AAM (after having copied the [!DNL Analytics] data on the Web page. [!UICONTROL Segments] are returned from AAM to the page, where they can be used for personalization, and so on. This is considered a legacy implementation and is no longer recommended.

Beyond the fact that this is not following best practices, the disadvantages of using this method include:

* Two hits coming from the page instead of just one
* server-side forwarding is required for real-time sharing of AAM audiences to [!DNL Analytics], so client-side implementations do not allow for this feature (and potentially other features in the future)

It is recommended that you move to a server-side forwarding method of AAM implementation.

### Server-side forwarding implementation {#server-side-forwarding-implementation}

As shown in the image above, a hit comes from the Web page to Adobe Analytics. [!DNL Analytics] then forwards that data to AAM in real time, and visitors are evaluated into AAM [!UICONTROL traits] and [!UICONTROL segments], just as if the hit had come directly from the page.

[!UICONTROL Segments] are returned on the same real-time hit back to [!DNL Analytics], which forwards the response on to the Web page for personalization, and so on.

There is no timing downside to moving to Server-Side Forwarding. Adobe highly recommends that anyone who has both Audience Manager and [!DNL Analytics] uses this implementation method.

## You have two main tasks {#you-have-two-main-tasks}

There is quite a bit of info on this page, and it is all important, of course. However, it **all boils down to two main things that you need to do**:

1. Change your code from client-side DIL code to server-side forwarding code
1. Flip the switch in the [!DNL Analytics] [!DNL Admin Console] to start the actual forwarding of data (per [!UICONTROL report suite])

If you skip either of these tasks, server-side forwarding will not work correctly. Steps and additional data have been added to this document to help you do these two steps correctly for your setup.

## Implementation options {#implementation-options}

As you move from client-side to server-side forwarding, one of the tasks you will have is changing the code to the new server-side forwarding code. This is done using one of the following options:

* Adobe Experience Platform tags - Adobe's recommended implementation option for Web properties. You’ll see that this is an easy task, as Platform tags has done all of the hard work for you.
* On the page - You can also place the new SSF code directly into the `doPlugins` function inside of your `appMeasurement.js` file, if you are not (yet) using Adobe Launch
* Other tag managers - These can be treated just like the previous (On the page) option, as you will still put the SSF code in `doPlugins`, wherever the other tag manager is storing the [!DNL AppMeasurement] code

We’ll look at each of these below in the _Updating the code_ section.

## Implementation steps {#implementation-steps}

The following steps describe the implementation.

### Step 0: Prerequisite: Experience Cloud ID Service (ECID) {#step-prerequisite-experience-cloud-id-service-ecid}

The main prerequisite for moving to server-side forwarding is to have the Experience Cloud ID Service implemented. This is most easily done if you are using Experience Platform Launch, in which case you simply install the ECID extension and it will do the rest.

If you are using a non-Adobe TMS, or no TMS at all, then please implement ECID to run **before** any other Adobe solutions. See the [ECID documentation](https://experienceleague.adobe.com/docs/id-service/using/home.html) for more details. The only other prerequisite is regarding code versions, so as you simply apply the most recent versions of the code in the following steps, you will be fine.

>[!NOTE]
>
>Please read this entire document before implementing. The “Timing” section below has important information on *when* you should implement each piece, including ECID (if it is not yet implemented).

### Step 1: Record currently used options from DIL code {#step-record-currently-used-options-from-dil-code}

As you get ready to move from client-side DIL code to server-side forwarding, the first step is to identify everything that you are doing with DIL code, including custom settings and data sent to AAM. Things to notice and consider include:

* Normal [!DNL Analytics] variables, using the `siteCatalyst.init` DIL module - You do not need to worry about this one, because its job is just to send the normal [!DNL Analytics] variables over, and that happens by virtue of simply having server-side forwarding enabled.
* Partner Subdomain - In the `DIL.create` function, make a note of the `partner` parameter. This is known as your “partner subdomain,” or sometimes “partner ID,” and will be needed when you place the new server-side forwarding code.
* [!DNL Visitor Service Namespace] - Also known as your “[!DNL Org ID]” or “[!DNL IMS Org ID],” you’ll need this as well when you set up the new server-side forwarding code. Make a note of it.
* containerNSID, uuidCookie, and other advanced options - Make a note of any additional advanced options you are using so that you can set them in the server-side forwarding code as well.
* Additional page variables - If other variables are being sent to AAM from the page (in addition to the normal [!DNL Analytics] variables handled by siteCatalyst.init), you will need to make note of them so that they can be sent in via server-side forwarding (spoiler alert: via [!DNL contextData] variables).

### Step 2: Update the code {#step-updating-the-code}

In [Implementation options](#implementation-options) (above), multiple options are given regarding how and where you are implementing server-side forwarding. In order for this section to be effective, we need to break it out into these sections (with two of them combined). Go to the method of this section that best describes your needs.

#### Adobe Experience Platform tags {#launch-by-adobe}

Watch the video below to learn about moving implementation options from client-side DIL code into server-side forwarding in Experience Platform Launch.

>[!VIDEO](https://video.tv.adobe.com/v/26310/?quality=12)

#### “On the page” or non-Adobe tag manager {#on-the-page-or-non-adobe-tag-manager}

Watch the video below to learn about moving implementation options from client-side DIL code into server-side forwarding in [!DNL AppMeasurement] code, residing either in a file or in a non-Adobe tag management system.

>[!VIDEO](https://video.tv.adobe.com/v/26312/?quality=12)

### Step 3: Enabling the forwarding (per [!UICONTROL Report Suite]) {#step-enabling-the-forwarding-per-report-suite}

So far in this tutorial we have spent all our time on switching the code from client-side DIL code to server-side forwarding. That is fine, because it is the more difficult part. This section, although you will see is super easy, is just as important as updating the code. In this video, you will see how to flip the switch that enables the actual forwarding of data from Analytics to Audience Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26355/?quality-12)

**NOTE:** As stated in the video, remember that it will take up to 4 hours for the enablement of forwarding to be fully implemented on the Experience Cloud backend.

## Timing {#timing}

As a reminder, there are two main tasks for moving over from client-side DIL to server-side forwarding:

1. Updating the code
1. Flipping the switch in the [!DNL Analytics] [!DNL Admin Console]

But the question is, which one do you do first? Does it matter? OK, sorry, that was two questions. But the answers are… it depends, and yes, it *can* matter. How’s that for vague? Let’s break it down. But first an additional question that can come up if you are a large organization with numerous sites: Do I have to do everything at once? That one is a little easier. Nope. You can do it piece by piece.

### A little deeper dive {#a-little-deeper-dive}

The reason why timing and order matter is because of how forwarding _really_ works, which can be summarized in the following few technical facts:

* If you have the Experience Cloud ID Service (ECID) implemented, and the switch in the [!DNL Analytics] [!DNL Admin Console] (“the switch”) is on, data WILL forward from [!DNL Analytics] to AAM, even if you haven’t updated the code yet.
* If you do not have ECID implemented, the data will not forward, even if you have the switch on, and have the server-side forwarding code.
* The server-side forwarding code (whether in Platform tags or on the page) really handles the response and is necessary to complete the migration.
* Remember that the server-side forwarding switch is enabled by the [!UICONTROL report suite], but that the code is handled by the property in Platform tags, or by the [!DNL AppMeasurement] file if you don’t use Platform tags.

### Best practices {#best-practices}

Based on these technical details, here are the recommendations for the timing of what to do and when:

#### If you do NOT have ECID yet implemented {#if-you-do-not-have-ecid-yet-implemented}

1. Flip the switch in [!DNL Analytics] for each [!UICONTROL report suite] that you will enable for server-side forwarding.

    1. Forwarding does not start yet because you don’t have ECID.

1. Per site, update your code from client-side DIL to server-side forwarding (this could be in Platform tags) or on the page, as discussed in another section above).

    1. Forwarding now flows (as you have added ECID), and you should also receive a proper JSON response to your [!DNL Analytics] beacon (see the Validation and Troubleshooting section below for more details).

#### If you do have ECID implemented {#if-you-do-have-ecid-implemented}

1. Prepare and plan so that you are ready to update your code from DIL to server-side forwarding PER [!UICONTROL report suite] that you will enable for server-side forwarding:

    1. Flip the switch in [!DNL Analytics] to enable server-side forwarding.

        1. Forwarding WILL start because you have ECID enabled.

    1. As soon as possible, update your code from client-side DIL to single-side forwarding (this could be in Platform tags or on the page, as discussed in another section above).

        1. You should receive a proper JSON response to your [!DNL Analytics] beacon (see the [Validation and troubleshooting](#validation-and-troubleshooting) section below for more details).

>[!NOTE]
>
>It is important to do these two steps as close to each other as possible, because between steps 1 and 2 above, you will have duplication of data going into AAM. In other words, single-side forwarding will have started sending data from [!DNL Analytics] to AAM, and since DIL code is still on the page, there will also be a hit going directly from the page into AAM, thus doubling the data. As soon as you update the code from DIL to server-side forwarding, this will be alleviated.

>[!NOTE]
>
>If you would rather have a small discrepancy in data rather than a small duplication of data, you can switch the order of steps 1 and 2 above. Moving the code from DIL to server-side forwarding would stop the data flow into AAM until you were able to flip the switch to turn on the server-side forwarding for the [!UICONTROL report suite]. Typically customers would rather have a small doubling of data rather than miss getting visitors into [!UICONTROL traits] and [!UICONTROL segments].

#### Migration timing when you have many sites and [!UICONTROL report suites] {#migration-timing-when-you-have-many-sites-and-report-suites}

This topic is briefly touched on in previous sections, in that the main strategy can be summarized by the following:

Migrate one site/[!UICONTROL report suite] (or group of sites/[!UICONTROL report suites]) at a time.

However, this can get a bit tricky based on a few possible scenarios:

* You have a site that contains several distinct [!UICONTROL report suites]
* You have a [!UICONTROL report suite] that includes several sites (like a global [!UICONTROL report suite])
* You use one Platform tags property to cover several sites
* You have different Development teams for different sites

Because of these items, it can get a bit complicated. The best things I can suggest are:

* Take some time to make a strategy for migrating to server-side forwarding, based on the things that have been explained above
* Based on the fact that a single property in Platform tags (or a single [!DNL AppMeasurement] file) typically maps to 1 or 2 distinct [!UICONTROL report suites], you will likely be able make a plan that works on these distinct groups one by one, updating your enterprise to server-side forwarding
* If you are working with Adobe Consulting, talk to them regarding your migration plan, so that they can help as needed

## Validation and troubleshooting {#validation-and-troubleshooting}

The main way to validate that the server-side forwarding is up and running is by looking at the response to any of your Adobe Analytics hits coming from the app.

If you are not doing server-side forwarding of data from [!DNL Analytics] to Audience Manager, then there is really no response to the [!DNL Analytics] beacon (besides a 2x2 pixel). However, if you are doing server-side forwarding, then there are items that you can verify in the [!DNL Analytics] request and response that will let you know that [!DNL Analytics] is communicating correctly with Audience Manager, forwarding the hit, and getting a response.

>[!VIDEO](https://video.tv.adobe.com/v/26359/?quality=12)

>[!WARNING]
>
>Beware the false "Success." If there is a response, and everything seems to be working, ensure that you have the `stuff` object in the response. If you don't, you may see a message that says `"status":"SUCCESS"`. As crazy as this sounds, this is actually proof that it is NOT working correctly. 
>
>If you see this, it means that you have completed the code update in Platform tags or [!DNL AppMeasurement], but that the forwarding in the [!DNL Analytics] [!DNL Admin Console] has not yet completed. In this case you need to verify that you have enabled server-side forwarding in the [!DNL Analytics] [!DNL Admin Console] for your [!UICONTROL report suite]. If you have, and it hasn't been 4 hours yet, be patient, as it can take that long to make all the necessary changes on the backend.


![false success](assets/falsesuccess.png)

For more information about server-side forwarding, please see the [documentation](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf.html).
