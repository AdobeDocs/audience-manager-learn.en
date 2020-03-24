---
title: IAB TCF Support in Audience Manager
seo-title: IAB TCF Support in Audience Manager
description: "Adobe provides you with the means to manage and communicate your users' privacy choices through the Opt-in functionality and through IAB Transparency and Consent Framework (TCF) support. This article works together with the documentation to help you understand the IAB TCF and how it works together with Adobe’s Opt-in object and your Consent Management Provider (CMP). To learn more about the IAB, please see their Web site at https://www.iabeurope.eu/"
seo-description: "Adobe provides you with the means to manage and communicate your users' privacy choices through the Opt-in functionality and through IAB Transparency and Consent Framework (TCF) support. This article works together with the documentation to help you understand the IAB TCF and how it works together with Adobe’s Opt-in object and your Consent Management Provider (CMP). To learn more about the IAB, please see their Web site at https://www.iabeurope.eu/"
feature: privacy
topics: 
audience: implementer, developer, architect
activity: implement
doc-type: technical video
author: Doug Moore
team: Technical Marketing
kt: 2728
---

# [!DNL IAB TCF] Support in Audience Manager {#iab-tcf-support-in-audience-manager}

Adobe provides you with the means to manage and communicate your users' privacy choices through the [!DNL Opt-in] functionality and through [!DNL IAB Transparency and Consent Framework (TCF)] support. This article works together with the documentation to help you understand the [!DNL IAB TCF] and how it works together with Adobe’s Opt-in object and your Consent Management Provider (CMP). To learn more about the [!DNL IAB], please see their Web site at https://www.iabeurope.eu/

## First Step: Understand ECID’s Opt-In {#first-step-understand-ecid-s-opt-in}

To understand how to work with the [!DNL IAB TCF], you must first understand [!DNL Opt-in] functionality, which is part of the Experience Cloud ID Service (ECID) library. If you are not familiar with how Opt-in works, please see [this helpful article](https://helpx.adobe.com/marketing-cloud-core/kt/using/ecid-opt-in-technical-video-implement.html) first. You should also review the Opt-in [documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/). Once you have gone through those resources, return to this page and continue.

## The Audience Manager Plug-In for [!DNL IAB TCF] {#the-audience-manager-plug-in-for-iab-tcf}

Now that you have at least a basic understanding of how Opt-in works, Audience Manager can layer onto it [!DNL IAB Transparency and Consent Framework (TCF)] support, which is done via a plug-in into the Opt-in object.

The Audience Manager plug-in for [!DNL IAB TCF] extends the functionality of Opt-in, and enables AAM customers to evaluate, honor, and forward user privacy choices to downstream partners in accordance with [!DNL IAB TCF]. It provides a standard that data controllers (that’s you as an Adobe customer) and vendors (DMPs, DSPs, SSPs, Ad Servers, etc.) can use to understand consent across the consent landscape.

## Enabling [!DNL IAB TCF] {#enabling-iab-tcf}

Enabling [!DNL IAB TCF] is easy if you are using Adobe Experience Platform Launch, as it is a simple checkbox, as shown in the short video below:

>[!VIDEO](https://video.tv.adobe.com/v/26433/?quality=12)

Alternatively, if you are not using Launch, you can use [!DNL isIabContext=true] to enable it when you instantiate the Experience Cloud Visitor. This initiates the IAB flow, I.e. adds another step to consent gathering, using the [!DNL IAB TCF] to query for the [!DNL IAB TCF] consent string and provides it back to Opt-in, which in turn then communicates with the Experience Cloud solutions.

## [!DNL IAB TCF] Consent String {#iab-tcf-consent-string}

One of the standards that IAB provides is a “consent string (also known as a [!DNL DaisyBit])”, which is really two lists put together:

1. Purposes: **What** is consent being given to do?
1. Vendors: **Who** is consent being given to?

### Purposes {#purposes}

The five standard purposes in the [!DNL IAB TCF] (what vendors can do with the visitor’s data) are:

1. [!DNL Storage and access information]
1. [!DNL Personalization]
1. [!DNL Ad selection, reporting and delivery]
1. [!DNL Content delivery, selection and reporting]
1. [!DNL Measurement]

This is the first part of the [!DNL IAB TCF] consent string and is just recorded as 1’s and 0’s, dictating whether or not that purpose/activity is approved.

### Vendors {#vendors}

The second part of the [!DNL IAB TCF] consent string is a long list of several hundred vendors, so that visitors can be presented with a list of applicable vendors who have tags on the site and can choose which vendors to use. Vendors maintain their spot on the list. For example, Adobe Audience Manager’s vendor number on this list is 565. If that number in the list has a “1”, then Audience Manager can do the approved purposes from the front of the list. If AAM’s spot has a “0”, it cannot do anything with the data.

**For Audience Manager to provide a UI for customers to use the [!DNL IAB TCF] to choose these purposes and vendors, or to approve/disapprove all activity, you must use a CMP partner use a CMP that is registered with IAB or build one that supports IAB and is registered with the [!DNL IAB TCF].**

## Opt-in: Translating between IAB and Adobe Solutions {#opt-in-translating-between-iab-and-adobe-solutions}

One of the benefits of using the [!DNL IAB TCF] is that the standard purposes listed above probably give the end user more of an idea of what they are approving than a list of Adobe solutions. End users might not know what it means to “approve” Audience Manager or [!DNL Target], but “[!DNL Storage and access information]” or “[!DNL Personalization]” is probably easier for them to understand and select.

In order for Audience Manager to be approved (I.e. In order for the translation of IAB purposes for Opt-in to give AAM a “yes” vote), purposes 1, 2, and 5 above have to be given consent from the end user. If any of these are not approved, AAM will not execute pixel fires or set cookies. It’s also good to know that many customers simply choose to provide the end user with an “all or nothing” UI, which would, of course, allow or disallow use of Audience Manager (and the other Experience Cloud solutions).

There is some great information in the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/aam-iab-plugin.html) about how the Audience Manager [!DNL Plug-In] for [!DNL IAB TCF] flow applies to both Publisher and Advertiser use cases.

## IAB: Sending Consent Downstream {#iab-sending-consent-downstream}

When the Audience Manager Plug-in for [!DNL IAB TCF] is used, the user choices that are gathered from the end user will also be sent to the platform-level ([!DNL 3rd party]) ID syncs that have been permitted by customer, so that the partner has the user choice information and can act upon it as well. This information is sent in two variables:

* gdpr = 1
* gdpr_consent = [encoded consent string]

The caveat is that if the user is in IAB context and does not provide consent (or provides negative consent), then Audience Manager doesn’t gather the [!DNL IAB TCF] consent string at all, and as such drop the calls. So, in that case…no passing downstream. For more detailed information about the Audience Manager [!DNL Plug-In] for [!DNL IAB TCF], including how to implement and test, use cases, and workflow, please see the [documentation](https://experiencecloud.adobe.com/resources/help/en_US/aam/aam-iab-plugin.html).

## Demo {#demo}

In the video below, see how cookies and beacons from ECID and solutions are affected by the IAB user choice selections.

>[!VIDEO](https://video.tv.adobe.com/v/26434/?quality=12)