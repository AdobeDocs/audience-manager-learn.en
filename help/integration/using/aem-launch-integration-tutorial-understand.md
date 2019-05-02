---
title: Understanding AEM Integration with Launch By Adobe, Analytics and Target
seo-title: Understanding AEM Integration with Launch By Adobe, Analytics and Target
description: Technical walkthrough integrating AEM 6.4 with Adobe Analytics, Adobe Target, and Launch By Adobe to build, deliver and measure personalized experiences. Also, examine how to leverage Context Hub to use your data for personalizing experiences and AEM Content Insights to visualize content KPIs. 
seo-description: Technical walkthrough integrating AEM 6.4 with Adobe Analytics, Adobe Target, and Launch By Adobe to build, deliver and measure personalized experiences. Also, examine how to leverage Context Hub to use your data for personalizing experiences and AEM Content Insights to visualize content KPIs. 
page-status-flag: never-activated
uuid: ff110f3e-89e8-419e-a7fa-60a8bc2eb3b8
products: SG_ANALYTICS
products: SG_TARGET
topic-tags: DTM
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: tagmanager
discoiquuid: 8921ed21-791b-4d92-9a6e-888ef3960841
targetaudience: target-audience advanced
index: y
internal: n
snippet: y
---

# Understanding AEM Integration with Launch By Adobe, Analytics and Target{#understanding-aem-integration-with-launch-by-adobe-analytics-and-target}

## Scenario {#scenario}

>[!VIDEO](https://video.tv.adobe.com/v/18045/?quality=9)

![Architecture Overview](assets/diagram.png) 
**Adobe Experience Manager** - Adobe Experience Manager (AEM) is a comprehensive content management solution for building website and forms. And it makes it easy to manage your marketing content and assets.  

**Adobe Target **- Adobe Target (Target) is a personalization solution that makes it easy to identify your best content through tests that are easy to execute. So you can deliver the right experience to the right customer.  

**Adobe Analytics **- Adobe Analytics (Analytics) is the industry-leading solution for applying real-time analytics and detailed segmentation across all of your marketing channels. Use it to discover high-value audiences and power customer intelligence for your business.  

**Tag Manager** - Launch by Adobe is the next-generation Tag Management platform. Each of the following guides provides best practices and instructions on how to implement Adobe Analytics, Adobe Target, Adobe Audience Manager, and the Experience Cloud ID Service using Launch in a variety of web architectures. Start with the Basic Setup guide and then choose your specific architecture.  

**Core Services - Profiles and Audiences ** - Profiles and Audiences core service gives you a complete and actionable view of your customers. It provides a common ID service (Marketing Cloud ID Service) to   
identify audiences across Adobe solutions so insights are taken from one solution can be applied in another.  

By using these products together, you can build engaging solutions that let you deliver the best content to a given  web site  visitor. That is, you display content from AEM DAM that meets the interest of the visitor. This development article walks you through how to build a solution that uses AEM, Analytics, Target, and Launch By Adobe.  

## Accessing Launch By Adobe within Adobe Marketing Cloud {#dynamictagmanagement-cloud}

>[!VIDEO](https://video.tv.adobe.com/v/22220/)

Launch By Adobe allows marketers to manage tags, distribute data, and simplifies tag management.

Data Elements, Extensions, Rules and the Publishing process are the main aspects of Launch which you will use on a day-to-day basis.

** [Data Elements](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/data-elements.html) **- Collect, organize, and deliver data across web-based marketing and advertising technology..

** [Extensions](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/extensions.html) - **“Tools” in DTM have been replaced by “Extensions”. While on the surface they will feel very similar, there are some subtle, yet extremely powerful differences to be aware of.

Launch is an open and extendable platform. Whereas the Activation team built all of the Adobe and 3-party Tools for DTM, Launch allows the Adobe solution teams and 3 parties to *build their own extensions*. You can even create your own extensions and share them to the extension marketplace.

Think of Launch as the OS and extensions as the App Store. Extensions on the Launch platform allow Launch to evolve with the digital marketing landscape without Adobe bottlenecks.

** [Rules](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/rules.html) - **Create robust rules that combine multiple events, sequenced in the way that you determine using if/then logic with conditions and exceptions. Extensions provide options for:

* Events
* Conditions
* Exceptions
* Actions

The rule builder includes real-time error checking and syntax highlighting for your custom code.

When the criteria outlined in your rules are met and conditions are satisfied, the actions you define are executed in order.

** [Publishing](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/c_publishing.html)** - The publishing process enables teams to publish code to pages. Different people can create an implementation, approve it, and publish it to your pages.

* Changes to your code are encapsulated within libraries you define 
* You specify where and when you want your code deployed 
* Multiple libraries can be built in parallel by different teams 
* Unlimited development environments 
* Deliberate, permissioned process for merging libraries together

**Open APIs** - Automate implementations of individual technologies, or a group of technologies.

* Launch interacts with the Reactor APIs 
* Deployments can be automated through APIs 
* Integrate the Launch APIs with your own internal systems 
* You can build your own user interface, if desired

**Light, Modular Container tag** - The Launch container tag is 60% lighter than DTM and 40% lighter than Google Tag Manager. The content of your container is minified, including your custom code. Everything is modular. If you don't need an item, it is not included in your library. The result is an implementation that is fast and compact. See [Minification](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/build.html#concept_0C31AA97343F4845BA799F751BADD1AA).

1. [Launch By Adobe Overview](https://www.adobe.com/enterprise/cloud-platform/launch/new-era-of-tag-management.html)
1. [Launch By Adobe Documentation](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/)
1. [Getting Started with Launch By Adobe Videos](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/videos.html)
1. [Launch Adminstration](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/administration.html)

## Configuring Data Elements and Rules within Launch By Adobe  {#analytics-dtm}

>[!VIDEO](https://video.tv.adobe.com/v/22219/)

1. [Adding a Data Elements](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/data-elements.html)
1. [Creating a Rule](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/rules.html)
1. [Adding an Extension](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/extensions.html)

### Adding Adobe Target and Adobe Analytics Extensions to Launch {#target-dtm}

1. [Configuring Adobe Target Extension](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/c_extension-target.html)
1. [Adobe Analytics Extension](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/c_extension-analytics.html)
1. [Configuring Experience Cloud Extension](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/c_extension-mcid.html)

## Integrating Launch By Adobe with Adobe Experience Manager {#aem-dtm}

Integrate Launch By Adobe with AEM so that you can use your Launch web properties to track AEM sites. Launch enables marketers to manage tags for collecting  data,  and distribute data across digital marketing systems. For example, use Launch to collect usage data for your AEM website and distribute the data for analysis in Adobe Analytics or Adobe Target.

**Cloud Services **- Digital Marketing cloud services are the AEM mechanism to configure integrations between AEM and cloud services such as Adobe Marketing  Cloud ,  Adobe Creative Cloud or third-party cloud services. Cloud Services typically hold the parameters for connecting  with  an external service such as credentials or API endpoints. This section describes how to configure connections to Launch.

Launch is Adobe's next-generation tag management platform and the best way to deploy Adobe Analytics, Target, Audience Manager, Experience Cloud ID Service, and all of their 3rd party marketing solutions using Launch by Adobe.

The integration allows for the self-hosting of the Launch JavaScript libraries which gives the customer maximum control over their code, which is especially important for financial services customers. Alternatively, customers can use this integration to host their Launch libraries on Adobe's Akamai instance.

Steps to follow before integrating Launch with AEM:

1. [Understanding the Launch by Adobe Integration with AEM Sites](https://helpx.adobe.com/experience-manager/kt/integration/using/adobe-launch-integration-tutorial-understand.html)

## Integrating Adobe Analytics with Adobe Experience Manager {#aem-analytics}

>[!VIDEO](https://video.tv.adobe.com/v/22213/?quality=9)

Integrate SiteCatalyst and AEM so that you can track your page activity SiteCatalyst. A SiteCatalyst configuration enables AEM to authenticate with SiteCatalyst. A framework identifies the data that is sent to your SiteCatalyst report suite. The data includes page and user data that AEM components collect, link clicks, and video usage information. The framework also causes AEM to retrieve the number of page visits from SiteCatalyst.

1. [Integrating with Adobe Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/adobeanalytics.html)
1. Integrating Adobe Analytics with AEM using Launch

## Integrating Adobe Target with Adobe Experience Manager {#aem-target}

>[!VIDEO](https://video.tv.adobe.com/v/22218/?quality=9)

>[!NOTE]
>
>*Launch By Adobe is used load client library for Adobe Target. AEM synchronizes segments from Adobe Target*

[Integrate your AEM sites with Adobe Target](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/target.html) to personalize content in your pages:Implement content targeting.Use Target audiences to create personalized experiences.Submit context data to Target when visitors interact with your pages.Track conversion rates.

>[!NOTE]
>
>When you target a component in AEM author, the component makes a series of server-side calls to Adobe Target to register the campaign, set up offers, and retrieve Adobe Target segments (if configured). No server-side calls are made from AEM publish to Adobe Target.

Integrating AEM with Adobe Target requires knowledge of Adobe Target, AEM Activities management, and AEM Audiences management. You should be familiar with the following information:

1. Adobe Target (See the [Adobe Target documentation](https://marketing.adobe.com/resources/help/en_US/target/)).
1. AEM Activities console (See [Managing Activities](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/activitylib.html)).
1. AEM Audiences (See [Managing Audiences](https://helpx.adobe.com/experience-manager/6-4/sites/authoring/using/managing-audiences.html)).

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

>[!VIDEO](https://video.tv.adobe.com/v/22217/)

## Experience Targeting using Adobe Target and Analytics (A4T) {#target-experience}

>[!VIDEO](https://video.tv.adobe.com/v/22214/?quality=9)

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

[Target and Analytics Integration Overview](https://marketing.adobe.com/resources/help/en_US/target/a4t/r_a4t-faq.html)

[Analytics for Target Implementation](https://marketing.adobe.com/resources/help/en_US/target/a4t/c_a4timplementation.html)

## Deep Dive - Debugging the network activity {#network-activity}

>[!VIDEO](https://video.tv.adobe.com/v/22216/?quality=9)

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
   <td>The second include in your page template.<br /> This loads the Launch library. </td> 
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

## Useful Tools {#tools}

### Experience Cloud Debugger Chrome Extension {#experience-cloud-debugger-chrome-extension}

The Experience Cloud Debugger is a Chrome Extension built by an Adobe.com developer. It contains basic debugging tools for all SaaS-based Experience Cloud Solutions, in addition to some very powerful and unique Target capabilities built by the Target Engineering Team. Add the extension from here:  
[https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj)

### Launch Command Chrome Extension {#launch-command-chrome-extension}

This is a new Extension built by the Launch BU to switch embed codes. Add the extension from here:

[https://chrome.google.com/webstore/detail/launch-command/nkjhamgjeocefocmpbcjfmohkjgildki](https://chrome.google.com/webstore/detail/launch-command/nkjhamgjeocefocmpbcjfmohkjgildki)

### Browser Developer Tools {#browser-developer-tools}

The tools above are both Chrome extensions. If you prefer to use a different browser, make sure you have Developer Tools installed (some browsers require a separate download).

>[!MORE_LIKE_THIS]
>
>* [Set up Adobe Analytics Activity Map with AEM Sites](https://helpx.adobe.com/experience-manager/kt/sites/using/activity-map-feature-video-setup.html)
>* [Understanding AEM Integration with DTM, Analytics and Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-dtm-integration-tutorial-understand.html)
>* [Understanding AEM Integration with Launch By Adobe, Analytics and Target](https://helpx.adobe.com/experience-manager/kt/integration/using/aem-launch-integration-tutorial-understand.html)
