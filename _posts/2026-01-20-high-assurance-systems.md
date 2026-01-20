---
layout: post
title: "High-Assurance Systems"
author: Jamie Adams
date: 2026-01-20
description: >
  A concise explanation of what high-assurance systems are,
  why they exist, and how they differ from traditional systems.
tags:
  - high-assurance
  - trusted-systems
  - mls
  - selinux
  - umrs
  - nist-800-53
  - cmmc
  - SPARK
  - Ada
---

<img src="/assets/images/umrs-logo-1024px.png" align="right" width="200">
A high-assurance system is a computer system that must not merely work correctly, but must be proven, verified, and demonstrably trustworthy under the most demanding security or safety conditions.

High-assurance engineering has its roots in High Assurance Computing and Management Systems (HACAMS). In the 1990s and early 2000s, HACAMS was often used in academic papers, DARPA programs, and DoD system descriptions. Over time, the terminology shifted.

Today, you rarely hear *HACAMS* used explicitly. Instead, the same ideas live on under different names, such as:
* High-assurance systems
* Trusted systems
* MLS (multi-level security) systems
* Cross-domain systems (CDS)
* Safety-critical and mission-critical systems
* Raise-the-Bar or similar assurance initiatives

## REAL WORLD EXAMPLES

High-assurance systems appear most often in environments where failure is unacceptable and recovery is either impossible or too late.

In **military and intelligence systems**, high assurance is required wherever information crosses trust boundaries or directly controls lethal force. Cross-Domain Solutions (CDS) and guards must comply with NSA “Raise the Bar” and NCDSMO requirements, enforce formal MLS policies, and are explicitly forbidden from failing open under any circumstance. SIGINT collection platforms operating on submarines, aircraft, or remote ground stations must behave deterministically and securely despite harsh conditions and limited access. Weapons-control computers, such as those used in missile defense and targeting systems, demand mathematically provable correctness and safety because software failure can have immediate and irreversible consequences.

Within **national infrastructure**, high-assurance requirements arise wherever systemic failure could threaten public safety or national survival. Nuclear command-and-control systems tolerate effectively zero probability of failure; even a sub-percent chance is considered unacceptable, pushing designs toward near-mathematical impossibility of error. Air-traffic control radar and coordination systems similarly require absolute integrity and predictable real-time behavior, as timing errors or corrupted data can cascade into catastrophic outcomes.

**Formal safety-critical industries** rely heavily on high-assurance principles enforced through regulation and certification. Aviation flight computers are governed by DO-178C Level A, requiring that every line of code be traceable, testable, and formally verified. Medical devices such as pacemakers and infusion pumps must be provably safe, because software crashes can directly result in loss of life. Industrial safety systems in oil refineries and power plants must maintain control under fault conditions, as failures can cause large-scale environmental and human disasters.

Finally, **high-integrity cryptography and security platforms** embody many of the same assurance goals. FIPS 140-3 validated cryptographic modules require not only approved algorithms, but implementations that are demonstrably correct under strict operational constraints. Formally verified microkernels, such as seL4, take this further by mathematically proving entire classes of correctness and isolation properties, eliminating whole categories of implementation error.


## CORE CONCEPTS
A high-assurance system is one in which correctness, security, and policy enforcement are **never assumed**. Instead, these properties must be explicitly demonstrated and continuously defended through structured, repeatable evidence.

This evidence typically includes formal proofs and model checking to show that critical properties hold by construction, rigorous code auditing to validate implementation correctness, and tightly controlled development processes that reduce the risk of unintended behavior. Trusted build environments ensure that the software being evaluated is exactly the software being deployed, while independent evaluation provides an external check against institutional bias or oversight.

High-assurance systems do not stop at initial certification. Verification continues throughout the system’s lifecycle, with ongoing validation and re-evaluation as software, configurations, and operational contexts evolve.

> A high-assurance system provides mathematical or process-based evidence that it behaves correctly,
> securely, and predictably, even under attack.
>
> Some high-assurance systems go beyond testing and provide mathematical proof of correctness. For example,
> software written in [SPARK Ada](https://docs.adacore.com/spark2014-docs/html/ug/en/overview.html)
 can use [formal contracts](https://docs.adacore.com/spark2014-docs/html/ug/en/contracts.html)
 and [theorem proving](https://docs.adacore.com/spark2014-docs/html/ug/en/proof.html) to demonstrate, with mathematical
> certainty, that critical properties always hold and that entire classes of runtime failure are impossible.
>
> 



## SYSTEM CHARACTERISTICS
A high-assurance system is engineered under strict, auditable processes designed to make security properties explicit rather than implicit. Its trusted computing base is deliberately minimized and verified, reducing the amount of code and functionality that must be trusted to enforce security correctly.

Such systems are built around a mathematically defined security policy that is enforced through non-bypassable controls, such as mandatory access control (MAC) or multi-level security (MLS). In practical deployments, this may include enforcing MLS separation on platforms like RHEL using SELinux MLS, ensuring that policy enforcement occurs below the application layer and cannot be circumvented by software behavior.

High-assurance designs frequently rely on formally verified components where possible. Examples include the use of formally verified microkernels such as seL4, deterministic control logic in aircraft flight computers, and cryptographic operations implemented exclusively through FIPS 140-3 validated modules. These choices eliminate entire classes of implementation error rather than attempting to detect them after the fact.

Finally, high-assurance systems are subjected to independent evaluation and formal analysis, often assessed against rigorous standards such as Common Criteria EAL5+ or higher. The goal is not merely to claim security, but to provide defensible, evidence-backed assurance that the system will behave correctly and securely under real-world conditions.



### KEY FEATURES

| **Feature**                                  | **Details**                                                              |
|:---------------------------------------------|:-------------------------------------------------------------------------|
| Mandatory Access Control (MAC) and MLS enforcement | The policy is not discretionary; users and applications cannot override security decisions.
| Verifiable and minimal trusted computing base (TCB) | Only a very small part of the system is trusted; everything else is untrusted by design.
| Strict development process | Coding standards, code reviews, static analysis, secure coding rules, and documentation are mandatory, not optional.
| Resistance to insider threat, misuse, or misconfiguration | The system should remain secure even when users or software try to bypass controls.
| Formal security model |  Typically Bell–LaPadula (confidentiality) or Biba (integrity), or modern variants.
| Independent evaluation or certification |<br>• Common Criteria EAL5 – EAL7<br>• NSA Raise-the-Bar guidance<br>• NCDSMO evaluations<br>• FIPS 140-3 validation<br>• DO-178C (aviation)<br>• IEC 61508 / ISO 26262 (industrial/safety) |


### KEY DIFFERENCES
The key differences between High-Assurance systems and traditional systems are summarized in the table below:

|                            | **High-Assurance Systems**                   | **Traditional Systems**                      |
|----------------------------|:---------------------------------------------|:---------------------------------------------|
| Level of required evidence | High-assurance systems require formal proofs, mathematical models, auditable processes, and verification evidence.|Traditional systems rely on: unit tests, integration tests, spot checks, and general best practices
| Impact of failure|Failure may mean a warfighter dies, intelligence is compromised, attackers cross domains, critical national data is exposed, or a weapon system misfires.|Failure means downtime, inconvenience, bugs.
|Trust boundary rigor|Every trusted component must be: minimal, auditable, inspected, verified, and controlled through change management|TCB (trusted computing base) isn’t carefully minimized; components grow organically.
| Development discipline | High-assurance:<br>• Strict coding standards<br>• Formal peer reviews<br>• Static analysis (Coverity, etc.)<br>• Configuration control<br>• Long-cycle testing<br>• Threat modeling<br>• Documentation requirements<br>• Security models (MLS, RBAC, etc.)<br>• Reproducible builds<br>• Mandatory hardening (FIPS, MAC, etc.) | Agile, quick iteration, “move fast,” flexible. |


## HIGH-ASSURANCE ENGINEERING
High-assurance engineering is the practice of building systems that must be *proven* trustworthy, not simply assumed to be well designed.

It applies to systems where failure is unacceptable because the consequences extend beyond inconvenience or localized damage. In these environments, failure can result in loss of life, compromise of national security, mission failure, catastrophic financial loss, leakage of classified data, or disruption of critical infrastructure.

> In high-assurance work, the goal is not “works correctly most of the time,” but demonstrable correctness, verifiable security, and predictable behavior under all conditions—including adversarial ones.
>
> In simple terms:
> 
> Traditional engineering = “We think it works.”
> High-assurance engineering = “We can prove it works, and prove it fails safely.”


High-assurance engineering is also frequently misunderstood. It is **not** synonymous with applying individual security mechanisms or modern tooling in isolation. Practices such as secure coding, choosing a memory-safe language like Rust, running SELinux in enforcing mode, deploying firewalls, using encryption, or writing unit tests are all important—but they are security controls, not assurance by themselves.

Those techniques reduce risk, but they do not establish trust.

> Assurance = evidence + process + verification + proven behavior.

