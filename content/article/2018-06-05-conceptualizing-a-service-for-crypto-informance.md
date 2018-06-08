---
title: "Conceptualizing a Simple Service for Crypto & Stock Market Informance"
date: 2018-06-05T23:17:26-04:00
draft: false

featuredImage: "/images/conceptualizing/dashboard-v1.png"
categories: ["product development", "software", "cryptocurrency", "design"]
tags: ["product development", "software", "cryptocurrency"]
author: "Nisarga Patel"
twitter:
  card: "summary"
  site: "@nphacker"
  title: "Conceptualizing a Simple Service for Crypto & Stock Market Informance"
  description: "Often times I have ideas for different types of products and services, many times I usually just write these ideas down to come back to them at a different date - this time I wanted to try something different. In this post I'll be conceptualizing one of these ideas and how it would look like as product from both a backend and frontend design perspective."
  image: "https://nisarga.io/images/conceptualizing/dashboard-v1.png"
---

Often times I have ideas for different types of products and services, many times I usually just write these ideas down to come back to them at a different date - this time I wanted to try something different. In this post I'll be conceptualizing one of these ideas and how it would look like as product from both a backend and frontend design perspective.

##### The idea

This application is essentially a general purpose cryptocurrency and stock market informance service i.e. a system dedicated to giving custom alerts regarding different happenings in the markets via text or email.

##### The backend design
<img src="/images/conceptualizing/service.png" width="300" />

The backend service design for the core functionality would be fairly simple, the endpoints shown in the diagrams would communicate with third party APIs in order to source the info that will eventually be sent out via text or email. In the diagram I have listed [Twilio](https://www.twilio.com/) as a possible way to send out texts programmatically, emails can be sent out via SMTP or using a third party service such as [SendGrid](https://sendgrid.com/).

In this service design there is also caching of data received from third party endpoints, many APIs have rate limiting i.e. you may be able to only ping them every X minutes, therefore caching would ensure that I'm not pinging a third party API constantly and would also increase the number of total requests a user can be served. 

<img src="/images/conceptualizing/thirdparty.png" width="300" />

Custom user-defined 3rd party data integrations may also be a feature of this service. In this case a user would be able to specify a custom endpoint and customize how that data will be parsed and sent out.

##### Choosing a name for this service

This hypothetical application's goal would be to inform and therefore give others a better perspective in regards to markets. Therefore I chose the word *drishti* which means "perspective or focused gaze" in Sanskrit.

##### Frontend design

<img src="/images/conceptualizing/frontpage-v1.png" alt="Frontpage" width="500" />

For the frontend design I decided to use [Sketch](https://www.sketchapp.com/) and make a quick design for the frontpage and the main dashboard. In this first iteration design I kept it relatively simple for the frontpage, spacing out UI components. The logo I conceptualized as an eye first and that eventually became a planet/eye shape.

<img src="/images/conceptualizing/dashboard-v1.png" alt="Dashboard" width="500" />

Following the same design principles from the frontpage I also designed the dashboard. The goal of the dashboard is to make it easy for users to specify custom alerts. In the create custom alert form users would ideally be able to specify the email or phone number for the alert in a modal that would appear upon pressing the corresponding button. 

##### Why?

I chose to conceptualize this simple service as an exercise in both backend and frontend design. If you are interested in seeing this service created or know of any similar apps that perform the same or similar functionality feel free to comment below. In the future I plan on writing more posts on conceptualizing the design of different products in short form style.

Thanks!