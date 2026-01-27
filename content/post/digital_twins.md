---
title: "When the Map No Longer Matches the Territory"
date: 2026-01-27T11:18:10+01:00
Description: ""
Tags: ["Digital Twins", "Observability", "Monitoring","Infrastructure","Reliability"]
Categories: ["Observability & Reliability"]
DisableComments: false
---
In the context of my new role within the [BATTwin project](https://battwin.net/), I have been thinking about how we observe systems and how far observation alone can take us. Working on reliability and industrial adoption quickly reveals a recurring pattern: we see problems, but often too late.

> **What follows should not be read as absolute truths, but as reflections.**


## Seeing Is Not Understanding
Managing a complex system is not easy. To understand what is going on, we usually start with monitoring and dashboards. They show metrics, signals, and trends, and help us notice when something is not working as expected.

But these metrics rarely explain the real problem. They show what is happening, not why it is happening or what will happen next. As systems become more complex, we collect more data, but understanding does not automatically improve. Without context, spikes or drops are visible, but their causes remain unclear.

I have experienced this during training sessions, where I manage the infrastructure that provides tools and environments for students’ practical labs. When many groups connect at the same time, the system may run out of memory or CPU. The usual response is simple: identify the processes consuming the most resources and stop them. The system recovers, and the session continues.

In that context, such a reaction is often acceptable. The priority is to keep the session running. Still, it remains purely reactive. It fixes the symptom without understanding the deeper causes, whether it comes from usage patterns, configuration limits, or design choices. As a result, the same problems tend to appear again.

This illustrates the difference between seeing a problem and understanding a system.



## When Monitoring Are Not Enough
In real systems, not everything that matters can be measured. Even with good monitoring, some problems remain hidden. Internal limits or compatibility constraints are not always visible in metrics or dashboards.

I encountered this during an upgrade of the Harvester platform used for training sessions. From a monitoring point of view, everything looked normal. Yet when the system attempted to migrate running workloads from one machine to another, some of them failed, without clear alerts or warning before starting the upgrade.

The root cause turned out to be a hardware compatibility issue. Two machines did not support the same CPU features, which prevented workload migration. This was not a resource usage problem, but a hidden constraint that monitoring did not reveal.

This reinforced an important lesson: monitoring can show visible symptoms, but it does not always expose deeper limitations.


## Why Simulations Are Not Enough
As systems grow more complex, it is natural to look for ways to test new design ideas or optimizations before applying them in reality. In theory, models, simulations, or pre-production environments should help address that need.

However, these approaches are often built separately from the real system. They rely on simplified assumptions and fixed conditions, while real systems evolve over time, with changing workloads and environments. Production clearly illustrates this gap: many constraints only appear under real workloads, real interactions, and real diversity. For example, upgrading our Harvester platform in a test environment worked perfectly, while applying the same changes in production failed.

As a result, simulations and test environments can validate expected behavior, but they struggle to reflect actual conditions. This raises a fundamental question: if reality cannot be fully reproduced elsewhere, how can we safely test new design ideas or optimize a system without discovering problems too late?


## Digital Twins as a potential Answer
When observation is limited, measurement is incomplete, and simulations no longer reflect reality, a different approach is needed. This is where digital twins naturally fit.


According to [IBM](https://www.ibm.com/think/topics/digital-twin), the definition of  digital twin is as follow:
> A digital twin is a virtual representation of a physical object or system that uses real-time data to accurately reflect its real-world counterpart's behavior, performance and conditions.

By bringing together observation, inference, and context, digital twins make it possible to move from reacting to problems to anticipating them. They provide a foundation for better understanding, better decisions, and more reliable systems.
> A digital twin is a living representation of a real system.
