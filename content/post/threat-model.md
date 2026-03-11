---
title: "Why Threat Models Matter in Security Research ?"
date: 2026-03-11T16:30:16+01:00
Description: ""
Tags: ["threat-modeling", "cybersecurity", "security-research"]
Categories: ["Cybersecurity"]
DisableComments: false
---

Over time, while reviewing and reading cybersecurity and privacy papers, I notice something that bothers me more and more: **some papers claim security or privacy guarantees without clearly defining a threat model**.

Personally, I find that problematic.

In security research, a threat model is not a minor detail. It is one of the **foundations of the work**. Without it, the problem is not clearly defined and the security claims become difficult to interpret.

### What Is Threat Modeling?

A threat model describes the **adversarial environment** in which a system operates. It usually defines several elements:

- **Who the adversary is ?**
- **What capabilities the adversary has ?**
- **What parts of the system can be attacked ?**
- **What assumptions the system relies on ?**

In other words, a threat model defines the **rules of the game** between the system and the attacker. It clarifies what the attacker can realistically do and what the system must resist.

### Reasons to Threat Model

Threat modeling helps structure security research in a clear and rigorous way.

First, it **defines the attacker**. In many systems, the attacker could be an external adversary, a malicious participant, or even a curious server that follows the protocol but tries to learn additional information. Each of these attackers has different capabilities and motivations.

Second, it helps identify the **attack surface**. Systems expose many possible points of interaction: communication channels, APIs, storage layers, or distributed components. Threat modeling helps researchers reason about how these components could be abused.

Third, it clarifies the **security goals** of the system. Whether the objective is confidentiality, integrity, availability, or privacy, these goals must always be defined relative to a specific adversary.

Without a threat model, it becomes difficult to understand what the system is actually trying to protect.

Sometimes papers include statements like: "Our system preserves privacy.", "The protocol guarantees security.", "User data remains protected."

But these claims quickly become vague if the threat model is not clearly described.

- Privacy from whom?
- Security against what kind of attacks?
- What capabilities does the adversary have?

Security guarantees only make sense **in relation to an adversarial model**. Without it, the claims lack context.

Another important aspect of threat modeling is that it forces to **make their assumptions explicit**. Every system relies on assumptions. Some components may be trusted, some communication channels may be assumed secure, and some participants may be assumed to behave honestly.

If these assumptions are not clearly stated, a system can appear secure simply because the most relevant attacks are ignored.

### Takeaway

In my opinion, threat modeling is one of the most important steps in cybersecurity research. It helps define the problem, clarify the adversarial context, and justify the proposed defenses. Without a threat model, it becomes difficult to evaluate the relevance of a security solution or to understand what guarantees it actually provides.

That is why I believe every serious security or privacy paper should start by clearly defining its threat model and answering a simple but fundamental question: **Secure against whom?**
