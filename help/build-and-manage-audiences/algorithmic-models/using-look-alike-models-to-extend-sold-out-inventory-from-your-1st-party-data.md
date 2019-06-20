---
title: Using Look-Alike Models to Extend Sold Out Inventory from Your 1st Party Data
seo-title: Using Look-Alike Models to Extend Sold Out Inventory from Your 1st Party Data
description: In this tutorial, we will walk through the steps you should take to set up and use Look-Alike Models, so that you can create new look-alike audiences, and sell them as an extension to your conversion segment.
seo-description: In this tutorial, we will walk through the steps you should take to set up and use Look-Alike Models, so that you can create new look-alike audiences, and sell them as an extension to your conversion segment.
feature: algorithmic models
topics: 
audience: all
activity: use
doc-type: feature video
author: Doug Moore
team: Technical Marketing
kt: 1688
---

# Using Look-Alike Models to Extend Sold Out Inventory from Your 1st Party Data {#using-look-alike-models-to-extend-sold-out-inventory-from-your-st-party-data}

In this tutorial, we will walk through the steps you should take to set up and use Look-Alike Models, so that you can create new look-alike audiences, and sell them as an extension to your conversion segment.

## Use Case Details {#use-case-details}

You are a content publisher. If you have already sold out inventory for converters on your site, you might think that your opportunity ends there. Enter AAM’s Look-Alike Models. By using this feature, you can extend sold out inventory further, and also sell audiences of people who maybe haven’t converted yet, but who look/act like people who have converted. This audience segment would typically sell for less than the actual converters, but nevertheless allows you to add to your bottom line by providing an additional audience option for Advertisers who want to place ads on your site. The additional benefit of this use case is that it doesn’t cost you anything to run this model on your first party data.

The steps in this tutorial will be as follows:

1. Identify/Create an ideal user (conversion) trait or segment
1. Create a model using this conversion trait/segment as the base item
1. Choose 1st party data source(s) in the model and run the model
1. Create an Algorithmic Trait from the model results and add the trait to a segment
1. Offer the segment to interested Advertisers to extend the conversion segment sales

## Identify/Create an ideal user (conversion) trait or segment {#identify-create-an-ideal-user-conversion-trait-or-segment}

What are you trying to get people to DO on your site? What is your conversion event? Of course, there are many different answers to this question, depending on your site type/vertical and your organizational goals. In any case, it is common in AAM to create a trait for visitors who have met those criteria.

In this use case, this is already assumed, because you have sold out the inventory for people who are converters. However, for the purpose of this tutorial, it is good to discuss it as reference for the rest of the use case.

Also, when using events to create traits, there is a major gotcha that you need to keep in mind, so that you don't collect more users than you should into the trait. Watch the following video for the big reveal. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**NOTE:** In the video above, the example that I show assumes that you have Adobe Analytics. Obviously, this may not be the case. If you have Google Analytics (GA), we have a module that you can use to send data into AAM (see the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)), and if your conversion activity on your site is sent to AAM by GA, then you can create your conversion trait from that. If you have a different Analytics solution (or no analytics solution), you can still send in data to AAM via our DIL code and the submit function, etc. (see the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Then, again, create the conversion trait based on the data sent when the conversion activity is performed on the site.

## Creating a Look-Alike Model from First Party Data {#creating-a-look-alike-model-from-first-party-data}

In this step, we are going to create a 1st Party Look-Alike Model. This means that not only are we going to use a 1st party conversion trait/segment for our base trait/segment (this would be normal for most models anyway), but we will also only be looking into the pool of 1st party data for more people who look like the converters. We will not be looking at 2nd or 3rd party data.

In this use case, this is important, because we are trying to create a segment of users on our site who look like converters but just haven't converted yet, so that we can sell this look-alike segment to interested advertisers.

>[!VIDEO](https://video.tv.adobe.com/v/23504/?quality-12)

## Creating an Algorithmic Trait {#creating-an-algorithmic-trait}

Next we will need to create an Algorithmic Trait, so that the results of the model can be used. Without creating a trait, the model is useless. So after the model runs, be sure to go into the trait dialog and create an Algorithmic Trait. The following video walks through it, and shows a couple of tips.

>[!VIDEO](https://video.tv.adobe.com/v/23523/?quality=12)

## Offering the Algorithmic Segment to Advertisers {#offering-the-algorithmic-segment-to-advertisers}

Once you have created an Algorithmic Trait, you can create a new segment to put it in, so that you can activate the data (you cannot activate a trait, but rather create a new one-trait segment with the Algorithmic Trait in it, so that you can activate (use) the segment.

Once you have created a segment of 1st party visitors who have scored high in the look-alike model (I.e. who look like converters but haven’t happened to convert yet), you can offer this segment to advertisers on your site, even after you have sold out all of your inventory of actual converters on your site. This is a great way to extend this audience and continue to see additional revenue by using Look-Alike Models in Audience Manager.
