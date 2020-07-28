---
title: Using Look-Alike Models to Extend Sold Out Inventory from Your First Party Data
description: In this tutorial, we will walk through the steps you should take to set up and use Look-Alike Models, so that you can create new look-alike audiences, and sell them as an extension to your conversion segment.
feature: algorithmic models
topics: 
audience: all
activity: use
doc-type: feature video
team: Technical Marketing
kt: 1688
---

# Using Look-Alike [!UICONTROL Models] to Extend Sold Out Inventory from Your [!UICONTROL First Party] Data {#using-look-alike-models-to-extend-sold-out-inventory-from-your-st-party-data}

In this tutorial, we will walk through the steps you should take to set up and use Look-Alike [!UICONTROL Models], so that you can create new look-alike audiences, and sell them as an extension to your conversion [!UICONTROL segment].

## Use Case Details {#use-case-details}

You are a content publisher. If you have already sold out inventory for converters on your site, you might think that your opportunity ends there. Enter AAM’s Look-Alike [!UICONTROL Models]. By using this feature, you can extend sold out inventory further, and also sell audiences of people who maybe haven’t converted yet, but who look/act like people who have converted. This audience [!UICONTROL segment] would typically sell for less than the actual converters, but nevertheless allows you to add to your bottom line by providing an additional audience option for Advertisers who want to place ads on your site. The additional benefit of this use case is that it doesn’t cost you anything to run this model on your first party data.

The steps in this tutorial will be as follows:

1. Identify/Create an ideal user (conversion) [!UICONTROL trait] or [!UICONTROL segment]
1. Create a [!UICONTROL model] using this conversion [!UICONTROL trait]/[!UICONTROL segment] as the base item
1. Choose [!UICONTROL First party] data source(s) in the [!UICONTROL model] and run the [!UICONTROL model]
1. Create an Algorithmic [!UICONTROL Trait] from the [!UICONTROL model] results and add the [!UICONTROL trait] to a [!UICONTROL segment]
1. Offer the [!UICONTROL segment] to interested Advertisers to extend the conversion [!UICONTROL segment] sales

## Identify/Create an ideal user (conversion) [!UICONTROL trait] or [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

What are you trying to get people to DO on your site? What is your conversion event? Of course, there are many different answers to this question, depending on your site type/vertical and your organizational goals. In any case, it is common in AAM to create a [!UICONTROL trait] for visitors who have met those criteria.

In this use case, this is already assumed, because you have sold out the inventory for people who are converters. However, for the purpose of this tutorial, it is good to discuss it as reference for the rest of the use case.

Also, when using events to create [!UICONTROL traits], there is a major gotcha that you need to keep in mind, so that you don't collect more users than you should into the [!UICONTROL trait]. Watch the following video for the big reveal. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**NOTE:** In the video above, the example that I show assumes that you have Adobe Analytics. Obviously, this may not be the case. If you have Google Analytics (GA), we have a module that you can use to send data into AAM (see the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)), and if your conversion activity on your site is sent to AAM by GA, then you can create your conversion trait from that. If you have a different analytics solution (or no analytics solution), you can still send in data to AAM via our DIL code and the `submit` function, etc. (see the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Then, again, create the conversion trait based on the data sent when the conversion activity is performed on the site.

## Creating a Look-Alike [!UICONTROL Model] from [!UICONTROL First Party] Data {#creating-a-look-alike-model-from-first-party-data}

In this step, we are going to create a [!UICONTROL First Party] Look-Alike [!UICONTROL Model]. This means that not only are we going to use a [!UICONTROL first party] conversion [!UICONTROL trait]/[!UICONTROL segment] for our base [!UICONTROL trait]/[!UICONTROL segment] (this would be normal for most [!UICONTROL models] anyway), but we will also only be looking into the pool of [!UICONTROL first party] data for more people who look like the converters. We will not be looking at [!UICONTROL second party] or [!UICONTROL third party] data.

In this use case, this is important, because we are trying to create a [!UICONTROL segment] of users on our site who look like converters but just haven't converted yet, so that we can sell this look-alike [!UICONTROL segment] to interested advertisers.

>[!VIDEO](https://video.tv.adobe.com/v/23504/?quality-12)

## Creating an Algorithmic [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Next we will need to create an Algorithmic [!UICONTROL Trait], so that the results of the [!UICONTROL model] can be used. Without creating a [!UICONTROL trait], the [!UICONTROL model] is useless. So after the [!UICONTROL model] runs, be sure to go into the [!UICONTROL trait] dialog and create an Algorithmic [!UICONTROL Trait]. The following video walks through it, and shows a couple of tips.

>[!VIDEO](https://video.tv.adobe.com/v/23523/?quality=12)

## Offering the Algorithmic [!UICONTROL Segment] to Advertisers {#offering-the-algorithmic-segment-to-advertisers}

Once you have created an Algorithmic [!UICONTROL Trait], you can create a new [!UICONTROL segment] to put it in, so that you can activate the data (you cannot activate a [!UICONTROL trait], but rather create a new one-[!UICONTROL trait] [!UICONTROL segment] with the Algorithmic [!UICONTROL Trait] in it, so that you can activate (use) the [!UICONTROL segment].

Once you have created a [!UICONTROL segment] of [!UICONTROL first party] visitors who have scored high in the look-alike [!UICONTROL model] (I.e. who look like converters but haven’t happened to convert yet), you can offer this [!UICONTROL segment] to advertisers on your site, even after you have sold out all of your inventory of actual converters on your site. This is a great way to extend this audience and continue to see additional revenue by using Look-Alike [!UICONTROL Models] in Audience Manager.
