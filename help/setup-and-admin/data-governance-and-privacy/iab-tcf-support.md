---
title: IAB TCF 2.0 Support in Audience Manager
description: Adobe provides you with the means to manage and communicate your users' privacy choices through the Opt-in functionality and through the Audience Manager Plug-in to IAB Transparency and Consent Framework 2.0 (TCF 2.0) support. This article works together with the documentation to help you understand the Audience Manager Plug-in to IAB TCF and how it works together with Adobe’s Opt-in object and your Consent Management Provider (CMP).
feature: data governance & privacy
topics: 
audience: implementer, architect
activity: implement
doc-type: technical video
team: Technical Marketing
thumbnail: 26434.jpg
kt: 5027
---

# IAB TCF 2.0 Support in Audience Manager {#iab-tcf-support-in-audience-manager}

Adobe provides you with the means to manage and communicate your users' privacy choices through the Opt-in functionality and through the Audience Manager Plug-in to IAB Transparency and Consent Framework 2.0 (TCF 2.0) support. This article works together with the documentation to help you understand the Audience Manager Plug-in to IAB TCF and how it works together with Adobe’s Opt-in object and your Consent Management Provider (CMP). To learn more about the IAB, please see their Web site at [https://www.iabeurope.eu/](https://www.iabeurope.eu/).

## First Step: Understand ECID’s Opt-In {#first-step-understand-ecid-s-opt-in}

To understand how to work with the IAB TCF, you must first understand [!DNL Opt-in] functionality, which is part of the Experience Cloud ID Service (ECID) library. If you are not familiar with how Opt-in works, please see [this helpful article](https://docs.adobe.com/content/help/en/core-services-learn/tutorials/id-service/use-opt-in-to-control-experience-cloud-activities-based-on-user-consent.html) first. You should also review the Opt-in [documentation](https://docs.adobe.com/content/help/en/id-service/using/implementation/opt-in-service/optin-overview.html). Once you have gone through those resources, return to this page and continue.

## The Audience Manager Plug-In for IAB TCF {#the-audience-manager-plug-in-for-iab-tcf}

Now that you have at least a basic understanding of how the Opt-in service works, Audience Manager can layer onto it [!DNL IAB Transparency and Consent Framework (TCF)] support, which is done via a plug-in into the Opt-in object.

The Audience Manager plug-in for IAB TCF extends the functionality of Opt-in, and enables AAM customers to evaluate, honor, and forward user privacy choices to downstream partners in accordance with IAB TCF. It provides a standard that data controllers (that’s you as an Adobe customer) and vendors (DMPs, DSPs, SSPs, Ad Servers, etc.) can use to understand consent across the consent landscape.

## Enabling IAB TCF {#enabling-iab-tcf}

Enabling the Audience Manager Plug-in for IAB TCF is easy if you are using Adobe Experience Platform Launch, as it is a simple checkbox, as shown in the short video below:

>[!VIDEO](https://video.tv.adobe.com/v/26433/?quality=12)

Alternatively, if you are not using Launch, you can use `isIabContext=true` to enable it when you instantiate the Experience Cloud Visitor. This initiates the IAB TCF flow, I.e. adds another step to consent gathering, using the IAB TCF to query for the IAB TC string and provides it back to Opt-in, which in turn then communicates with the Experience Cloud solutions.

## IAB TC String {#iab-tcf-consent-string}

One of the standards that IAB provides is a “consent string" (also known as a "DaisyBit"), which is really two lists put together:

1. Purposes: **What** is consent being given to do?
1. Vendors: **Who** is consent being given to?

### Purposes {#purposes}

With IAB TCF 2.0, there are ten "purposes" for which to gather consent (what vendors can do with the visitor’s data). Adobe Audience Manager does not require all ten, but rather only requires consent for the following purposes, in addition to vendor consent:

* **Purpose 1:** Store and/or access information on a device;
* **Purpose 10:** Develop and improve products;
* **Special Purpose 1:** Ensure security, prevent fraud, and debug.

This is the first part of the IAB TC string and is just recorded as 1’s and 0’s, dictating whether or not that purpose/activity is approved.

>[!NOTE]
>
>Per IAB regulations, Special Purpose 1 (Ensure security, prevent fraud, and debug) is always consented to, and users cannot object to it.

### Vendors {#vendors}

Another part of the IAB TC string is a long list of several hundred vendors, so that visitors can be presented with a list of applicable vendors who have tags on the site and can choose which vendors to use. Vendors maintain their spot on the list. For example, Adobe Audience Manager’s vendor number on this list is 565. If that number in the list has a “1”, then Audience Manager can do the approved purposes from the front of the list. If AAM’s spot has a “0”, it cannot do anything with the data.

**For Audience Manager to provide a UI for customers to use the IAB TCF to choose these purposes and vendors, or to approve/disapprove all activity, you must use a CMP partner that is registered with IAB TCF or build one that supports IAB TCF and is registered with the IAB TCF.**

## Opt-in: Translating between IAB and Adobe Solutions {#opt-in-translating-between-iab-and-adobe-solutions}

One of the benefits of using the IAB TCF is that the standard purposes listed above probably give the end user more of an idea of what they are approving than a list of Adobe solutions. End users might not know what it means to “approve” Audience Manager or [!DNL Target], but “Store and/or access information on a device” or “Develop and improve products” is probably easier for them to understand and consent to.

In order for Audience Manager to be approved (I.e. In order for the translation of IAB purposes for Opt-in to give AAM a “yes” vote), purposes 1 and 10, as listed above, have to be given consent from the end user. If either of these are not approved, or if a vender is not approved, AAM will not execute pixel fires or set cookies. It’s also good to know that many customers simply choose to provide the end user with an “all or nothing” UI, which would, of course, allow or disallow use of Audience Manager (and the other Experience Cloud solutions).

There is some great information in the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/aam-iab-plugin.html) about how the Audience Manager Plug-In for IAB TCF flow applies to both Publisher and Advertiser use cases.

## IAB: Sending Consent Downstream {#iab-sending-consent-downstream}

When the Audience Manager Plug-in for IAB TCF is used, the user's consent choices will also be sent to the platform-level (3rd party) ID syncs for partners who are present on the Global Vendor List, so that the partner has the user consent information and can act upon it as well. This information is sent in two variables:

* gdpr = 1
* gdpr_consent = [encoded consent string]
  
The caveat is that if the user is in IAB context and does not provide consent (or provides negative consent), then Audience Manager doesn’t gather the IAB TC string at all, and as such drops the calls. So, in that case…no passing of consent downstream.

## Demo {#demo}

In the video below, see how cookies and beacons from ECID and solutions are affected by the IAB user choice selections.

>[!VIDEO](https://video.tv.adobe.com/v/26434/?quality=12)

For more detailed information about the Audience Manager Plug-In for IAB TCF 2.0, including how to implement and test, use cases, and workflow, please see the [documentation](https://docs.adobe.com/content/help/en/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html).
