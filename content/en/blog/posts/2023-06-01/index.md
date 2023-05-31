---
date: 2023-06-01T08:08:35+10:00
author: "[Ben Vilnis](/about/)"
title: "Turning Down the Noise: Unleashing the Power of SLO-Based Alerting for Superior User Experiences"
linkTitle: "Turning Down the Noise: The Power of SLO-Based Alerting"
description: "Why you should focus on the experience of your users instead of noisy metrics."
tags: ["blog", "o11y", "techincal"]
draft: false
---

<div class="center-text">

  {{< imgproc featured-image-get Fill "1200x627" />}}

  In my [previous post](https://bennysbytes.dev/blog/alert-fatigue-why-less-is-more/), I delved into the concept of alert fatigue and how it can hinder the performance of systems and the productivity of teams, suggesting that less is indeed more when it comes to system alerts. Now it's time to translate that understanding into a tangible strategy to combat alert fatigue while improving overall user experience. This brings us to the emerging paradigm of Service Level Objective (SLO)-based alerting.

  Imagine moving away from the chaos of old-school alerting methods that are overwhelmed by the complexity of contemporary distributed systems, towards a more user-centric, insightful, and resilient approach that focuses on the actual quality of service provided. In this post, I will delve into the nuances of SLO-based alerting, illustrating how it serves as a potent tool in the quest to optimize system health, reduce alert noise, and focus on the actual experience of your users.

  ## Demystifying SLO-Based Alerting

  Instead of obsessing over system metrics, SLO-based alerting narrows in on user experiences and the quality of service provided. Imagine a Service Level Objective (SLO) as a promise—a commitment to a certain level of service over time. It might go something like, "The service will stay up 99.9% of the time over a 30-day rolling window." Pretty neat, right?

  In this framework, an "error budget" is established. This budget represents the amount of allowable service unavailability while still meeting the outlined SLO. In other words, it's the amount of 'downtime' that a service can have without breaching the SLO. For a service with an SLO of 99.9% availability, this equates to a budget of 0.1% unavailability.

  The real magic happens when the "error budget burn rate" starts rising. If the rate of undesirable events (like errors or service unavailability) starts eating into the error budget faster than a dessert lover at a pastry shop, it's time to sound the alarm.

  The beauty of this system is the concept of multi-threshold alerting. For example, suppose we're burning our error budget at the equivalent of 2% per hour. That's like setting the budget on fire! It's a critical issue that needs immediate dousing, triggering an urgent alert. But what if the burn rate is slow, let's say 10% over three days? It's not as pressing and can wait until regular office hours, triggering a less urgent alert. Compared to traditional metrics-based alerting, this approach offers a multi-faceted view of system health, adept at detecting both fast-burning issues and slow, smouldering problems.

  The beauty of SLO-based alerting is its inherent connection to user experience. By focusing on factors that truly impact users, this approach aids in the reliability and resilience of service offerings.

  ## The Value of SLO-Based Alerting

  ### Bridging the Pain Gap between Engineers and Users

  A key benefit of SLO-based alerting is the alignment of engineers' pain with users' pain. It's not unusual with conventional metrics-based alerting for engineers to face an onslaught of alerts while the user impact remains minuscule. Or worse yet, critical issues impacting users might fly under the radar if they don't breach pre-set metrics thresholds.

  > "Your engineers' pain should be as closely aligned with your users' pain as possible."
  >
  >  -- Charity Majors

  With SLO-based alerting, the tie to user experience is direct and meaningful. If an SLO-based alert goes off, it's a clear sign that users are likely being affected. Alerts that result from genuine user impact also provide clear, necessary actions to be taken. In contrast, traditional metrics alerting often generates alerts with no clear action to be taken, thus contributing more to noise than constructive action.

  ### Dialling Down Alert Noise and Fatigue

  Traditional metric-based alerting often resembles a temperamental alarm clock—going off for transient issues or those that don't significantly disturb the user experience. The result? Alert fatigue. It slows response times and risks critical issues being overlooked.

  SLO-based alerting turns down the noise by concentrating on trends over a defined period rather than one-off incidents. Since alerts are tied to the error budget burn rate, temporary issues are less likely to sound the alarm unless they're severe or enduring enough to make a real dent in the error budget.

  ### Accepting Failure as Inevitable

  In the realm of modern, intricate, distributed systems, failures are par for the course. In fact, there is almost always a number of errors occurring at any given moment in a modern, distributed system. The traditional approach of attempting to prevent every single hiccup by alerting on every conceivable metric has proven to be not just unsustainable but counterproductive. It's like a fire alarm that rings every time you light a candle, ultimately leading to alert noise and fatigue, and even then, it might miss the actual fire.

  Embracing SLOs and error budgets means accepting some level of failure as inevitable. The focus shifts from playing an endless game of whack-a-mole with problems to maintaining a high level of service despite these inevitable failures. This change in perspective lets us build more resilient systems and respond more effectively when real fires do break out.

  ## Enter the Role of Observability

  Observability plays a starring role in SLO-based alerting. It's the detective that investigates the crimes that SLOs alert us to. When SLOs indicate that the service isn't meeting user expectations—the "what"—observability steps in to answer the critical "why"?

  The observability paradigm encompasses the collection, analysis, and visualisation of the system's behaviour, focusing on wide-structured events, otherwise known as traces. Although logs and metrics—the traditional "pillars" of monitoring—are still useful, they are like a tourist in a foreign city with a map: you need to know what you're looking for. They cater to _"known-unknown"_ scenarios.

  Wide-structured events, on the other hand, light up the _unknown-unknowns_. They allow us to interrogate the system's behavior with flexibility and depth without a predefined route. When an SLO-based alert rings, observability tools offer a deep dive into the rich, context-laden event data captured as traces. This data helps pinpoint the services, resources, or components implicated, understand the user impact, and ultimately identify the root cause. This level of insight accelerates diagnosis and issue resolution, minimizing user impact.

  Beyond just troubleshooting, observability provides a profound understanding of system behavior, helping to identify trends, patterns, and potential for system improvement. It informs decisions around system architecture and capacity planning. By offering a comprehensive system overview, observability enhances system reliability and performance, solidifying the achievement of SLOs.

  ## To Wrap Up

  Propelled by robust observability, SLO-based alerting offers a user-focused and sustainable methodology to understand and manage system health and reliability. By syncing engineers' efforts with user experiences, dialling down alert noise and fatigue, and acknowledging failure as an inevitable part of the process, SLO-based alerting equips us to create and manage more resilient systems. Ultimately, it paves the way for providing superior service to end-users. So, it's not just a win-win. It's a win-win-win.

</div>
