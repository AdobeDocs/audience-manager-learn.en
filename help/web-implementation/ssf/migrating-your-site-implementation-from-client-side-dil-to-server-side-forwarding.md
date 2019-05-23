---
title: Migrating Your Site's AAM Implementation from Client-Side DIL to Server-Side Forwarding
seo-title: Migrating Your Site's AAM Implementation from Client-Side DIL to Server-Side Forwarding
description: This tutorial applies to you if you have both Adobe Audience Manager (AAM) and Adobe Analytics, and you are currently sending a hit from the page to AAM using “DIL” (Data Integration Library) code, and also sending a hit from the page to Adobe Analytics. Since you have both of these solutions, and since they are both part of the Adobe Experience Cloud, you have the opportunity to follow the best practice of turning on “Server-Side Forwarding (SSF),” which enables the Analytics data collection servers to forward site analytics data in real time to Audience Manager, instead of having client-side code send an additional hit from the page to AAM. This tutorial will walk you through the steps of making the switch from the older “Client-Side DIL” implementation to the newer “Server-Side forwarding” method.
seo-description: This tutorial applies to you if you have both Adobe Audience Manager (AAM) and Adobe Analytics, and you are currently sending a hit from the page to AAM using “DIL” (Data Integration Library) code, and also sending a hit from the page to Adobe Analytics. Since you have both of these solutions, and since they are both part of the Adobe Experience Cloud, you have the opportunity to follow the best practice of turning on “Server-Side Forwarding (SSF),” which enables the Analytics data collection servers to forward site analytics data in real time to Audience Manager, instead of having client-side code send an additional hit from the page to AAM. This tutorial will walk you through the steps of making the switch from the older “Client-Side DIL” implementation to the newer “Server-Side forwarding” method.
uuid: d096d5c0-4d72-4525-9043-0c09f394d1b6
products: SG_ANALYTICS
products: SG_AUDIENCEMANAGER
discoiquuid: 164d6b0b-05d4-4b45-a7e4-f35b5f6f2571
targetaudience: target-audience new;target-audience ongoing
index: y
internal: n
snippet: y
---

# Migrating Your Site's AAM Implementation from Client-Side DIL to Server-Side Forwarding {#migrating-your-site-s-aam-implementation-from-client-side-dil-to-server-side-forwarding}

This tutorial applies to you if you have both Adobe Audience Manager (AAM) and Adobe Analytics, and you are currently sending a hit from the page to AAM using “DIL” (Data Integration Library) code, and also sending a hit from the page to Adobe Analytics. Since you have both of these solutions, and since they are both part of the Adobe Experience Cloud, you have the opportunity to follow the best practice of turning on “Server-Side Forwarding (SSF),” which enables the Analytics data collection servers to forward site analytics data in real time to Audience Manager, instead of having client-side code send an additional hit from the page to AAM. This tutorial will walk you through the steps of making the switch from the older “Client-Side DIL” implementation to the newer “Server-Side forwarding” method.

## Client-Side (DIL) vs. Server-Side {#client-side-dil-vs-server-side}

When comparing and contrasting these two methods of getting Adobe Analytics data into AAM, it might first be helpful to visualize the differences in the following image:

![client-side to server-side](assets/client-side_vs_server-side_aam_implementation.png)

### Client-side DIL Implementation {#client-side-dil-implementation}

If you are using this method to get Adobe Analytics data into AAM, it means that you have two hits coming from your Web pages: One going to Analytics, and one going to AAM (after having copied the Analytics data on the Web page. Segments are returned from AAM to the page, where they can be used for personalization, etc. This is considered a “legacy” implementation and is no longer recommended.

Beyond the fact that this is not following best practices, the disadvantages of using this method include:

* Two hits coming from the page instead of just one
* Server-Side Forwarding is required for real-time sharing of AAM audiences to Analytics, so Client-side implementations do not allow for this feature (and potentially other features in the future)

It is recommended that you move to a Server-Side Forwarding method of AAM implementation.

### Server-Side Forwarding Implementation {#server-side-forwarding-implementation}

As shown in the image above, a hit comes from the Web page to Adobe Analytics. Analytics then forwards that data to AAM in real time, and visitors are evaluated into AAM traits and segments, just as if the hit had come directly from the page.

Segments are returned on the same real-time hit back to Analytics, which forwards the response on to the Web page for personalization, etc.

There is no timing downside to moving to Server-Side Forwarding. We highly recommend that anyone who has both Audience Manager and Analytics utilize this implementation method.

## You Have TWO Main Tasks {#you-have-two-main-tasks}

There is quite a bit of info on this page, and it is all important, of course. However, it **all boils down to two main things that you need to do**:

1. Change your code from Client-Side DIL code to Server-Side Forwarding code
1. Flip the switch in the Analytics Admin Console to start the actual forwarding of data (per report suite)

If you skip either of these two, SSF will not work correctly. Steps and additional data have been added to this document to help you do these two steps correctly for your setup.

## Implementation Options {#implementation-options}

As you move from client-side to server-side, one of the tasks you will have is changing the code to the new Server-Side Forwarding code. This is done using one of the following options:

* Adobe Launch - Our recommended implementation option for Web properties. You’ll see that this is a very easy task, as Launch has done all of the hard stuff for you.
* On the page - You can also place the new SSF code directly into the doPlugins function inside of your appMeasurement.js file, if you are not (yet) using Adobe Launch
* Other tag managers - These can be treated just like the previous (On the page) option, as you will still put the SSF code in doPlugins, wherever the other tag manager is storing the AppMeasurement code

We’ll look at each of these below in the Updating the Code section.

## Implementation Steps {#implementation-steps}

### Step 0: Prerequisite: Experience Cloud ID Service (ECID) {#step-prerequisite-experience-cloud-id-service-ecid}

The main prerequisite for moving to Server-Side Forwarding is to have the Experience Cloud ID Service implemented. This is most easily done if you are using Launch, by Adobe, in which case you simply install the ECID extension and it will do the rest.

If you are using a non-Adobe TMS, or no TMS at all, then please implement ECID to run **before** any other Adobe solutions. See the [ECID documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/) for more details. The only other prerequisite is regarding code versions, so as you simply apply the most recent versions of the code in the following steps, you will be fine.

>[!NOTE] Please read this entire document before implementing. The “Timing” section below has important information on *when* you should implement each piece, including ECID (if it is not yet implemented).

### Step 1: Record Currently Used Options from DIL Code {#step-record-currently-used-options-from-dil-code}

As you get ready to move from Client-Side DIL code to Server-Side Forwarding, the first step is to identify everything that you are doing with DIL code, including custom settings and data sent to AAM. Things to notice and consider include:

* Normal Analytics variables, using the siteCatalyst.init DIL module - You won’t need to worry about this one, because its job is just to send the normal Analytics variables over, and that will happen by virtue of simply having SSF enabled.
* Partner ID - In the DIL.create function, make a note of the “partner” parameter. This is known as your “partner ID,” or sometimes “partner subdomain,” and will be needed when you place the new SSF code.
* Visitor Service Namespace - Also known as your “Org ID” or “IMS Org ID,” you’ll need this as well when you set up the new SSF code. Make a note of it.
* containerNSID, uuidCookie, and other advanced options - Make a note of any additional advanced options you are using so that you can set them in the SSF code as well.
* Additional page variables - If other variables are being sent to AAM from the page (in addition to the normal Analytics variables handled by siteCatalyst.init), you will need to make note of them so that they can be sent in via SSF (spoiler alert: via contextData variables).

### Step 2: Updating the Code {#step-updating-the-code}

In the section above titled “Implementation Options,” multiple options are given regarding how/where you are implementing Server-Side Forwarding. In order for this section to be effective, we need to break it out into these sections (with two of them combined). Go to the method of this section that best describes your needs.

#### Launch, by Adobe {#launch-by-adobe}

Watch the video below to learn about moving implementation options from Client-Side DIL code into Server-Side Forwarding in Launch, by Adobe.

>[!VIDEO](https://video.tv.adobe.com/v/26310/?quality=12)

#### “On the Page” or Non-Adobe Tag Manager {#on-the-page-or-non-adobe-tag-manager}

Watch the video below to learn about moving implementation options from Client-Side DIL code into Server-Side Forwarding in AppMeasurement code, residing either in a file or in a non-Adobe tag management system.

>[!VIDEO](https://video.tv.adobe.com/v/26312/?quality=12)

### Step 3: Enabling the forwarding (per Report Suite) {#step-enabling-the-forwarding-per-report-suite}

So far in this tutorial we have spent all our time on switching the code from Client-Side DIL code to Server-Side Forwarding. That is fine, because it is the more difficult part. This section, although you will see is super easy, is just as important as updating the code. In this video, you will see how to flip the switch that enables the actual forwarding of data from Analytics to Audience Manager.

>[!VIDEO](https://video.tv.adobe.com/v/26355/?quality-12)

**NOTE:** As stated in the video, remember that it will take up to 4 hours for the enablement of forwarding to be fully implemented on the Experience Cloud backend.

## Timing {#timing}

As a reminder, there are two main tasks for moving over from Client-Side DIL to Server-Side Forwarding:

1. Updating the code
1. Flipping the switch in the Analytics Admin Console

But the question is, which one do you do first? Does it matter? OK, sorry, that was two questions. But the answers are… it depends, and yes, it *can* matter. How’s that for vague? Let’s break it down. But first an additional question that can come up if you are a large organization with a lot of sites: Do I have to do everything at once? That one is a little easier. Nope. You can do it piece by piece…sort of. :)

### A Little Deeper Dive {#a-little-deeper-dive}

The reason why timing and order matter is because of how forwarding *really *works, which can be summarized in the following few technical facts:

* If you have the Experience Cloud ID Service (ECID) implemented, and the switch in the Analytics Admin Console (“the switch”) is on, data WILL forward from Analytics to AAM, even if you haven’t updated the code yet.
* If you do not have ECID implemented, the data will not forward, even if you have the switch on, and have the SSF code.
* The SSF code (whether in Launch or on the page) really handles the response and is of course necessary to complete the migration.
* Remember that the SSF switch is enabled by Report Suite, but that the code is handled by property in Launch, or by AppMeasurement file if you don’t use Launch

### Best Practices {#best-practices}

Based on these technical details, here are the recommendations for the timing of “what to do when”:

#### If you do NOT have ECID yet implemented {#if-you-do-not-have-ecid-yet-implemented}

1. Flip the switch in Analytics for each report suite that you will enable for SSF

    1. Forwarding will not start yet because you don’t have ECID

1. Per site, update your code from Client-Side DIL to SSF (this could be in Launch or on the page, as discussed in another section above)

    1. Forwarding will now flow (as you have added ECID), and you should also receive a proper JSON response to your Analytics beacon (see the Validation and Troubleshooting section below for more details)

#### If you do have ECID implemented {#if-you-do-have-ecid-implemented}

1. Prepare and plan so that you are ready to update your code from DIL to SSF
1. PER report suite that you will enable for SSF:

    1. Flip the switch in Analytics to enable SSF

        1. Forwarding WILL start because you have ECID enabled

    1. As soon as possible, update your code from Client-Side DIL to SSF (this could be in Launch or on the page, as discussed in another section above)

        1. You should receive a proper JSON response to your Analytics beacon (see the Validation and Troubleshooting section below for more details)

**NOTE 1:** It is important to do these two steps as close to each other as possible, because between steps ‘a’ and ‘b’ above, you will have duplication of data going into AAM. In other words, SSF will have started sending data from Analytics to AAM, and since DIL code is still on the page, there will also be a hit going directly from the page into AAM, thus doubling the data. As soon as you update the code from DIL to SSF, this will be alleviated.

**NOTE 2:** If you would rather have a small discrepancy in data rather than a small duplication of data, you can switch the order of ‘a’ and ‘b’ above. Moving the code from DIL to SSF would stop the data flow into AAM until you were able to flip the switch to turn on the SSF for the report suite. Typically customers would rather have a small doubling of data rather than miss getting visitors into traits and segments.

#### Migration Timing when You Have Many Sites and Report Suites {#migration-timing-when-you-have-many-sites-and-report-suites}

This topic is briefly touched on in previous sections, in that the main strategy can be summarized by the following:

Migrate one site/report suite (or group of sites/report suites) at a time.

However, this can get a bit tricky based on a few possible scenarios:

* You have a site that contains several distinct report suites
* You have a report suite that includes several sites (like a global report suite)
* You use one Launch property to cover several sites
* You have different Development teams for different sites

Because of these items, it can get a bit complicated. The best things I can suggest are:

* Take some time to make a strategy for migrating to SSF, based on the things that have been explained above
* Based on the fact that a single property in Launch (or a single AppMeasurement file) typically maps to 1 or 2 distinct report suites, you will likely be able make a plan that works on these distinct groups one by one, updating your enterprise to SSF
* If you are working with Adobe Consulting, talk to them regarding your migration plan, so that they can help as needed

## Validation and Troubleshooting {#validation-and-troubleshooting}

The main way to validate that the Server-Side Forwarding is up and running is by looking at the response to any of your Adobe Analytics hits coming from the app.

If you are not doing server-side forwarding of data from Analytics to Audience Manager, then there is really no response to the Analytics beacon (besides a 2x2 pixel). However, if you are doing SSF, then there are items that you can verify in the Analytics request and response that will let you know that Analytics is communicating correctly with Audience Manager, forwarding the hit, and getting a response.

>[!VIDEO](https://video.tv.adobe.com/v/26359/?quality=12)

**WARNING:** Beware the False "Success" - If there is a response, and everything seems to be working, make sure that you have the "stuff" object in the response. If you don't, you may see a message that says "status":"SUCCESS". As crazy as this sounds, this is actually proof that it is NOT working correctly. If you see this, it means that you have completed the code update in Launch or AppMeasurement, but that the forwarding in the Analytics Admin Console has not yet completed. In this case you need to verify that you have enabled SSF in the Analytics Admin Console for your report suite. If you have, and it hasn't been 4 hours yet, be patient, as it can take that long to make all the necessary changes on the backend.

![false success](assets/falsesuccess.png)

For more information about Server-Side Forwarding, please see the [documentation](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).