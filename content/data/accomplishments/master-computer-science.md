+++
date = '2026-01-24T17:00:33+01:00'
draft = false
title = 'A State of the Art on Privacy-Preserving Clustering with Missing Data'
+++


During my **Master’s degree in Computer Science**, I conducted a research thesis focused on building a **state of the art** at the intersection of **data analysis, privacy, and cloud computing**.

You can read more in these documents [[Thesis]](/documents/accomplishments/Rapport_Master.pdf) ·
[[Poster]](/documents/accomplishments/PosterMaster.pdf).

The objective of this work was not to design a new algorithm, but to **analyze, compare, and synthesize existing approaches** addressing the following question:

> **How can sensitive and incomplete data be clustered while preserving privacy, particularly in cloud-based environments?**

<img src="/data/accomplishments/images/CloudDataAnalysis.png" width="800">



## 🌍 Why This Topic Matters

Modern digital systems generate massive volumes of data through:
- connected devices (IoT),
- online platforms and services,
- healthcare, industrial, and financial systems.

These datasets are often:
- **sensitive**, requiring strong privacy guarantees,
- **incomplete**, due to missing measurements or failures,
- processed on **external cloud infrastructures**.

This creates a fundamental tension between **data usefulness** and **data confidentiality**.





## 📚 Scope and Outcomes of the State of the Art

This work presents:
- a survey of **clustering methods handling missing data**,
- a review of **privacy-preserving clustering approaches** based on homomorphic encryption,
- a comparative analysis of their **assumptions, limitations, and trade-offs**.

By confronting these approaches with real-world constraints, the thesis highlights several **open gaps** between theoretical solutions and practical deployment.



## 🔎 Identified Research Gaps

The state-of-the-art analysis reveals:
- limited support for missing data in encrypted clustering methods,
- high computational overhead introduced by cryptographic operations,
- simplifying assumptions that do not hold in realistic system settings.

These gaps motivated further work beyond the scope of this thesis.



## 🚀 Conclusion

This thesis established a **conceptual and technical foundation** for understanding the challenges of privacy-preserving data clustering in realistic environments.

By identifying unresolved issues and practical limitations, it naturally opened the way for **subsequent applied and engineering-oriented work**, presented separately in  [this article](/data/accomplishments/ingenieur-computer-science/).
