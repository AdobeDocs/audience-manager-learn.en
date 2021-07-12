---
title: Increase ROAS by Using Algorithmic (Look-Alike) Models in Audience Manager
description: The real power of Audience Manager's Look-alike Modeling comes when you seek to expand your baseline audience against a quality, brand new set of users from 2nd and 3rd party data sources. In this tutorial, learn the steps create a model from this data.
feature: Algorithmic Models
topics: 
activity: use
doc-type: feature video
team: Technical Marketing
thumbnail: 25188.jpg
kt: 1849
role: User, Developer, Data Engineer, Architect, Data Architect, Admin, Leader
level: Intermediate
exl-id: 6626ae11-8709-4302-9e03-0d55878d2409
---
# Increase ROAS by Using Algorithmic (Look-Alike) [!UICONTROL Models] in Audience Manager {#increase-roas-by-using-algorithmic-look-alike-models-in-audience-manager}

The real power of Audience Manager's Look-alike [!UICONTROL Modeling] comes when you seek to expand your baseline audience against a quality, brand new set of users from [!UICONTROL second party] and [!UICONTROL third party] [!UICONTROL data sources]. In this tutorial, learn the steps needed to create a [!UICONTROL model] from this data.

## Enable [!UICONTROL Second Party] or [!UICONTROL Third Party] Data Streams from the Audience Marketplace {#enable-2nd-or-3rd-party-data-streams-from-the-audience-marketplace}

In order to use [!UICONTROL second party] and [!UICONTROL third party] data in a look-alike [!UICONTROL model], we first have to enable this data into your Audience Manager interface. Adobe has a large number of [!UICONTROL second party] and [!UICONTROL third party] data providers from which you can choose. These are available for you in a self-serve interface in AAM, via the Audience Marketplace. Navigate to the Audience Marketplace and browse through the possibilities. The following video will show you how to do this, including how to enable free “try before you buy” streams, so that you can lock in on the data that will be most useful to your organization before you commit to the data provider’s pricing.

Also, to help you research and decide on which data provider to use, a great resource is the [[!DNL Adobe Audience Finder]](https://www.adobe-audience-finder.com/).

>[!VIDEO](https://video.tv.adobe.com/v/25188/?quality=12)

## Identify/Create an ideal user (conversion) [!UICONTROL trait] or [!UICONTROL segment] {#identify-create-an-ideal-user-conversion-trait-or-segment}

What are you trying to get people to DO on your site? What is your conversion event? Of course, there are many different answers to this question, depending on your site type/vertical and your organizational goals. In any case, it is common in AAM to create a [!UICONTROL trait] for visitors who have met those criteria.

In the video below, I will show you how to create a conversion [!UICONTROL trait], which you will want to have in place as you continue through this tutorial and create a look-alike [!UICONTROL model].

Also, when using Adobe Analytics events to create [!UICONTROL traits], there is a major gotcha that you need to keep in mind, so that you don't collect more users than you should into the [!UICONTROL trait]. Watch the following video for the big reveal. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**NOTE:** In the video above, the example that I show assumes that you have Adobe Analytics. Obviously, this may not be the case. If you have Google Analytics (GA), we have a module that you can use to send data into AAM (see the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html)), and if your conversion activity on your site is sent to AAM by GA, then you can create your conversion [!UICONTROL trait] from that. If you have a different analytics solution (or no analytics solution), you can still send in data to AAM via our DIL code and the `submit` function, etc. (see the [documentation](https://marketing.adobe.com/resources/help/en_US/aam/c_dil.html)). Then create the conversion [!UICONTROL trait] based on the data sent when the conversion activity is performed on the site.

## Create a Look-alike [!UICONTROL Model] from [!UICONTROL Second Party] or [!UICONTROL Third Party] Data {#create-a-look-alike-model-from-2nd-or-3rd-party-data}

After completing the steps above, we are now ready to create an Algorithmic (Look-alike) [!UICONTROL Model]. As we are setting up the [!UICONTROL model], we will use the conversion [!UICONTROL trait] as our base [!UICONTROL trait] (key visitors who we want to duplicate), and we will use the enabled [!UICONTROL third party] data stream as our pool of people to pull from.

>[!VIDEO](https://video.tv.adobe.com/v/25190/?quality-12)

## An Important Best Practice {#an-important-best-practice}

When creating the algorithmic [!UICONTROL model] in Audience Manager, obviously we want the [!UICONTROL model] to be as effective as possible. As the [!UICONTROL model] is considering all of the [!UICONTROL traits] that the members of your base [!UICONTROL trait]/[!UICONTROL segment] are part of, it doesn’t help the [!UICONTROL model] if ALL of the people are in a [!UICONTROL trait]/[!UICONTROL segment]. Therefore, if you have any super generic [!UICONTROL traits] (like everyone who went to your site, or everyone who has received any ad from you, etc.), make sure that the [!UICONTROL data source] that they belong to is NOT included in the [!UICONTROL data sources] in your [!UICONTROL model]. In this article’s use case, it’s unlikely that you would, because we are focusing on looking at [!UICONTROL third party] data for our new look-alikes, but it’s worth mentioning anyway, and applies to ALL of your algorithmic [!UICONTROL models].

## Creating an Algorithmic [!UICONTROL Trait] {#creating-an-algorithmic-trait}

Next, we will need to create an Algorithmic [!UICONTROL Trait], so that the results of the [!UICONTROL model] can be used. Without creating a [!UICONTROL trait], the model is useless. So, after the [!UICONTROL model] runs, be sure to go into the [!UICONTROL trait] dialog and create an Algorithmic [!UICONTROL Trait]. The following video walks through it and shows a couple of tips.

>[!VIDEO](https://video.tv.adobe.com/v/25191/?quality=12)

## Creating a [!UICONTROL Segment] from the [!UICONTROL Model] Data and Sending it to DSPs {#creating-a-segment-from-the-model-data-and-sending-it-to-dsps}

Once you have created an Algorithmic [!UICONTROL Trait], you can create a new [!UICONTROL segment] to put it in, so that you can activate the data (you cannot activate a [!UICONTROL trait], but rather create a new one-[!UICONTROL trait] [!UICONTROL segment] with the Algorithmic [!UICONTROL Trait] in it, so that you can activate (use) the [!UICONTROL segment]).

Once you have created a [!UICONTROL segment] from this Algorithmic [!UICONTROL trait], you will have an audience of potential clients who look like people that have already converted on your site. Now you can map this [!UICONTROL segment] to any of your DSP [!UICONTROL destinations] in Audience Manager. You will be able to target your marketing to those look-alikes, who are more likely to convert on your site than just the normal public, increasing your Return on Ad Spend. Good luck!
