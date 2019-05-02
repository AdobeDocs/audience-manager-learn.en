---
title: Increase ROAS by Using Algorithmic (Look-Alike) Models in Audience Manager
seo-title: Increase ROAS by Using Algorithmic (Look-Alike) Models in Audience Manager
description: The real power of Audience Manager's Look-alike Modeling comes when you seek to expand your baseline audience against a quality, brand new set of users from 2nd and 3rd party data sources. In this tutorial, learn the steps needed to create a model from this data.
seo-description: The real power of Audience Manager's Look-alike Modeling comes when you seek to expand your baseline audience against a quality, brand new set of users from 2nd and 3rd party data sources. In this tutorial, learn the steps needed to create a model from this data.
uuid: f57cdc09-3ea4-448b-8e92-66018d6d5352
products: SG_ANALYTICS
discoiquuid: 4fe49ac7-87ce-413b-9d6d-ca621a83fa91
targetaudience: target-audience new;target-audience ongoing
index: y
internal: n
snippet: y
---

# Increase ROAS by Using Algorithmic (Look-Alike) Models in Audience Manager{#increase-roas-by-using-algorithmic-look-alike-models-in-audience-manager}

## Enable 2nd or 3rd Party Data Streams from the Audience Marketplace {#enable-nd-or-rd-party-data-streams-from-the-audience-marketplace}

In order to use 2 and 3 party data in a look-alike model, we first have to enable this data into your Audience Manager interface. Adobe has a large number of 2 and 3 party data providers from which you can choose. These are available for you in a self-serve interface in AAM, via the Audience Marketplace. Navigate to the Audience Marketplace and browse through the possibilities. The following video will show you how to do this, including how to enable free “try before you buy” streams, so that you can lock in on the data that will be most useful to your organization before you commit to the data provider’s pricing.

Also, to help you research and decide on which data provider to use, a great resource is the [Adobe Audience Finder](https://www.adobe-audience-finder.com/).

>[!VIDEO](https://video.tv.adobe.com/v/25188/?quality=12)

## Identify/Create an ideal user (conversion) trait or segment {#identify-create-an-ideal-user-conversion-trait-or-segment}

What are you trying to get people to DO on your site? What is your conversion event? Of course, there are many different answers to this question, depending on your site type/vertical and your organizational goals. In any case, it is common in AAM to create a trait for visitors who have met those criteria.

In the video below, I will show you how to create a conversion trait, which you will want to have in place as you continue through this tutorial and create a look-alike model.

Also, when using Adobe Analytics events to create traits, there is a major gotcha that you need to keep in mind, so that you don't collect more users than you should into the trait. Watch the following video for the big reveal. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

NOTE: In the video above, the example that I show assumes that you have Adobe Analytics. Obviously, this may not be the case. If you have Google Analytics (GA), we have a module that you can use to send data into AAM (documented [here](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)), and if your conversion activity on your site is sent to AAM by GA, then you can create your conversion trait from that. If you have a different Analytics solution (or no analytics solution), you can still send in data to AAM via our DIL code and the submit function, etc. (documented [here](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Then, again, create the conversion trait based on the data sent when the conversion activity is performed on the site.

## Create a Look-alike Model from 2nd or 3rd Party Data {#create-a-look-alike-model-from-nd-or-rd-party-data}

After completing the steps above, we are now ready to create an Algorithmic (Look-alike) Model. As we are setting up the model, we will use the conversion trait as our base trait (key visitors who we want to duplicate), and we will use the enabled 3 party data stream as our pool of people to pull from.

>[!VIDEO](https://video.tv.adobe.com/v/25190/?quality-12)

## An Important Best Practice {#an-important-best-practice}

When creating the algorithmic model in Audience Manager, obviously we want the model to be as effective as possible. As the model is considering all of the traits that the members of your base trait/segment are part of, it doesn’t help the model if ALL of the people are in a trait/segment. Therefore, if you have any super generic traits (like everyone who went to your site, or everyone who has received any ad from you, etc.), make sure that the data source that they belong to is NOT included in the data sources in your model. In this article’s use case, it’s unlikely that you would, because we are focusing on looking at 3 party data for our new look-alikes, but it’s worth mentioning anyway, and applies to ALL of your algorithmic models.

## Creating an Algorithmic Trait {#creating-an-algorithmic-trait}

Next, we will need to create an Algorithmic Trait, so that the results of the model can be used. Without creating a trait, the model is useless. So, after the model runs, be sure to go into the trait dialog and create an Algorithmic Trait. The following video walks through it and shows a couple of tips.

>[!VIDEO](https://video.tv.adobe.com/v/25191/?quality=12)

## Creating a Segment from the Model Data and Sending it to DSPs {#creating-a-segment-from-the-model-data-and-sending-it-to-dsps}

Once you have created an Algorithmic Trait, you can create a new segment to put it in, so that you can activate the data (you cannot activate a trait, but rather create a new one-trait segment with the Algorithmic Trait in it, so that you can activate (use) the segment).

Once you have created a segment from this Algorithmic trait, you will have an audience of potential clients who look like people that have already converted on your site. Now you can map this segment to any of your DSP destinations in Audience Manager, and you will be able to target your marketing to those look-alikes, who are more likely to convert on your site than just the normal public, increasing your Return on Ad Spend. Good luck!

## More AAM Videos {#more-aam-videos}

For more AAM Videos, visit the [Helpx AAM page](https://helpx.adobe.com/audience-manager/kt/index/aam-videos.html).
