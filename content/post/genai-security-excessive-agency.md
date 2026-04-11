---
title: "Excessive Agency: Why Human-in-the-Loop Is Not Enough"
date: 2026-04-10T15:17:01+02:00
Description: "Learn how excessive agency in LLMs and AI agents creates new security risks. This article explains how over-permissioned systems, prompt injection, and hidden data exfiltration can bypass human-in-the-loop controls, and explores key mitigation strategies aligned with OWASP and modern AI security practices."
Tags: ["llm-security", "genai", "owasp", "ai-agents"]
Categories: ["Cybersecurity"]
DisableComments: false
---

Tools such as Claude Code and Claude CoWork are increasingly embedded in systems where they are granted a degree of agency. They are no longer limited to generating text, but can call functions, interact with external tools, modify code, and execute multi-step workflows in response to a prompt.

In these agent-based setups, the model can decide which actions to take and iteratively use its own previous outputs to guide subsequent steps. As these capabilities grow, a new challenge emerges: **excessive agency**.

## 🧠 What Is Excessive Agency in LLMs?

Excessive agency occurs when the autonomy given to an LLM extends beyond what is appropriate or intended. It arises when the model begins to over-interpret instructions, take initiatives that were not explicitly requested, or continue executing actions across multiple steps without sufficient validation.

For example, instead of applying a small, targeted code fix, it may refactor an entire module, introduce new abstractions, or trigger additional operations that expand the original scope.

Excessive agency is not simply about acting, but about **acting beyond the right boundaries**. The system shifts from assisting the user to implicitly deciding what should be done. While these systems are designed to be helpful and proactive, they do not always have a reliable sense of when to stop, when to ask for clarification, or when to remain strictly aligned with the user’s intent.

In practice, excessive agency typically arises from three complementary issues.

The first is **excessive functionality**. The system is equipped with more capabilities than necessary, such as allowing write or delete operations when only read access is required.

The second is **excessive permissions**. The system has access to more data or resources than it needs, such as full database or mailbox access instead of narrowly scoped, read-only permissions.

The third is **excessive autonomy**. The model is allowed to execute actions or chain decisions without sufficient validation, oversight, or human control.

Individually, each of these factors introduces risk. Combined, they create systems that are powerful but insufficiently constrained, increasing the likelihood that the model will act beyond its intended role.

## ⚠️ Example: Excessive Agency in an Agent-Based Email Assistant

Consider an organization deploying an LLM-based assistant integrated with tools like Microsoft Outlook or Gmail. Unlike a simple chatbot, this assistant operates in an **agent-based setup**. It can read emails, retrieve historical conversations, and generate draft replies. It can also chain multiple steps, using previous outputs to guide subsequent actions.

On paper, the system appears well-designed. Drafting responses is a legitimate feature, and emails are only sent after human validation.

Now imagine a malicious email crafted with hidden instructions. The attacker embeds content using techniques such as invisible text, manipulated HTML formatting, or any **steganography technique**, hiding instructions in a way that is not perceptible to the human reader but still processed by the LLM.

Because the system operates as an agent, it does more than just read and draft. It can **decide how to process the input**, **retrieve additional information**, and **chain multiple actions** before producing an output. The hidden instructions can influence the model’s internal reasoning and decision-making process.

The issue comes from the combination of capabilities:

- **Broad data access**: the system can access large portions of the mailbox, including historical and sensitive conversations
- **Unconstrained retrieval**: it can pull in additional context that is not strictly required for the task
- **Multi-step reasoning**: it can chain actions and expand the scope based on intermediate results

Drafting itself is not the problem. The problem is that the draft is built using **data and decisions that exceed the original intent**.

Under the influence of malicious input, the assistant may retrieve sensitive information from past emails and include it in a draft reply. More subtly, the exfiltration can reuse the same techniques used in the attack, embedding sensitive data through invisible text, HTML tricks, or **steganography**. The visible part of the draft appears legitimate, while hidden content carries confidential information that may go unnoticed during human review.

This is excessive agency in practice. The system stays within its defined capabilities, but the **way it uses them** goes beyond what is appropriate.

Even with human validation, the risk remains significant. The draft appears coherent and trustworthy, while the underlying multi-step process that produced it remains invisible.

This example shows that excessive agency does not require inherently dangerous features. It emerges when **legitimate capabilities interact without sufficient boundaries**, turning a helpful assistant into a potential covert data exfiltration channel.

## 🛡️ Mitigation Strategies: Reducing Excessive Agency in LLM Systems

Mitigating excessive agency is about controlling how capabilities are used, not removing them.
These mitigation measures help reduce unnecessary access, limit autonomy, and enforce boundaries.
However, they should be treated as mitigations, not guarantees, and must be continuously monitored.
Below are some of them.

#### 1. Minimize functionality (principle of least capability)

The system should only be given the capabilities it strictly needs to perform its task. Avoid unnecessary features such as write or delete operations when only read access is required, and favor narrowly scoped tools over general-purpose ones.

#### 2. Restrict permissions (principle of least privilege)

Access to data and resources should be tightly controlled. The system should operate with read-only access by default and be restricted to specific datasets, folders, or time ranges. Broad access significantly increases the risk of unintended data exposure.

#### 3. Control autonomy (human-in-the-loop)

Critical actions should always require human validation. The model can generate drafts or recommendations, but execution must remain under human control.

#### 4. Constrain tool use and action chaining

The system’s ability to invoke tools and chain actions should be bounded. Limiting steps and preventing uncontrolled execution helps maintain alignment with the original intent.

#### 5. Sanitize and isolate inputs

All external inputs should be treated as untrusted. Hidden or obfuscated content, including HTML tricks and steganographic signals, should be removed or neutralized.

#### 6. Limit data retrieval and context expansion

The model should only access the information strictly necessary for the task. Avoid unnecessary retrieval of historical or sensitive data.

#### 7. Increase transparency and observability

System behavior should be logged and auditable. Tracking tool usage and data access helps detect abnormal or unintended actions.

#### 8. Apply output controls and validation

Outputs should be inspected for hidden or encoded content. This includes detecting invisible text or unusual patterns that could indicate data exfiltration.

## 💡 Key Takeaway

Excessive agency does not stem from a single issue, but from the interaction between functionality, permissions, and autonomy.

Mitigating it requires carefully balancing these elements so that the system remains useful while staying strictly within its intended boundaries.

> A system is not safe because a human reviews the final output.
> It is safe when it **cannot produce harmful output in the first place**.

## 📚 References

- [OWASP GenAI – Excessive Agency (LLM06)](https://genai.owasp.org/llmrisk/llm08-excessive-agency/)
- [Understanding Excessive Agency in LLMs (Coralogix)](https://coralogix.com/ai-blog/understanding-excessive-agency-in-llms-implications-and-solutions/)
- [Mitigate Excessive Agency in AI Agents (Auth0)](https://auth0.com/blog/mitigate-excessive-agency-ai-agents/)
- [https://genai.owasp.org/llmrisk/llm062025-excessive-agency/](https://genai.owasp.org/llmrisk/llm062025-excessive-agency/)
