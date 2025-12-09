---
title: "FotMob delivers near real-time football updates to millions of fans with AWS"
date: 2025-03-25
lastmod: 2025-03-25
author: "Emily McKinzie"
categories: ["AWS for Games Blog"]
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

by Emily McKinzie | on 25 MAR 2025 | in [Amazon Aurora](https://aws.amazon.com/blogs/gametech/category/database/amazon-aurora/), [Amazon Bedrock](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/amazon-machine-learning/amazon-bedrock/), [Amazon CloudFront](https://aws.amazon.com/blogs/gametech/category/networking-content-delivery/amazon-cloudfront/), [Amazon EC2](https://aws.amazon.com/blogs/gametech/category/compute/amazon-ec2/),[Amazon Elastic Kubernetes Service](https://aws.amazon.com/blogs/gametech/category/compute/amazon-kubernetes-service/), [Amazon ElastiCache](https://aws.amazon.com/blogs/gametech/category/database/amazon-elasticache/), [Amazon Machine Learning](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/amazon-machine-learning/), [Amazon Simple Storage Service (S3)](https://aws.amazon.com/blogs/gametech/category/storage/amazon-simple-storage-services-s3/), [Artificial Intelligence](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/), [AWS Lambdak](https://aws.amazon.com/blogs/gametech/category/compute/aws-lambda/),[Compute](https://aws.amazon.com/blogs/gametech/category/compute/), [Database](https://aws.amazon.com/blogs/gametech/category/database/), [Game Development](https://aws.amazon.com/blogs/gametech/category/game-development/), [Games](https://aws.amazon.com/blogs/gametech/category/industries/games/), [Generative AI](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/generative-ai/), [Industries](https://aws.amazon.com/blogs/gametech/category/artificial-intelligence/generative-ai/), [Networking & Content Delivery](https://aws.amazon.com/blogs/gametech/category/networking-content-delivery/), [Storage](https://aws.amazon.com/blogs/gametech/category/storage/)


The world’s most-watched sport, professional football (soccer) attracts a global fanbase of [five billion](https://publications.fifa.com/en/vision-report-2021/the-football-landscape/) people. With hundreds of thousands of players participating in matches across the world, the sport also generates staggering amounts of data, from goals to saves, assists, and beyond. In today’s connected world, fans want real-time access to all the match, player, and team stats, driving demand for matchday apps like [FotMob](https://www.fotmob.com/). Home to over 17 million users, FotMob delivers live football updates and news spanning 500 international leagues nearly all day, every day.

With its infrastructure built on [Amazon Web Services](https://aws.amazon.com/) (AWS), the Norwegian company behind the app can scale and innovate to continuously elevate the fan experience. Recently, the team developed an in-house push notification system that not only enhances near real-time updates for fans but also saves over $130,000 USD annually.

These savings will be paramount to developing new engaging app features, as the organization aims to double its user base in the coming years. Recognizing personalization will be key to this growth strategy, the FotMob team is also experimenting with generative AI-powered team summaries built with [Amazon Bedrock](https://aws.amazon.com/bedrock/).

## From humble beginnings to top-rated matchday app

FotMob started out in 2004 as a passion project led by founders and brothers Christer and Tommy Nordvik. The two worked evenings and weekends, juggling full-time jobs and family responsibilities, to build the company from the ground up. However, it wasn’t until 2008, when smartphones began popularizing, that FotMob took on a life of its own. Since then, the team has extended its offering to include more in-depth match statistics, personalized notifications, and team and match news summaries spanning multiple regions.

![Blog Image](/images/logo-blog/bog1.jpg)

“We built the app to cater to all user types, whether the casual fan who wants to check in on scores or the more passionate ones who want to delve deep into the data. Using machine learning, we’ve been able to transform stats from data providers, like Stats Perform, into easy-to-digest visuals, like a momentum graph or player rating system,” explained FotMob Founder Christer Nordvik. “The latter of the two gives users a better understanding of a player’s skillset; some scouts even use it as a player scouting tool.”

## Revamping the push notification system to scale with an expanding user base

When FotMob began sending push notifications to users, it originally enlisted third-party providers. However, it quickly found they couldn’t support the volume of notifications the app needed to distribute the updates and crashed during peak traffic periods. Pivoting, Christer and Tommy quickly began plans to develop a solution in-house and looked to AWS for an assist.

“Our fans are loyal, but FotMob is a live sports service, so there’s an expectation our app will be stable; downtime isn’t an option,” Christer explained. “If something breaks or we’re dark for more than a few minutes, users will go elsewhere. We knew AWS could give us that peace of mind, and we were right; AWS provides incredible stability.”

On an average week, FotMob’s system may send over three billion push notifications, and in just one day, it can see five billion HTTP requests each hour, which translates to 1.6 million requests every second. With its infrastructure now powered by AWS, FotMob can support near-instant push notification delivery across regions, even during peak traffic periods. [ Amazon Simple Storage Service](https://aws.amazon.com/s3/) (Amazon S3) and [Amazon Aurora](https://aws.amazon.com/rds/aurora/) enable the team to store match data and highlights in a multi-region setup. [Amazon Elastic Cloud Compute](https://aws.amazon.com/ec2/) (Amazon EC2) processes and distributes the match updates in near real-time, while [Amazon Elastic Kubernetes Service](https://aws.amazon.com/eks/) (Amazon EKS) and [Amazon ElastiCache](https://aws.amazon.com/pm/elasticache/) support the push notification delivery.

FotMob also uses Amazon CloudFront to confirm rapid delivery of other static content to users, AWS Lambda for scalable application programming interfaces (APIs), and AWS Cloud Development Kit (AWS CDK) for infrastructure as code. Christer added, “With AWS as our backend, we don’t get hung up on infrastructure challenges, so we can innovate faster to deliver features fans care about. They get quick, reliable updates without any disruption.”

## Charting the course ahead

With a vision to expand its user base to 30 million, FotMob understands the importance of further personalizing the user experience. It recently began experimenting with generative AI using Amazon Bedrock to help create more tailored news and team summaries, with match reports designed to engage fans.

Thus far, FotMob has tested several large language models, with [Anthropic’s Claude](https://aws.amazon.com/bedrock/claude/) proving the most cost-efficient and delivering optimal results. Using the model, FotMob successfully launched a team summary feature for its app in English and is already planning to use generative AI to support additional languages.

“Amazon Bedrock gives us a scalable and efficient framework to deliver the AI-generated summaries fans want,” Christer noted. “It integrates with our existing AWS services and lets us quickly test different models to ensure accuracy and minimize costs.”

He believes FotMob’s continued emphasis on user experience and innovation sets the company apart in the sports app landscape and that AWS is integral to maintaining this edge. Christer concluded, “One of the greatest benefits with AWS is having everything we need from a single provider. Even when we’re exploring new tech, we often go to AWS first to see if they have something that suits, as it’s easier to have everything in one place.”

[Download FotMob](https://www.fotmob.com/download) to see AWS technology in action and experience near real-time football updates.[ Explore how](https://aws.amazon.com/gametech/?trk=77f9e342-cda0-4c48-a2dd-0879fd1617ff&sc_channel=ps&ef_id=CjwKCAiA2cu9BhBhEiwAft6IxGqfN6ek5iPMXBv8s2m0UX_X8XjE6oXDTg-Qq7XEYcXtAKozlWKkwxoCNqUQAvD_BwE:G:s&s_kwcid=AL!4422!3!719304002286!e!!g!!aws%20for%20games!21865058392!169751941436&gbraid=0AAAAADjHtp-IHIvIfr6qxfxTz2YWg6xik&gclid=CjwKCAiA2cu9BhBhEiwAft6IxGqfN6ek5iPMXBv8s2m0UX_X8XjE6oXDTg-Qq7XEYcXtAKozlWKkwxoCNqUQAvD_BwE) you can build, run, and grow applications with AWS or [connect with an AWS for Games team member](https://pages.awscloud.com/Amazon-Game-Tech-Contact-Us.html) for more information.

## Recommended reading

[- Bundesliga powered by AWS  ](https://aws.amazon.com/sports/bundesliga/?did=cr_card&trk=cr_card)

[- NFL on AWS](https://aws.amazon.com/sports/nfl/?did=cr_card&trk=cr_card)

[- How DAZN uses AWS Step Functions to orchestrate event-based video streaming at scale](https://aws.amazon.com/blogs/media/how-dazn-uses-aws-step-functions-to-orchestrate-event-based-video-streaming-at-scale/)

[- Hudl Scales Video Processing and Boosts Reliability by Optimizing on Amazon EC2 Spot Instances  ](https://aws.amazon.com/solutions/case-studies/hudl-spot/)

  
![Blog Image](/images/logo-blog/blog1.1.png)


Source:  
https://aws.amazon.com/blogs/gametech/fotmob-delivers-near-real-time-football-updates-to-millions-of-fans-with-aws/
