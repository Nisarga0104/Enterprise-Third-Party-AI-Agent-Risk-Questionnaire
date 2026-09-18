# Reference Notes — Third-Party AI Vendor Risk Questionnaire
Date: 2026-09-13

What informed each section of the questionnaire, checked live rather than assumed.

## NIST AI RMF (supply-chain framing)
NIST AI RMF 1.0's Map function explicitly includes third-party components as part of a system's
risk surface — a system built on a third-party LLM inherits that vendor's risks, which is why
this questionnaire exists as a distinct artifact from Project 2's internal risk assessment rather
than folding vendor questions into it. Sections A (Governance & Accountability) and G (Model Risk)
are structured to mirror NIST's Govern/Map/Measure/Manage logic applied specifically to a vendor
relationship rather than an internally-built system.

## ISO/IEC 42001:2023 — Third-Party and Customer Relationships
Confirmed: ISO/IEC 42001:2023's Annex A includes a dedicated control objective for third-party
and customer relationships, requiring (a) clear allocation of roles and responsibilities between
the organization and external parties across the AI lifecycle — data providers, model developers,
platform vendors, integrators — and (b) a defined process for supplier selection and ongoing
monitoring, including requiring evidence such as certifications and impact assessments rather
than accepting self-attestation alone. This directly supports Section T (Assurance Evidence) of
the questionnaire: a vendor's ISO/IEC 42001 or SOC 2 certification is evidence to request, not a
substitute for asking the underlying questions. (Sources differ on whether this sits at control
number A.9 or A.10 depending on which control-numbering revision they're describing — the
control's substance, not its exact number, is what's cited here.)

## Salesforce Einstein Trust Layer (Agentforce) — illustrative reference for Sections K and L
Confirmed the Trust Layer's actual architecture: secure data retrieval filtered by the current
user's permissions, data masking (PII replaced with deterministic tokens before reaching the
LLM), prompt-injection defense (system instructions plus detection), and audit logging of agent
actions — used as the illustrative reference for what a mature agent-governance stack looks like,
consistent with the original draft's framing.

**Important finding, not in the original draft:** In September 2025, security researchers (Noma
Security) disclosed "ForcedLeak" (CVSS 9.4) — a critical, real, patched vulnerability in
Salesforce Agentforce. An attacker embedded a malicious instruction in a public Web-to-Lead form's
Description field; when an employee later asked the agent to process that lead, the agent read
the hidden instruction and exfiltrated CRM data to an attacker-controlled domain. A second,
related research chain ("PipeLeak") was published in April 2026. The root cause in both cases was
**not** a failure of the Trust Layer's masking or toxicity detection — it was that the agent had
broader read/action permissions and less restricted egress than it needed, and indirect prompt
injection (malicious instructions arriving inside *data* the agent reads, not from the user
directly) is not something any current vendor's safety layer fully prevents.
**This is directly relevant evidence for the questionnaire, not just interesting context:** it's
concrete, real, recent proof of why Section K asks about permission scoping and egress
restrictions as a distinct question from Section L's prompt-injection defense question — a vendor
can have strong prompt-injection detection and still be exploitable if agent permissions are too
broad. Added as a named example in the final questionnaire's introduction and as a new red flag.

## Net changes applied
- Added a red flag: "Vendor cannot describe specific limits on what external destinations
  (URLs/domains) an agent is permitted to send data to" — directly informed by the ForcedLeak
  mechanism (data exfiltrated via an agent-generated request to an allowlisted-but-expired domain).
- Added one line to the questionnaire's introduction naming ForcedLeak as a concrete, real
  precedent for why Sections K and L are asked as separate questions rather than one combined
  "is the agent secure?" question.
- Built out the actual question text under each of the 20 sections (A–T) — the original draft
  had section headers only; the questions themselves are the actual deliverable of this project
  and did not exist yet. See `02_Template/Vendor_Risk_Questionnaire_Template.xlsx`.
