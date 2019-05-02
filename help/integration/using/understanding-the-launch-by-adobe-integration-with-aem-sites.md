---
title: Understanding the Launch by Adobe Integration with AEM Sites
seo-title: Understanding the Launch by Adobe Integration with AEM Sites
description: Technical walk-through of of how to configure the AEM 6.4 integration with Launch by Adobe. This integration allows customer to pull the Launch "embed codes" and related JavaScript libraries into AEM Sites.
seo-description: Technical walk-through of of how to configure the AEM 6.4 integration with Launch by Adobe. This integration allows customer to pull the Launch "embed codes" and related JavaScript libraries into AEM Sites.
page-status-flag: never-activated
uuid: d0310adc-47e5-4607-bd9c-b03fa70d26b3
contentOwner: dwright
discoiquuid: 801754e2-9fbc-433f-96f8-414ec573ab1b
index: y
internal: n
snippet: y
---

# Understanding the Launch by Adobe Integration with AEM Sites{#understanding-the-launch-by-adobe-integration-with-aem-sites}

## Overview {#overview}

>[!VIDEO](//video.tv.adobe.com/v/21982/)

Launch is Adobe's next-generation tag management platform and the best way to deploy Adobe Analytics, Target, Audience Manager, Experience Cloud ID Service, and all of their 3rd party marketing solutions using Launch by Adobe.

The integration allows for the self-hosting of the Launch JavaScript libraries which gives the customer maximum control over their code, which is especially important for financial services customers. Alternatively, customers can use this integration to host their Launch libraries on Adobe's Akamai instance.

## Set up the Integration {#set-up-the-integration}

These three videos explain everything you need to know to successfully implement the integration, from creating a property in Launch, connecting Adobe IO to AEM, and configuring the Launch Cloud Service in AEM to finally pull in the embed codes and JavaScript libraries.

### Step 1: Configure the Launch Property {#launch}

>[!VIDEO](//video.tv.adobe.com/v/21984/)

In this step we will configure a Launch property with the bare-minimum configuration needed to set up the rest of the integration. More information about using Launch can be found in the [Adobe Launch Videos,](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/videos.html) [Help Documentation](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/) and [Launch Reference Architectures landing page](https://helpx.adobe.com/experience-manager/kt/integration/using/launch-reference-architecture-guides.html).

>[!NOTE]
>
>Full rights in Adobe Launch are required to complete the steps in this video.

### Step 2: Connect Adobe IO and Adobe Experience Manager {#adobeio}

>[!VIDEO](//video.tv.adobe.com/v/21983/)

In this step, the Launch Integration will be configured in Adobe I/O and connected to AEM.

>[!NOTE]
>
>System Administrator rights in the Experience Cloud organization and AEM admin rights are required to configure the Adobe IO integration and set up the IMS Configuration.

### Step 3: Configure the Launch Cloud Service in Adobe Experience Manager {#step-configure-the-launch-cloud-service-in-adobe-experience-manager}

cloudservice

>[!VIDEO](//video.tv.adobe.com/v/21985/)

In the final step, the Launch Cloud Configuration will be set up and the correct Launch property will be applied to the AEM site.

>[!NOTE]
>
>Admin rights in AEM are required to configure the Launch Cloud Service.

