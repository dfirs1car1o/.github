# dfirs1car1o

**SaaS security assessments, automated.**

We build open-source tooling for governance-grade security reviews of enterprise SaaS platforms — combining OSCAL, multi-agent AI, and regulatory frameworks into auditable, reproducible assessment pipelines.

---

## saas-posture

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://github.com/dfirs1car1o/saas-posture/blob/main/LICENSE)
[![CI](https://github.com/dfirs1car1o/saas-posture/actions/workflows/ci.yml/badge.svg)](https://github.com/dfirs1car1o/saas-posture/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.11%2B-blue)](https://www.python.org/)

A six-phase, read-only security assessment pipeline powered by multi-agent AI:

```
Phase 1 — Collect    sfdc-connect / workday-connect   →  platform snapshot
Phase 2 — Assess     oscal-assess + oscal_gap_map      →  gap analysis + backlog
Phase 3 — Score      sscf-benchmark                    →  RED / AMBER / GREEN
Phase 4 — Gate       nist-review (NIST AI RMF 1.0)     →  clear / flag / block
Phase 5 — Report     report-gen                        →  Markdown + DOCX packages
Phase 6 — Monitor    OpenSearch + 3 dashboards         →  trending posture over time
```

**Platform support:** Salesforce (35 SBS controls) · Workday (30 WSCC controls)  
**Framework chain:** Platform control → SSCF → CCM v4.1 → SOX / HIPAA / SOC2 / ISO 27001 / NIST 800-53 / PCI DSS / GDPR  
**AI governance:** Every output passes through a NIST AI RMF gate. Block verdicts require human acknowledgment before report distribution.

→ **[View the project](https://github.com/dfirs1car1o/saas-posture)**
