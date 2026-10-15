# Dario Gemi

### Senior Technical Business Analyst | Product & Technical Project Professional | Banking & Payments | AI & Systems Architecture

📍 Montevideo, Uruguay · ✉️ dariogemi@gmail.com · [LinkedIn](https://linkedin.com/in/dariogemi) · [GitHub](https://github.com/dariogemi)

---

## About

I am a **Senior Technical Business Analyst and Technical Project/Product professional with 20+ years of experience** across banking, payments, enterprise integration, and service management. My career has been built at the intersection of business and engineering: eliciting requirements from stakeholders, resolving technical ambiguity across global teams, and delivering payment systems, ATM networks, gateway integrations, and enterprise platforms in strictly regulated environments. My roles have spanned Technical Project Manager, Product Manager, and Senior Business Analyst titles across consulting, enterprise services, and product organizations.

My domain core is **banking and payments** — payment gateways, ATM transaction flows (ISO 8583 authorization/reversal, STAN/RRN traceability, reconciliation and settlement), EMV migrations, Visa/Mastercard certification support, XFS/HSM configuration, AML integrations, and PCI DSS-related environments — for institutions including BROU, BBVA, Banco Nación Argentina, Citibank, Bank of America, Chase, Google Pay and Apple Pay integrations.

Since 2022 I run **Nivora, an independent technology and AI lab**, where I work hands-on with applied AI, LLM orchestration, event-driven automation, edge computing, observability, and resilient systems design. The lab is contemporary evidence that I still design, build, validate, and operate real systems — with specs, runbooks, and rollback discipline — not demonstrations.

How I work: evidence before assumptions, failure modes designed upfront (fallback, idempotency, correlation, circuit breaking), operational runbooks for everything I ship, and version-controlled change with checkpoint discipline. I operate as comfortably in service-governance conversations with executive stakeholders (RACI, SLOs, QA, risk) as in protocol-level troubleshooting with engineers. I am not a "developer who recently discovered AI": I am a senior business-technology professional whose two decades of integration and analysis work now extend into AI transformation.

## What I Work On

### Business & Product

Requirements elicitation, functional specifications, stakeholder management across business and engineering, Agile/Scrum delivery, product workflow optimization, software factory management. Recent practice: service onboarding and intake processes for enterprise services across global teams (TCS / PwC US), product and operational consulting (Kreilabs, Odoo ecosystem).

### Banking & Payments

Payment gateways and regional gateway integrations (POS systems, payment terminals, virtual terminals, e-commerce), ATM networks, ISO 8583 transaction flows, authorization and reversal handling, reconciliation and settlement, EMV national migrations, Visa and Mastercard certification support, XFS/HSM, AML integrations aligned with Central Bank of Uruguay guidelines, PCI DSS-related environments.

### Enterprise Integration

API integration, systems integration, distributed platforms (e.g. distributed check-clearing), event-driven architectures, messaging (including MQTT in edge contexts), external integrations with banks, acquirers, wallets, and payment networks. Comfortable owning the ambiguous middle between vendor specs, internal systems, and delivery expectations.

### AI & Intelligent Systems

Applied AI and AI transformation: multi-provider LLM routing with error classification and circuit breaking, AI agent coordination with idempotency and durable records, prompt engineering, AI-assisted software engineering workflows, Model Context Protocol (MCP) integrations, local AI models for privacy-sensitive workloads. Focus is always reliability and operability, not demos.

### Software & Systems Architecture

Systems architecture, solution architecture, integration architecture: defining contracts, state machines, fallback chains, correlation and idempotency strategies, configuration-as-code, and documentation that future engineers (or future AI agents) can actually follow. Working languages and platforms: Python, Bash, SQL, YAML/Jinja, C#, Java, Linux, AWS, Azure, Git/GitHub.

### Reliability & Operations

Observability, SRE practices for constrained environments, incident management, runbooks, service management frameworks (RACI matrices, SLOs, target operating models), QA governance, continuous process improvement with Jira, Confluence, and Azure DevOps.

## Selected Professional Experience

> Full detail in [`resume/dario-gemi-resume.md`](resume/dario-gemi-resume.md). Employers, titles, and dates below are stated as in my CV.

* **Tata Consultancy Services (Client: PwC US)** — Technical Project Manager / Senior Service Management Analyst, Aug 2024 – Feb 2026. Enterprise service onboarding and intake; RACI/SLO service frameworks; cross-functional delivery across engineering, architecture, and IT operations; QA governance with Azure DevOps.
* **Kreilabs (Odoo Platinum Partner)** — Product Manager / Business Consultant, 2024. Executive advisory on strategy, operations, and software factory management; workflow optimization for delivery efficiency.
* **Nivora — Independent Technology & AI Lab** — Founder, 2022 – Present. Applied-AI lab: event-driven automation with LLMs, autonomous incident detection/classification/safe remediation, intelligent environments. See below.
* **Verifone Inc.** — Senior Business Analyst, Global Engineering & Regional Gateways, 2022 – 2023. Gateway integrations with Bank of America, Chase US/Canada, Google Pay, Apple Pay; requirements across POS, terminals, and e-commerce gateways in regulated environments.
* **Evertec Inc.** — Senior Business Analyst, 2021 – 2022. Business analysis for high-volume payment-processing platforms; functional specifications under strict financial regulation.
* **Arnaldo C. Castro S.A.** — Technical Director / IT Expert / Business & Functional Analyst, 2013 – 2021. Mission-critical banking systems for BROU, Bandes, BBVA, Banco Nación Argentina, Citibank; distributed check-clearing platform (CV-reported results: −70% hold times, −60% operating costs); ATM flows, EMV, XFS/HSM, AML.

## Nivora — Independent Technology & AI Lab (2022 – Present)

**Nivora** is my independent lab for applied technology work. It is not a large company, a funded startup, a consultancy, or a commercial product — it is a disciplined one-person initiative where I prototype and operate real systems: AI-driven automation workflows, systems integration, intelligent environments, and reliability engineering on edge infrastructure.

Focus areas: applied AI, AI-assisted software engineering, intelligent automation, AI orchestration, edge computing, observability, resilient systems, local-first technology, systems integration, and experimentation with production-grade discipline (specs, runbooks, version control, rollback).

**Public AI experience → [Hogar IA Daret](https://hogar-ia-daret.dgemi.chatgpt.site/)** — a concrete way to explore the project.

The engineering case studies below are distilled from this lab work. They are written as **patterns and architectures**, deliberately abstracted from any private infrastructure — no network details, device identities, credentials, or household information.

## Selected Engineering Case Studies

Supporting evidence of current hands-on depth — the professional identity above (business-technology leadership in payments and integration) is the core; these patterns show the engineering rigor behind it.

| Case study | Problem | Key engineering ideas |
|---|---|---|
| [Resilient multi-provider LLM routing](projects/resilient-llm-router.md) | Single LLM provider = single point of failure | Error classification, fallback policy, circuit breaker, correlation IDs |
| [Idempotent AI coordination (BEACON)](projects/beacon-coordination.md) | Coordinating AI actions without duplication or lost traceability | Lifecycle state machine, idempotency keys, durable ACCEPTED/RESULT records |
| [Multi-provider TTS fallback](projects/tts-fallback-router.md) | Silent or repeated announcements on provider failure | Ordered fallback chain, real-playback success verification |
| [Safety-constrained HVAC automation](projects/hvac-safety-architecture.md) | Comfort vs. energy waste and unsafe setpoints | Guardrails on actuation, occupancy-aware policy, energy model |
| [Proprietary protocol research (CK99)](projects/ck99-protocol-research.md) | Undocumented Bluetooth control protocol | Evidence-tagged reverse engineering, listen-first harness, safe bridge |
| [Edge observability & autonomous caretaker](projects/edge-observability-caretaker.md) | Silent degradation on a constrained host | Layered detection, risk-classified remediation (L1/L2/L3), runbooks |
| [Local-first IoT migrations](projects/local-first-iot-migrations.md) | Cloud dependence for local devices | Multi-evidence device identity, staged migration, no registry hacks |

Details and architecture sketches for public sharing live in [`projects/`](projects/). This portfolio includes selected professional experience and technical case studies; private validation notes and internal evidence records are intentionally kept out of the public repository.

## Contact

* Email: dariogemi@gmail.com
* LinkedIn: [linkedin.com/in/dariogemi](https://linkedin.com/in/dariogemi)
* GitHub: [github.com/dariogemi](https://github.com/dariogemi)
* Location: Montevideo, Uruguay
* Machine-readable profile for recruiting/AI platforms: [`zorin-profile.md`](zorin-profile.md)
* Skills matrix: [`skills.md`](skills.md)
