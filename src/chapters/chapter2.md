## Introduction to the Speech to Text Service

In this chapter you'll learn about the Speech to Text Service, how to provision one in the Azure Portal, and how to link your subscription to the Speech to Text Service portal.

> **Abbreviation** 
>
> To save some time, you may see me refer to the Speech to Text Service as STT.

### Overview

The Speech to Text Service enables you to create a customized speech-to-text platform that meets the needs of your business. With the service, you create customized language models and acoustic models tailored to your application and your users. By uploading your specific speech and/or text data to the Speech to Text Service, you can create custom models that can be used in conjunction with Microsoft’s existing state-of-the-art speech models. With these capabilities, you're able to filter out common background noise, adjust for localized dialects, and train the speech service to recognize non-standard/obscure words and phrases (like "Pokemon", scientific terms, and technical jargon).

For example, if you’re adding voice interaction to a mobile phone, tablet or PC app, you can create a custom language model that can be combined with Microsoft’s acoustic model to create a speech-to-text endpoint designed especially for your app. If your application is designed for use in a particular environment or by a particular user population, you can also create and deploy a custom acoustic model with this service.

#### How do speech recognition systems work?

Before you get started, it's important to understand how speech recognition systems work.

Speech recognition systems are composed of several components that work together. Two of the most important components are the acoustic model and the language model.

> **Acoustic Model**
>
> The acoustic model is a classifier that labels short fragments of audio into one of a number of phonemes, or sound units, in a given language. For example, the word “speech” is comprised of four phonemes “s p iy ch”. These classifications are made on the order of 100 times per second.

> **Phoneme**
>
> In short, a sound unit. Any of the perceptually distinct units of sound in a specified language that distinguish one word from another, for example p, b, d, and t in the English words pad, pat, bad, and bat.

> **Language Model**
>
> The language model is a probability distribution over sequences of words. The language model helps the system decide among sequences of words that sound similar, based on the likelihood of the word sequences themselves. For example, “recognize speech” and “wreck a nice beach” sound alike but the first hypothesis is far more likely to occur, and therefore will be assigned a higher score by the language model.

Both the acoustic and language models are statistical models learned from training data. As a result, they perform best when the speech they encounter when used in applications is similar to the data observed during training. The acoustic and language models in the Microsoft Speech-To-Text engine have been trained on an enormous collection of speech and text and provide state-of-the-art performance for the most common usage scenarios, such as interacting with Cortana on your smart phone, tablet or PC, searching the web by voice or dictating text messages to a friend.

> **Credits**
>
> This section was borrowed from Microsoft's [official documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/overview). Thank you!

#### Using the Speech to Text Service, Acoustic Models, and Language Models

Throughout the next several chapters, you'll be building acoustic and language models. Don't worry if you don't understand everything right now, because you'll be learning as you go.

> **Bing Speech API and Custom Speech Service**
>
> Microsoft has various other speech-to-text services in Azure. The first is called the Bing Speech API, and the second Custom Speech Service. The Bing Speech API is like the Speech to Text Service, but it cannot be customized. I like to think of the Bing Speech API as a v1 product.
>
> The Custom Speech Service was their first version of Microsoft's customized speech-to-text platform. As of the 2018 //BUILD conference, the Custom Speech Service was enhanced and renamed to the Speech to Text service. From time to time, you may see Custom Speech Service used interchangeably with Speech to Text service.
>
> The Bing Speech API and Speech to Text Service are highly capable, but when I need to account for background noise, custom words, etc. I choose the Speech to Text Service.

### Provisioning in Azure

Now that you know what the Speech to Text Service can do, let's start using it! You'll start by creating a Speech to Text Service instance in the Azure portal. 

<h4 class="exercise-start">
    <b>Exercise</b>: Creating a Speech to Text Service Instance
</h4>

Start by jumping back to the Azure portal, and create a new resource by clicking the *Create a resource* button.

Search for *Custom Speech*:

<img src="images/chapter2/css-search.png" class="img-override" />

In the of search results, select *Custom Speech (preview)*:

<img src="images/chapter2/css-search-results.png" class="img-override" />

Fill out the required parameters as you create an instance:
- Name: *workshop-css*, or something similar
- Subscription
- Location: *West US*
- Pricing tier: *F0*
- Resource group: the resource group you created earlier

<img src="images/chapter2/css-create.png" class="img-override" />

> **West US Location**
>
> Normally, I recommend you keep resources in the same region, but the Speech to Text Service is in preview right now, so it's only available in West US.

When the Speech to Text Service instance is provisioned, it will appear in your resource group:

<img src="images/chapter2/css-resource-group.png" class="img-override" />

The final step is to navigate to the Speech to Text Service instance by clicking on it. 

Locate the *Keys* area and take note of *KEY 1*:

<img src="images/chapter2/css-keys.png" class="img-override" />

You'll need this key in the next step, so don't forget it.

This concludes the exercise. 

<div class="exercise-end"></div>

### Linking your Subscription on the Speech To Text Service Web Portal

There's not much you can do with the Speech to Text Service in the Azure portal because the service is still in preview. Instead, a separate portal exists to customize and work with the service. In the next section, you'll be introduced to the Speech to Text Service portal.

<h4 class="exercise-start">
    <b>Exercise</b>: Linking your STT subscription to the STT portal
</h4>

Start by navigating to the STT web portal at <a href="https://cris.ai" target="_blank">https://cris.ai</a>.

Click the *Sign In* link in the upper right and sign in with your Azure portal subscription login.

After logging in, click on your name the upper right, and select the *Subscriptions* option below it:

<img src="images/chapter2/portal-sub.png" class="img-override" />

#### Subscriptions

The *Subscriptions* page shows all of your connected STT subscriptions. 

<img src="images/chapter2/portal-sub-page.png" class="img-override" />

Click the *Connect existing subscription* button. Add the STT subscription you just created in the Azure portal. Give it a name and enter *KEY 1* from the Azure portal.

<img src="images/chapter2/sub-add.png" class="img-override" />

You should see the subscription appear on the subscriptions page.

This concludes the exercise. 

<div class="exercise-end"></div>

That's it. In the next chapter, you'll start to use the STT by creating various data sets for training and testing.
