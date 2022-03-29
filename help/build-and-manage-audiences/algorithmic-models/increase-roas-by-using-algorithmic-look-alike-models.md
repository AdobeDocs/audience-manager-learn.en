---
title: Increase ROAS by using Algorithmic (Look-Alike) Models
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
# Increase ROAS by using Algorithmic (Look-Alike) Models in Audience Manager {#increase-roas-by-using-algorithmic-look-alike-models-in-audience-manager}

The real power of Audience Manager's Look-alike [!UICONTROL Modeling] comes when you seek to expand your baseline audience against a quality, brand new set of users from second-party and third-party data sources. In this tutorial, learn the steps needed to create a model from this data.

## Enable second-party or third-party data streams from the Audience Marketplace {#enable-2nd-or-3rd-party-data-streams-from-the-audience-marketplace}

In order to use second-party and third-party data in a look-alike model, we first have to enable this data into your Audience Manager interface. Adobe has a large number of second-party and third-party data providers from which you can choose. These are available for you in a self-serve interface in AAM, via the Audience Marketplace. Navigate to the Audience Marketplace and browse through the possibilities. The following video will show you how to do this, including how to enable free “try before you buy” streams, so that you can lock in on the data that will be most useful to your organization before you commit to the data provider’s pricing.

Also, to help you research and decide on which data provider to use, a great resource is the [[!DNL Adobe Audience Finder]](https://www.adobe-audience-finder.com/).

>[!VIDEO](https://video.tv.adobe.com/v/25188/?quality=12)

## Identify or create an ideal user (conversion) trait or segment {#identify-create-an-ideal-user-conversion-trait-or-segment}

What are you trying to get people to DO on your site? What is your conversion event? Of course, there are many different answers to this question, depending on your site type/vertical and your organizational goals. In any case, it is common in AAM to create a trait for visitors who have met those criteria.

In the video below, I will show you how to create a conversion trait, which you will want to have in place as you continue through this tutorial and create a look-alike model.

Also, when using Adobe Analytics events to create traits, there is a major gotcha that you need to keep in mind, so that you don't collect more users than you should into the trait. Watch the following video for the big reveal. :)

>[!VIDEO](https://video.tv.adobe.com/v/23431/?quality=12)

**NOTE:** In the video above, the example that I show assumes that you have Adobe Analytics. Obviously, this may not be the case. If you have Google Analytics (GA), we have a module that you can use to send data into AAM (see the [documentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-modules.html)), and if your conversion activity on your site is sent to AAM by GA, then you can create your conversion trait from that. If you have a different analytics solution (or no analytics solution), you can still send in data to AAM via our DIL code and the `submit` function, etc. (see the [documentation](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html)). Then create the conversion trait based on the data sent when the conversion activity is performed on the site.

## Create a Look-Alike Model from second-party or third-party data {#create-a-look-alike-model-from-2nd-or-3rd-party-data}

After completing the steps above, we are now ready to create an Algorithmic (Look-alike) Model. As we are setting up the model, we will use the conversion trait as our base trait (key visitors who we want to duplicate), and we will use the enabled third-party data stream as our pool of people to pull from.

>[!VIDEO](https://video.tv.adobe.com/v/25190/?quality-12)

## An important best practice {#an-important-best-practice}

When creating the algorithmic model in Audience Manager, obviously we want the model to be as effective as possible. As the model is considering all of the traits that the members of your base trait/segment are part of, it doesn’t help the model if ALL of the people are in a trait/segment. Therefore, if you have any super generic traits (like everyone who went to your site, or everyone who has received any ad from you, etc.), make sure that the data source that they belong to is NOT included in the data sources in your model. In this article’s use case, it’s unlikely that you would, because we are focusing on looking at third-party data for our new look-alikes, but it’s worth mentioning anyway, and applies to ALL of your algorithmic models.

## Create an [!UICONTROL Algorithmic Trait] {#creating-an-algorithmic-trait}

Next, we will need to create an  [!UICONTROL Algorithmic Trait], so that the results of the model can be used. Without creating a trait, the model is useless. So, after the model runs, be sure to go into the trait dialog and create an [!UICONTROL Algorithmic Trait]. The following video walks through it and shows a couple of tips.

>[!VIDEO](https://video.tv.adobe.com/v/25191/?quality=12)

## Create a segment from the model data and send it to DSPs {#creating-a-segment-from-the-model-data-and-sending-it-to-dsps}

Once you have created an [!UICONTROL Algorithmic Trait], you can create a new segment to put it in, so that you can activate the data (you cannot activate a trait, but rather create a new one-trait segment with the [!UICONTROL Algorithmic Trait] in it, so that you can activate (use) the segment).

Once you have created a segment from this Algorithmic trait, you will have an audience of potential clients who look like people that have already converted on your site. Now you can map this segment to any of your DSP destinations in Audience Manager. You will be able to target your marketing to those look-alikes, who are more likely to convert on your site than just the normal public, increasing your Return on Ad Spend.
