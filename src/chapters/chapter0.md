## Introduction

Welcome to the Speech Workshop!

### About the Speech Workshop

The Speech Workshop is a free one-day training event on Azure, from the community to the community. 

The format for the workshop is a brief presentation, followed by hands-on and guided labs. 

Your speakers include:

* [Mike Branstein](https://twitter.com/mikebranstein)
    * [KiZAN Technologies](http://kizan.com)
    * [Brosteins](https://brosteins.com)

### Getting Started

To get started you'll need the following pre-requisites. Please take a few moments to ensure everything is installed and configured.

* Microsoft Windows PC or Mac or Linux. Just have a laptop.
* [Azure Subscription](https://azure.microsoft.com) (Trial is ok, or an Azure account linked to a Visual Studio subscription or MSDN account. See later sections of this chapter to create a free trial account or activate your Visual Studio subscription)

### What You're Building

Azure is big. Really big. Too big to talk about all things Azure in a single day. 

We've assembled an exciting workshop to introduce you to several Azure services that cloud developers should know about:
* [Web app](https://azure.microsoft.com/en-us/services/app-service/web/)
* [Cognitive Services](https://www.microsoft.com/cognitive-services) API for [customized speech to text](https://azure.microsoft.com/en-us/services/cognitive-services/speech-to-text/)
* [Cognitive Services](https://www.microsoft.com/cognitive-services) API for [Language Understanding (LUIS)](https://azure.microsoft.com/en-us/services/cognitive-services/language-understanding-intelligent-service/)

In this workshop, you’ll learn how to integrate Azure’s customizable speech recognition, text analytics, and intent analysis APIs into an Azure-hosted app. You’ll start by learning about the Speech to Text Service, a speech recognition API that can be trained to filter out background noise and recognize obscure words and phrases. After training the speech recognition model, you’ll integrate it into an Azure-hosted web app to recognize real-time speech. Finally, you’ll integrate and train the Language Understanding and Intelligence Service (LUIS) to analyze the intent of speech phrases you generate. With the intent identified, your app will be able to respond in real time.

#### Key concepts and takeaways

* Navigating the Azure portal
* Using Azure Resource Groups to manage multiple Azure services
* Deploying a web app to Azure web app service
* Developing language and acoustic models for the Speech to Text Service
* Deploying a customized speech recognition API
* Developing intent models for the Language Understanding (LUIS) service
* Deploying a customized LUIS endpoint
* Integrating speech recognition and intent analysis into an application

### Agenda

* Chapter 0: Introduction
* Chapter 1: Getting Started in Azure
* Chapter 2: Introduction to the Speech to Text Service
* Chapter 3: Building Speech to Text Service data sets 
* Chapter 4: Speech to Text Service Models
* Chapter 5: Deploying Speech to Text Service Endpoints
* Chapter 6: Introduction to Language Understanding (LUIS)
* Chapter 7: Building a LUIS App
* Chapter 8: Publishing and Testing LUIS Endpoints
* Chapter 9: Integrating LUIS into Your App

### Materials

You can find additional lab materials and presentation content at the locations below:

* Presentation: [https://github.com/mikebranstein/speech-workshop](https://github.com/mikebranstein/speech-workshop)
* Source code for the code used in this guide: [https://github.com/mikebranstein/speech-workshop](https://github.com/mikebranstein/speech-workshop)
* This guide: [https://github.com/mikebranstein/speech-workshop-instructions](https://github.com/mikebranstein/speech-workshop-instructions/)

### Creating a Trial Azure Subscription

> **If you already have an Azure account** 
>
> If you have an Azure account already, you can skip this section. If you have a Visual Studio subscription (formerly known as an MSDN account), you get free Azure dollars every month. Check out the next section for activating these benefits.

There are several ways to get an Azure subscription, such as the free trial subscription, the pay-as-you-go subscription, which has no minimums or commitments and you can cancel any time; Enterprise agreement subscriptions, or you can buy one from a Microsoft retailer. In exercise, you'll create a free trial subscription.

<h4 class="exercise-start">
    <b>Exercise</b>: Create a Free Trial Subscription
</h4>

Browse to the following page http://azure.microsoft.com/en-us/pricing/free-trial/ to obtain a free trial account.

Click *Start free*.

Enter the credentials for the Microsoft account that you want to use. You will be redirected to the Sign up page.

> **Note** 
>
> Some of the following sections could be omitted in the Sign up process, if you recently verified your Microsoft account.

Enter your personal information in the About you section. If you have previously loaded this info in your Microsoft Account, it will be automatically populated.

<img src="images/chapter0/sign-up.png" class="img-medium" />

In the *Verify by phone* section, enter your mobile phone number, and click *Send text message*.

<img src="images/chapter0/send-text-message.png" class="img-medium" />

When you receive the verification code, enter it in the corresponding box, and click *Verify code*.

<img src="images/chapter0/verify-code.png" class="img-medium" />

After a few seconds, the *Verification by card* section will refresh. Fill in the Payment information form. 

> **A Note about your Credit Card** 
>
> Your credit card will not be billed, unless you remove the spending limits. If you run out of credit, your services will be shut down unless you choose to be billed.

<img src="images/chapter0/verify-by-card.png" class="img-medium" />

In the *Agreement* section, check the *I agree to the subscription Agreement*, *offer details*, and *privacy statement* option, and click *Sign up*.

Your free subscription will be set up, and after a while, you can start using it. Notice that you will be informed when the subscription expires.

<img src="images/chapter0/agreement.png" class="img-medium" />

Your free trial will expire in 29 days from it's creation.

<img src="images/chapter0/expiration.png" class="img-medium" />

<div class="exercise-end"></div>

### Activating Visual Studio Subscription Benefits

If you happen to be a Visual Studio subscriber (formerly known as MSDN) you can activate your Azure Visual Studio subscription benefits. It is no charge, you can use your MSDN software in the cloud, and most importantly you get up to $150 in Azure credits every month. You can also get 33% discount in Virtual Machines and much more.

<h4 class="exercise-start">
    <b>Exercise</b>: Activate Visual Studio Subscription Benefits
</h4>

To active the Visual Studio subscription benefits, browse to the following URL: [http://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits-details/](http://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits-details/)

Scroll down to see the full list of benefits you will get for being a MSDN member. There is even a FAQ section you can read.

Click *Activate* to activate the benefits.

<img src="images/chapter0/activate.png" class="img-medium" />

You will need to enter your Microsoft account credentials to verify the subscription and complete the activation steps.

<div class="exercise-end"></div>

### Preparing your Azure environment

You might be wondering how you can participate in a cloud development workshop and not need Visual Studio installed. Am I right? 

Thanks to the Azure Resource Manager and some nifty templates I put together, we're going to provision a virtual machine (VM) with Visual Studio installed in your Azure subscription. From that point forward, you can work from the VM. 

It takes about 10 minutes to get the VM deployed to your subscription, so let's get started!

<h4 class="exercise-start">
    <b>Exercise</b>: Provisioning a Visual Studio Community VM in your Azure Subscription
</h4>

Start by clicking the *Deploy to Azure* button below.

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmikebranstein%2Fvscommunity-workshop-vm%2Fmaster%2Ftemplate.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png" class="img-override" /></a>

This opens the Azure portal in a new tab of your browser. If you're prompted to sign in, do so. 

When the page loads, you'll see this custom deployment page:

<img src="images/chapter0/custom-deployment.png" class="img-override" />

#### Under *Basics*, select/enter the following
- Subscription: *your Azure subscription*
- Resource group: *Create new*
- Resource group name: *workshop-vm*, or some other name that's easy to remember
- Location: *East US*

> **Resource Groups** 
>
> Formally, resource groups provide a way to monitor, control access, provision and manage billing for collections of assets that are required to run an application, or used by a client or company department. Informally, think of resource groups like a file system folder, but instead of holding files and other folders, resource groups hold azure objects like storage accounts, web apps, functions, etc.

#### Under *Settings*, enter
- Virtual Machine Name: *workshop-vm*, or some other name that is less than 15 characters long, and no special characters
- Admin Username: *your first name*, or some other username without spaces
- Admin Password: *P@ssW0rd1234*, or another 12-character password with upper, lower, numbers, and a special character 

> **WARNING** 
>
> Do not forget your username and password. Write it down for today. 

#### Approving the "Purchase"

Scroll down to the bottom of the page and click two boxes:
1. I agree to the terms and conditions stated above
2. Pin to dashboard

Press the *Purchase* button.

#### Deploying the VM

After a few moments, the deployment of your VM will begin, and you'll see a status notification in the upper right:

<img src="images/chapter0/deployment-start1.png" class="img-override" />

...and a deployment tile on your dashboard:

<img src="images/chapter0/deployment-start2.png" class="img-override" />

Now, wait for about 10 minutes and your virtual machine will be deployed and ready to use.

<div class="exercise-end"></div>

That's it for the pre-requisites for today's workshop. Wait until your VM is created, and we'll be getting started soon!

