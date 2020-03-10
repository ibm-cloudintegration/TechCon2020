---
title: API Led Integration and the journey to iPaaS - A Lab
toc: false
folder: master
permalink: /api_ipaas.html
summary: api docs
applies_to: [developer,administrator,consumer]
---

## Lab Overview
===============

One of the more prevelant implementation patterns out there that is driving Application and Integration Modernization is **API Led Integration**.  API Led Integration is built around the model exposing enteprise systems that are located on-premesis or within public/private/SaaS clouds using common standards like REST or GraphQL.  With this lab, you will be simulating the "day in the life" of a API developer at a Health Care Services company who has been tasked with importing integration assets and expose those assets as consumable APIs using the *Cloud Pack for Integration*.  You will be provided a pre configured CP4I cluster as well as some pre-configured integration artifacts and implement these as live integrations on the cluster and then expose those as consumable APIs.

## Cloud Pak for Integration

You will be using the *Cloud Pak for Integration* with this lab.  The Cloud Pak for Integration is one of six Cloud Paks IBM has created that provide the full spectrum of integration capabilities in a single platform that can be deployed wherever you like, in any cloud.  It is built on top of *Red Hat Open Shift* and provides the robust power and flexibility of Kubernetes that is purpose built for the enterprise.  More information on Open Shift can be found [here](https://www.openshift.com/).  The specific capabilities of the Cloud Pak for Integration are provided for you below:


### API lifecycle

Create, secure, manage, share and monetize APIs across clouds while you maintain continuous availability. Take control of your API ecosystem and drive digital business with a robust API strategy that can meet the changing needs of your users.

### Application and data integration

Integrate all of your business data and applications more quickly and easily across any cloud, from the simplest SaaS application to the most complex systems — without worrying about mismatched sources, formats or standards.

### Enterprise messaging

Simplify, accelerate and facilitate the reliable exchange of data with a flexible and security-rich messaging solution that’s trusted by some of the world’s most successful enterprises. Ensure you receive the information you need, when you need it — and receive it only once.

### Event streaming

Use Apache Kafka to deliver messages more easily and reliably and to react to events in real time. Provide more personalized customer experiences by responding to events before the moment passes.

### High-speed data transfer

Send large files and data sets virtually anywhere, reliably and at maximum speed. Accelerate collaboration and meet the demands of complex global teams, without compromising performance or security.

### Secure gateway

Create persistent, security-rich connections between your on-premises and cloud environments. Quickly set up and manage gateways, control access on a per-resource basis, configure TLS encryption and mutual authentication, and monitor all of your traffic.


## API Led Integration Basics

The basic premise of API Led Integration is based around the exposure of the valuable technical assets to innovate and reach into new areas of business, but do so in a fashion that is minimally disruptive to the enterprise, and is by its base nature secure and fast.  The primary capability within the Cloud Pak for Integration that handle this are *Application and data integration*, *enterprise messaging*, and *api lifecycle*

![](api_led1.png)



## Lab Environment

You will be provded an environment to implement the use case.  It is a pre-configured CP4I cluster that will be unique for each student.  It has instances of App Connect, API Connect and MQ that are setup for you to start implementing your use case right away.  The use cases and the steps to implement each of these use cases will be provided below.

## The Use Case

ABC Health is in the process of modernizing their integration infrastructure, and has implemented a new installation of the Cloud Pak for Integration to support their new strateging initaives around API enabling some older interfaces so they can be consumed by a wider audience.  To accomplish this, RESTful interfaces will be provided for each of the APIs using an API Gateway and managed using the API Management Capability provided by the Cloud Pak for Integration. There are a total of two APIs to implement, which will be described in the sections below.

### API 1 Provider Lookup

ABC uses a SaaS based CRM system (Salesforce) for maintaining their master data.  Since ABC Health is using the Cloud Pak for Integration, which includes the App Connect integration capability, the folks on the CRM integration team used the `App Connect Designer` to build a flow that exposed a custom object that was created for the Health Care Provider records.  You will not be creating this interface, as it has been created for you already, but you will be taking the deployable object (App Connect .bar file) and deploy it your CP4I Cluster. 

The Provider Lookup API is a REST API that extracts out providers (aka Doctors) by type.  For the scope of this lab, there are two supported types "GP" for General Practioner or "Time Lords" for when they are needed.

API Supports the GET Method Supported with Query Parameters described here:

![](model2.png)

The structure of the model used for the provider API is here:

![](model1.png)

### API 2 Invoice Processing

ABC is looking to automate the processing of invoices from their respective partners using a standard mechanism that is REST based, and plugs in neatly into their architecture.  This interface is exposed via a PUT Method that will receive in an invoice in JSON format coming in externally, whether it be from mobile, web or otherwise.  Once the invoice is received it will be put to queue (via MQ) for processing on the back end.  For this lab, the API covers the put to queue only.

This flow was created also by the Integration Team using the `App Connect Toolkit`.  Version 11 is used in the Cloud Pak for Integration and has been provided as a bar file.  You will deploy this bar file like Provider Lookup, but the parameters you use will be different

## Implementation of the APIs on the Cloud Pak for Integration

1. Your instructor will provide the information how to access your lab environments.
2. Once you have access to your environment, gog into your provided demo environment by selecting the "Developer" Machine from the list of machines
3. When the developer machine comes up, you can login with the credentials of `ibmuser` and the password of `passw0rd`.
4. It will drop you to the desktop of the developer machine.  All of the requisite applications you need are there.  This includes the Terminal and Web Browser and the Advanced REST Client.
5. Double Click on the `Terminal` application and it will take you to the command line.
6. Execute this command to do a clone of the git repository
```
git clone https://github.com/ibm-cloudintegration/TechCon2020
```

7. kjkjkjk

