---
title: Azure Cloud Resume Challenge
tags: [Azure Functions, Cosmos DB, HTML/CSS, JavaScript, CDN]
style: 
color: 
description: Developed a static website with a visitor counter using only serverless technologies in Azure.
---

Source: [Daniel Hinden](https://resume.hindentech.com)

## The Cloud Resume Challenge

The Cloud Resume Challenge requires that you build and host a resume, using serverless infrastructure, with a Cloud Provider of your choice. If the challenge is done correctly, it can be done at virtually no cost.

I think a pre-requisite of the challenge should be to thoroughly understand the costs of the Cloud Provider and set up budget alerts to avoid surprises. A credit card must be on file to start a cloud subscription, and making configuration errors while setting up Azure resources can be costly.

The Challenge is broken up into 5 Chunks:

Chunk 0. Certification Prep<br>
Chunk 1. Building the front-end<br>
Chunk 2. Building the API<br>
Chunk 3. Front-end / back-end integration<br>
Chunk 4. Automation (IaC, CI/CD)

## Chunk 0. Certification Prep

Chunk 0 consists of obtaining a fundamental level certification in the specific Cloud that you will use for the challenge. Luckily, I had completed most of the Azure Fundamental Certifications by the time I started the challenge, so I was able to skip this Chunk.

## Chunk 1. Building the front-end

The front-end is to be built using HTML and CSS. Since I am not a programmer by trade, I had to brush up on my coding skills. Most of it was familiar and so it didn't take long to remember enough to start working.

In order to keep the design time to a minimum, I customized an open-source HTML/CSS resume template provided by Matt Brown at https://sampleresumetemplate.net/. I updated the reset-fonts-grids.css to the most recent version available and integrated an open-source 404 page and style sheet from https://codepen.io/honeybadger2788/pen/oNzKzvy.

Once I had the website working correctly on my local machine, it was time to migrate it to the cloud. To accomplish this, the Cloud Challenge instructs that you use specific cloud services, which is meant to deconstruct the website development into its individual services. There are easier ways to host websites in Azure that automatically configure much of this for you, such as Azure App Services, but the Challenge forces you build it step-by-step to foster a deeper understanding of each of the services involved.

The website is to be hosted using an Azure Storage Account with Static Website hosting. I had already purchased a custom domain name from GoDaddy that I transferred into Azure DNS and utilized a Content Delivery Network to configure the custom domain name and add HTTPs security to the website.

After deployment, I couldn't access the CDN endpoint's webpage. The error indicated the files couldn't be found, so I had a feeling it was a permissions issue on the storage account. However, I did not want to open the storage account up for public access, so I spent some time researching storage account firewalls and best practices for this use case.

I found the most challenging aspect of Chunk 1 to be understanding the proper security configuration of setting up an Azure Storage Account with Static Hosting enabled. I wanted to be confident that my configuration followed the principle of least privilege. I ended up restricting the storage account firewall to only allow access from the Azure CDN network IP range.

I will return to this Chunk and incorporate the Developer and DevOps Mods after completing the original challenge. I had the urge to jump into these mods right away, but I also didn't want to slow down the overall momentum of the main challenge.

## Chunk 2. Building the API