# Enterprise Third-Party AI & Agent Risk Questionnaire
**AI Governance Portfolio — Project 4 of 5**

An operational, risk-tiered assessment framework designed to evaluate enterprise third-party AI systems and autonomous agents prior to procurement and deployment.

---

## Key Features

* **Worst-of Section Methodology:** Prevents high-performing baseline security controls from masking severe, localized safety or governance deficiencies.
* **Agentic Risk Framework:** Explicitly isolates prompt injection defenses from permission scoping and data egress constraints to detect privilege-escalation vulnerabilities.
* **Automated Red Flag Escalation:** Triggers mandatory escalation to the AI Governance Committee upon hitting any of 9 defined critical failure conditions.
* **Standard Alignment:** Mapped to **NIST AI RMF 1.0** and **ISO/IEC 42001:2023 Annex A** supplier controls.

---

## Workbook Architecture

| Tab | Purpose | Key Metrics / Output |
| :--- | :--- | :--- |
| `Instructions` | Methodology, decision criteria, and scoring bands | Guidance for assessors |
| `Vendor Profile` | Metadata, deployment context, and initial risk tiering | High / Medium / Low initial profile |
| `Questionnaire` | 61 structured evaluation criteria across 20 functional domains (A–T) | Section gap severity ratings |
| `Scoring Summary` | Real-time automated worst-of aggregation formula | Overall Rating & Final Decision Band |
| `Red Flags` | 9 mandatory disqualification/escalation conditions | Mandatory Governance Committee Escalation |

---

## Decision Bands

* **Approved (Low Rating):** Standard procurement and integration pipeline.
* **Approved with Conditions (Medium Rating):** Remediation required within set timeframe under designated internal ownership.
* **Further Due Diligence Required (High Rating):** Mandatory AI Governance Committee review before technical deployment.
* **Further Due Diligence Required - Critical (Critical Rating):** Automatic hold; defaults to **Rejected** if unmitigated.

---

## Repository Structure

* `01_Research/`: Technical notes on agent threat modeling (e.g., ForcedLeak) and standard mapping.
* `02_Template/`: Reusable Excel assessment tool (`.xlsx`) and schema overview (`.md`).
* `03_Worked_Example/`: End-to-end completed assessment for fictional vendor CloudAgent Technologies Inc.
* `04_Final/`: [Executive Overview presentation (PDF)](04_Final/Vendor_Risk_Questionnaire_Overview.pdf)

* ---
*[← Back to full AI Governance portfolio](https://github.com/Nisarga0104)*
