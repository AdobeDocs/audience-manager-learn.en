---
title: Updating to Adobe Audience Manager’s DIL version 8.0 (or greater)
seo-title: Updating to Adobe Audience Manager’s DIL version 8.0 (or greater)
description: This article will give you steps and recommendations on updating Adobe Audience Manager (AAM) Data Integration Library (DIL) code to version 8.0 or later. This is referring to “client-side” DIL implementation, not server-side forwarding of Adobe Analytics data, and will cover DTM, Launch by Adobe, and implementations with no Adobe tag manager solution.
seo-description: This article will give you steps and recommendations on updating Adobe Audience Manager (AAM) Data Integration Library (DIL) code to version 8.0 or later. This is referring to “client-side” DIL implementation, not server-side forwarding of Adobe Analytics data, and will cover DTM, Launch by Adobe, and implementations with no Adobe tag manager solution.
uuid: 2cf92535-58af-4f56-9284-258cb527c280
products: SG_AUDIENCEMANAGER
discoiquuid: 13c92bbe-43bb-4c73-8b88-48ab4b3251fa
targetaudience: target-audience new;target-audience ongoing
index: y
internal: n
snippet: y
---

# Updating to Adobe Audience Manager’s DIL version 8.0 (or greater){#updating-to-adobe-audience-manager-s-dil-version-or-greater}

This article will give you steps and recommendations on updating Adobe Audience Manager (AAM) Data Integration Library (DIL) code to version 8.0 or later. This is referring to “client-side” DIL implementation, not server-side forwarding of Adobe Analytics data, and will cover DTM, Launch by Adobe, and implementations with no Adobe tag manager solution.

## Overview {#overview}

Audience Manager’s Data Integration Library (DIL) code allows you to implement AAM on your Web site*. When implementing previous versions of DIL, it was not required to have Adobe’s Experience Cloud ID Service (ECID) implemented as well (although it was a very good idea). Starting with DIL version 8.0, there is a hard dependency on ECID version 3.3 or later. If you implement DIL 8.0 or later without ECID 3.3, or with an earlier version, you will get an error and it will not function. As there are multiple ways that you can implement AAM, we created this page to give you some steps to go through, as well as some recommendations. Below you will find these steps and recommendations broken out by platform/implementation method. More information about DIL is available in the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html).

*&#42;* As stated in the description of this page, this will only cover “client-side” DIL implementations, used by AAM customers who do not have Adobe Analytics. If you have Adobe Analytics, you should use the server-side forwarding method of implementing AAM. This method is described in the [documentation](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).

## Duplicate and Deprecated Elements and Methods {#duplicate-and-deprecated-elements-and-methods}

In prior versions of DIL and ECID, there were duplicative methods (methods that do the same function in both DIL and ECID), which caused confusion regarding which one to use. Typically, you needed to use both of them and match them up, and that message was not well communicated to our customers. Starting with DIL 8.0, these duplicate methods and elements have been deprecated in DIL, and it is recommended that you use the ECID version.

For example:

* When using DIL.create, a few elements have been deprecated and you should use the ECID elements instead. These elements are called out in the [DIL.create documentation](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_create.html).
* The idSync instance-level method has also been deprecated, as called out in the method’s [documentation](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html).

## ID Syncing with a Customer ID {#id-syncing-with-a-customer-id}

In AAM, you can synchronize your UUID (anonymous unique user ID) on the machine with a customer ID, so that you can upload offline data about that customer and tie it together with their online behavior, to get a better understanding of your customers. In the past, this has been done in one of two ways:

* The idSync instance-level method
* The declaredId element in DIL.create

If you have been using either of these older methods to sync with a customer ID, it is highly recommended that you update to using the setCustomerIDs method, which is part of the ECID Service. More information about setCustomerIDs is available in the method’s [documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_setcustomerids.html).

**Quick Tip:** When previously using either of the methods above, you referenced the AAM Data Source with the Data Source ID (AKA the “DPID”). When updating to setCustomerIDs, you will need to use the AAM Data Source’s “Integration Code” instead. It still points to the same Data Source but is just a different identifier. This is shown in the video below.

>[!VIDEO](https://video.tv.adobe.com/v/23873/?quality=12)

The following sections list steps and recommendations for updating to DIL 8.0 based on your implementation method:

## Updating to DIL 8.0 in Launch by Adobe {#updating-to-dil-in-launch-by-adobe}

Basic Steps for Updating to DIL 8.0

1. If you are using pre-8.0 DIL, before you upgrade, go into the DIL configuration in the AAM extension, and take a note of any advanced options that you are using (to be used in a subsequent step)
1. Update your AAM extension to version 8.0 or greater
1. Verify that your Experience Cloud ID Service extension is version 3.3.0 or greater
1. For any deprecated methods/elements (like "disableIDSyncs") that were in your pre-8.0 AAM Extension or in custom code for DIL, enable the ECID methods in the ECID extension.

    1. (DIL) disableDestinationPublishingIframe -&gt; (ECID) disableIdSyncs
    1. (DIL) disableIDSyncs -&gt; (ECID) disableIdSyncs
    1. (DIL) iframeAkamaiHTTPS -&gt; (ECID) dSyncSSLUseAkamai
    1. (DIL) declaredId -&gt; (ECID) setCustomerIDs

1. Publish the changes

>[!VIDEO](https://video.tv.adobe.com/v/23874/?quality=12)

## Updating to DIL 8.0 in Adobe DTM {#updating-to-dil-in-adobe-dtm}

1. Update your AAM tool to version 8.0 or greater. This version setting is under the “General” section of the AAM tool.
1. For any deprecated methods/elements (like "disableIDSyncs") that were in your pre-8.0 AAM Tool’s custom code for DIL, make note of them (so that you can add them to the ECID tool) and then remove them from the custom DIL code in the AAM tool.
1. Update your Experience Cloud ID Service extension to version 3.3.0 or greater
1. Add the advanced options to the ECID tool that you removed from the AAM tool’s custom code.
1. Publish the changes

## Updating to DIL 8.0 with No Adobe Tag Management Solution {#additional-resources}

If you are updating your code directly on the page, then you can just replace older items with newer items, except for when you need to move methods/elements from DIL to ECID, as discussed above. In that case you will simply replace the old method/element in the DIL location with the ECID method/element in the ECID location.

The same really goes for non-Adobe tag managers. Wherever you have the old versions in that TMS, replace it with the new code as described in the following steps.

1. Update your DIL library to the latest version (8.0 or greater) - You will need to get the latest DIL code from Adobe Consulting or Adobe Customer Care, as it is not currently available in a public location. Then simply replace the old DIL library code with the new DIL library code and move on to the next step (don’t stop now or you’ll run into issues, ha).
1. Install ECID Service or update your existing version to 3.3.0 or greater. You can download the latest Experience Cloud ID Service release [from our GitHub page](https://github.com/Adobe-Marketing-Cloud/id-service/releases). If you need help with this, see the [documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/) or talk to an Adobe Consultant.

1. Verify that any deprecated methods or elements that are in your custom code for DIL are moved to the ECID methods:

    1. (DIL) disableDestinationPublishingIframe -&gt; (ECID) disableIdSyncs

        [Documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-disableidsync.html)

    1. (DIL) disableIDSyncs -&gt; (ECID) disableIdSyncs

        [Documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-disableidsync.html)

    1. (DIL) iframeAkamaiHTTPS -&gt; (ECID) idSyncSSLUseAkamai

        [Documentation](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_create.html)

    1. (DIL) declaredId -&gt; (ECID) setCustomerIDs

        [Documentation](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_setcustomerids.html)