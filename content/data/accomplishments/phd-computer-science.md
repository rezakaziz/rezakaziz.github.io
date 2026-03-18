+++
date = '2026-01-24T17:00:48+01:00'
draft = false
title = 'Phd Computer Science'
+++

During my **PhD in Computer Science**, I conducted research on a central and unresolved problem in modern machine learning systems:

> **How can federated learning be made both privacy-preserving and verifiable, without relying on unrealistic trust assumptions?**

This work explores the gap between **theoretical privacy guarantees** and their **practical enforcement in distributed systems**.

The objective is **not only to protect data**, but to go one step further:

- ensure that privacy mechanisms are **correctly applied**,
- reduce trust in the central server,
- and make the entire learning process **verifiable and auditable**.

You can read more in these documents [[Thesis]](/documents/accomplishments/Thesis_Phd.pdf) ·
[[Poster]](/documents/accomplishments/Slides_Phd.pdf).

---

## 🌐 Federated Learning: Promise and Limitations

**Federated Learning (FL)** enables multiple participants to collaboratively train a model **without sharing their raw data**.

Instead of centralizing data:

- each client trains locally,
- and only model updates are shared with a central server.

At first glance, this paradigm appears to solve privacy concerns.

However, this assumption is **fundamentally incomplete**.

### ⚠️ The Hidden Problem

Even without raw data sharing:

- gradients can leak sensitive information,
- model updates can be exploited through inference attacks,
- and the central server remains a **critical point of trust**.

This reveals a key insight:

> **Federated Learning provides privacy by design — but not privacy by guarantee.**

---

## 🔐 Core Challenges

From an engineering and system perspective, three major challenges arise:

### 1. Information Leakage

Gradients and model updates can reveal:

- training samples,
- user attributes,
- or dataset membership.

### 2. Trust Assumptions

Most existing systems assume:

- an honest or semi-honest server,
- which is often unrealistic in real-world deployments.

### 3. Lack of Verifiability

There is **no mechanism to prove** that:

- differential privacy was correctly applied,
- aggregation was done properly,
- or the system behaves as claimed.

As a result:

> **Users and regulators are forced to trust — without the ability to verify.**

---

## 🧠 Research Direction

This thesis is built on a central idea:

> **Privacy alone is not sufficient — it must be combined with verifiability.**

Among existing techniques, **Differential Privacy (DP)** provides the only formal guarantee that remains valid after model release.

However:

- DP introduces a **privacy–utility trade-off**,
- and requires trusting the entity that applies the noise.

To address these limitations, this work explores the combination of:

- **Differential Privacy (DP)** → formal privacy guarantees
- **Homomorphic Encryption (HE)** → protection of computations
- **Zero-Knowledge Proofs (ZKPs)** → verifiability without disclosure
- **Secret Sharing** → decentralization of trust

---

## 🧩 Contributions

This thesis introduces **three complementary contributions**, each addressing a specific limitation of federated learning.

### 1. Reducing Trust with Homomorphic Encryption

A first framework introduces a **secure aggregation tunnel** using additive homomorphic encryption.

- Client updates remain encrypted during transmission and aggregation
- The server never accesses raw updates
- Noise generation is decoupled from aggregation

This significantly reduces reliance on a trusted server.

---

### 2. Verifying Differential Privacy with Zero-Knowledge Proofs

A second contribution introduces a **non-interactive verifiability protocol** based on:

- **zk-SNARKs**
- **cryptographic hash commitments**

This allows:

- proving that differential privacy was correctly applied
- without revealing either the data or the noise

This is a key step toward **auditable machine learning systems**.

---

### 3. ProoFed: A Unified Framework

The final contribution is **ProoFed**, a distributed framework that combines:

- Differential Privacy
- Secret Sharing
- Verifiable aggregation

Key properties:

- Noise generation is decentralized across clients
- No single entity controls privacy
- Aggregation is **verifiable in zero-knowledge**

This removes **single points of trust** while preserving scalability.

---

## 🚀 Conclusion

This thesis demonstrates that:

> **Privacy-preserving machine learning must evolve into verifiable machine learning.**

By combining cryptographic techniques with differential privacy, it is possible to design systems that are:

- **secure** (data remains confidential)
- **trust-reduced** (no reliance on a central authority)
- **verifiable** (correctness can be proven)

More broadly, this work highlights a shift:

> **From “trust the system” → to “prove the system”.**
