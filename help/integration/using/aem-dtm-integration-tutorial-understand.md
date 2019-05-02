---
title: Understanding AEM Integration with DTM, Analytics and Target
seo-title: Understanding AEM Integration with DTM, Analytics and Target
description: Technical walkthrough integrating AEM 6.3 with Adobe Analytics, Adobe Target, and Dynamic Tag Management to build, deliver and measure personalized experiences. Also, examine how to leverage Context Hub to use your data for personalizing experiences and AEM Content Insights to visualize content KPIs. 
seo-description: Technical walkthrough integrating AEM 6.3 with Adobe Analytics, Adobe Target, and Dynamic Tag Management to build, deliver and measure personalized experiences. Also, examine how to leverage Context Hub to use your data for personalizing experiences and AEM Content Insights to visualize content KPIs. 
page-status-flag: never-activated
uuid: c2eb1a71-c56f-4d57-b4ca-e3352f903256
products: SG_ANALYTICS
products: SG_EXPERIENCEMANAGER/6.3/SITES
products: SG_TARGET
topic-tags: DTM
topic-tags: integration
discoiquuid: 0033cef5-1ceb-46cf-91e4-5e821042327c
targetaudience: target-audience advanced
index: y
internal: n
snippet: y
---

# Understanding AEM Integration with DTM, Analytics and Target{#understanding-aem-integration-with-dtm-analytics-and-target}

## Scenario {#scenario}

>[!VIDEO](https://video.tv.adobe.com/v/18045/?quality=9)

![Architecture Overview](assets/diagram.png) 
**Adobe Experience Manager** - Adobe Experience Manager (AEM) is a comprehensive content management solution for building website and forms. And it makes it easy to manage your marketing content and assets.  

**Adobe Target **- Adobe Target (Target) is a personalization solution that makes it easy to identify your best content through tests that are easy to execute. So you can deliver the right experience to the right customer.  

**Adobe Analytics **- Adobe Analytics (Analytics) is the industry-leading solution for applying real-time analytics and detailed segmentation across all of your marketing channels. Use it to discover high-value audiences and power customer intelligence for your business.  

**Dynamic Tag Managemen**t - Digital Marketing cloud service that allows a marketer to manage Adobe and third-party tags used for tracking or other analytic purposes. It is done through client-side scripting that injects tag related code throughout the pages of the site.  

**Core Services - Profiles and Audiences ** - Profiles and Audiences core service gives you a complete and actionable view of your customers. It provides a common ID service (Marketing Cloud ID Service) to   
identify audiences across Adobe solutions so insights are taken from one solution can be applied in another.  

By using these products together, you can build engaging solutions that let you deliver the best content to a given web site visitor. That is, you display content from AEM DAM that meets the interest of the visitor. This development article walks you through how to build a solution that uses AEM, Analytics, Target, and DTM.  

## Accessing Dynamic Tag Management within Adobe Marketing Cloud {#dynamictagmanagement-cloud}

>[!VIDEO](https://video.tv.adobe.com/v/18029/?quality=9)

Adobe's Dynamic Tag Manager (DTM) allows marketers to manage tags, distribute data, and simplifies tag management.

1. [Linking Activation - Dynamic Tag Management (DTM) account to Marketing Cloud](https://helpx.adobe.com/dtm/kb/linking-activation-account-to-marketing-cloud.html)
1. [Dynamic Tag Management (DTM) Documentation](https://helpx.adobe.com/marketing-cloud/dynamic-tag-management.html)

## Configuring Analytics with DTM  {#analytics-dtm}

>[!VIDEO](https://video.tv.adobe.com/v/18030/?quality=9)

1. [Getting Started with Adobe Dynamic Tag Management](https://blogs.adobe.com/digitalmarketing/analytics/getting-started-adobe-dynamic-tag-management-part-1/)
1. [Adding A Tool to DTM Web Property](https://blogs.adobe.com/digitalmarketing/analytics/getting-started-adobe-dynamic-tag-management-part-2/)

## Configuring Target with DTM {#target-dtm}

>[!VIDEO](https://video.tv.adobe.com/v/18031/?quality=9)

1. [Best Practices for Implementing Adobe Target using Dynamic Tag Management](https://marketing.adobe.com/resources/help/en_US/target/dtm/)
1. [Adobe Target Tool](https://marketing.adobe.com/resources/help/en_US/dtm/target/adobe-target-tool.html)

## Integrating Dynamic Tag Management with Adobe Experience Manager {#aem-dtm}

>[!VIDEO](https://video.tv.adobe.com/v/18032/?quality=9)

Integrate Adobe Dynamic Tag Management with AEM so that you can use your Dynamic Tag Management web properties to track AEM sites. Dynamic Tag Management enables marketers to manage tags for collecting  data,  and distribute data across digital marketing systems. For example, use Dynamic Tag Management to collect usage data for your AEM website and distribute the data for analysis in Adobe Analytics or Adobe Target.

**Cloud Services **- Digital Marketing cloud services are the AEM mechanism to configure integrations between AEM and cloud services such as Adobe Marketing  Cloud ,  Adobe Creative Cloud or third-party cloud services. Cloud Services typically hold the parameters for connecting  with  an external service such as credentials or API endpoints. This section describes how to configure connections to DTM.

Steps to follow before integrating DTM with AEM:

1. You need to create a [web property](https://marketing.adobe.com/resources/help/en_US/dtm/#Web_Properties) that tracks the domain of your AEM site
1. The [hosting options](https://marketing.adobe.com/resources/help/en_US/dtm/gs/dtm-technical-architecture-and-hosting.html) of the web property must to configured so that you can configure AEM to access DTM libraries

## Integrating Adobe Analytics with Adobe Experience Manager {#aem-analytics}

>[!VIDEO](https://video.tv.adobe.com/v/18033/?quality=9)

Integrate SiteCatalyst and AEM so that you can track your page activity SiteCatalyst. A SiteCatalyst configuration enables AEM to authenticate with SiteCatalyst. A framework identifies the data that is sent to your SiteCatalyst report suite. The data includes page and user data that AEM components collect, link clicks, and video usage information. The framework also causes AEM to retrieve the number of page visits from SiteCatalyst.

1. [Integrating with Adobe Analytics](https://docs.adobe.com/docs/en/aem/6-2/administer/integration/marketing-cloud/sitecatalyst.html)
1. [Integrating AEM with Adobe Target and Adobe Analytics using DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html)

## Integrating Adobe Target with Adobe Experience Manager {#aem-target}

>[!VIDEO](https://video.tv.adobe.com/v/18034/?quality=9)

>[!NOTE]
>
>*Dynamic Tag Management is used load client library for Adobe Target. AEM synchronizes segments from Adobe Target*

[Integrate your AEM sites with Adobe Target](https://docs.adobe.com/docs/en/aem/6-2/administer/integration/marketing-cloud/target.html) to personalize content in your pages:Implement content targeting.Use Target audiences to create personalized experiences.Submit context data to Target when visitors interact with your pages.Track conversion rates.

>[!NOTE]
>
>When you target a component in AEM author, the component makes a series of server-side calls to Adobe Target to register the campaign, set up offers, and retrieve Adobe Target segments (if configured). No server-side calls are made from AEM publish to Adobe Target.

Integrating AEM with Adobe Target requires knowledge of Adobe Target, AEM Activities management, and AEM Audiences management. You should be familiar with the following information:

1. Adobe Target (See the [Adobe Target documentation](https://marketing.adobe.com/resources/help/en_US/target/)).
1. AEM Activities console (See [Managing Activities](https://docs.adobe.com/docs/en/aem/6-2/author/personalization/activitylib.html)).
1. AEM Audiences (See [Managing Audiences](https://docs.adobe.com/docs/en/aem/6-2/author/personalization/managing-audiences.html)).

>[!NOTE]
>
>When working with Adobe Target, the following is the maximum number of artifacts allowed within a campaign:
>
>* 50 locations
>* 2,000 experiences
>* 50 metrics
>* 50 reporting segments
>

>[!VIDEO](https://video.tv.adobe.com/v/18035/?quality=9)

## Package Installation {#package-installation}

>[!VIDEO](https://video.tv.adobe.com/v/18036/?quality=9)

## Experience Targeting using Adobe Target and Analytics (A4T) {#target-experience}

>[!VIDEO](https://video.tv.adobe.com/v/18054/?quality=9)

Author targeted content using Targeting mode of the AEM touch-optimized UI. Targeting mode and the Target component provide tools for creating content for experiences:

* Easily recognize the targeted content that is on the page. A dotted line forms a border around all targeted content. 
* Select a brand and an activity to see the experiences.Add experiences to an activity or remove experiences.
* Perform A/B testing and convert winners (Adobe Target only).
* Add offers to an experience by creating offers or using offers from a library.
* Configure goals and monitor performance.Simulate the user experience.
* For more customization, configure the Target component.

Key Terminology

* Activity - rule set defining which content is shown to which visitor
* Experiences - collection of offers, bound to an audience
* Offer - content to be shown in a location
* Audience - class of visitors defined by specific criteria
* Location - specific area on the page where content is targeted

[Target and Analytics Integration Overview](https://marketing.adobe.com/resources/help/en_US/target/a4t/c_integration.html)

[Analytics for Target Implementation](https://marketing.adobe.com/resources/help/en_US/target/a4t/c_a4timplementation.html)

## Deep Dive - Debugging the network activity {#network-activity}

>[!VIDEO](https://video.tv.adobe.com/v/18088/?quality=9)

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td>Network Activity</td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td>contexthub.kernel.js </td> 
   <td>The first include in your page header. This<br /> loads the Context Hub base library<br /> including the code for the stores. </td> 
  </tr> 
  <tr> 
   <td>satelliteLib.js </td> 
   <td>The second include in your page template.<br /> This loads the DTM library. </td> 
  </tr> 
  <tr> 
   <td>data. 
    <g class="gr_ gr_90 gr-alert gr_spell gr_inline_cards gr_run_anim ContextualSpelling ins-del multiReplace" data-gr-id="90">
      json 
    </g></td> 
   <td>This is the request that loads the data for<br /> our donation store. </td> 
  </tr> 
  <tr> 
   <td>global- 
    <g class="gr_ gr_102 gr-alert gr_spell gr_inline_cards gr_run_anim ContextualSpelling ins-del multiReplace" data-gr-id="102">
      mbox 
    </g>-request (shown as /ajax): </td> 
   <td>This is the request made by the auto-<br /> generated global 
    <g class="gr_ gr_126 gr-alert gr_gramm gr_inline_cards gr_run_anim Style multiReplace" data-gr-id="126"> 
     <g class="gr_ gr_100 gr-alert gr_spell gr_inline_cards gr_disable_anim_appear ContextualSpelling ins-del multiReplace" data-gr-id="100">
       mbox 
     </g> 
    </g></td> 
  </tr> 
  <tr> 
   <td> 
    <g class="gr_ gr_126 gr-alert gr_gramm gr_inline_cards gr_disable_anim_appear Style multiReplace" data-gr-id="126"> 
     <g class="gr_ gr_119 gr-alert gr_spell gr_inline_cards gr_disable_anim_appear ContextualSpelling ins-del multiReplace" data-gr-id="119">
       mbox 
     </g> 
    </g> requests (shown as /standard): </td> 
   <td>These are the 2 targeted locations on our<br /> page. </td> 
  </tr> 
 </tbody> 
</table>

The difference between the /ajax request for the global mbox and the /standard request for the targeted components is that we don’t expect content to be returned by the global mbox request. So we can send this as an asynchronous request that just sends the profile data required for the current user and then forget about it.

The targeted components and their mbox however are expected to return actual content to be displayed. In the lab setup we are using a synchronous request for the targeted components to make sure our page loads smoothly without any flicker. For the mbox managed by the targeted components this means that on the AEM publish instance we are using an mboxCreate call to define the mbox. But using synchronous requests can affect page load performance.

>[!NOTE]
>
>When inspecting the responses for the local  mbox  request you can see that AEM just synchs a JS snippet that takes care of loading the experience from AEM. This means the actual content stays in AEM and will be delivered from there, which allows to leverage AEMs powerful content aggregation and management  
>capabilities.

