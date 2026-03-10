# dfirs1car1o

**SaaS security assessments, automated.**

We build open-source tooling for governance-grade security reviews of enterprise SaaS platforms — combining OSCAL, multi-agent AI, and regulatory frameworks into auditable, reproducible assessment pipelines.

---

## saas-posture

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://github.com/dfirs1car1o/saas-posture/blob/main/LICENSE)
[![CI](https://github.com/dfirs1car1o/saas-posture/actions/workflows/ci.yml/badge.svg)](https://github.com/dfirs1car1o/saas-posture/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.11%2B-blue)](https://www.python.org/)
[![codecov](https://img.shields.io/badge/tests-37%20passing-brightgreen)](https://github.com/dfirs1car1o/saas-posture/actions)

A six-phase, read-only security assessment pipeline powered by multi-agent AI. Produces governance-grade evidence packages for Salesforce and Workday orgs — no writes, no shared state, fully auditable.

```
Phase 1 — Collect    sfdc-connect / workday-connect   →  platform snapshot
Phase 2 — Assess     oscal-assess + oscal_gap_map      →  gap analysis + backlog
Phase 3 — Score      sscf-benchmark                    →  RED / AMBER / GREEN
Phase 4 — Gate       nist-review (NIST AI RMF 1.0)     →  clear / flag / block
Phase 5 — Report     report-gen                        →  Markdown + DOCX packages
Phase 6 — Monitor    OpenSearch + 3 dashboards         →  trending posture over time
```

**Platform support:** Salesforce (35 SBS controls) · Workday (30 WSCC controls)

**Framework chain:**
Platform control → SSCF domain → CCM v4.1 → ISO 27001:2022 Annex A → SOX / HIPAA / SOC2 / NIST 800-53 / PCI DSS / GDPR

**AI governance:** Every output passes a NIST AI RMF 1.0 gate before delivery. Block verdicts require human acknowledgment.

**Auth:** Salesforce JWT Bearer · Workday OAuth 2.0 Client Credentials · Read-only by design.

---

### Continuous Monitoring Dashboards

Three OpenSearch dashboards ship pre-built — auto-imported on `docker compose up`:

| Dashboard | Purpose |
|-----------|---------|
| Salesforce Security Posture | SBS quarterly review — score tile, top failing controls, domain risk, severity heat, POA\&M |
| Workday Security Posture | WSCC compliance review — identical layout, filtered to Workday findings |
| SSCF Overview | Cross-platform leadership view — Salesforce vs. Workday side-by-side, score trends |

---

### Quick Start

```bash
git clone git@github.com:dfirs1car1o/saas-posture.git
cd saas-posture
python3 -m venv .venv && source .venv/bin/activate
pip install -e .
cp .env.example .env  # add credentials

# Full pipeline — Salesforce live org
agent-loop run --env dev --org <org-alias> --approve-critical

# Workday dry-run (no credentials needed)
python3 scripts/workday_dry_run_demo.py --org acme-workday --env dev

# Drift detection — compare two assessment runs
python scripts/drift_check.py --baseline <old>/backlog.json --current <new>/backlog.json
```

→ **[View the project →](https://github.com/dfirs1car1o/saas-posture)**
→ **[Full wiki →](https://github.com/dfirs1car1o/saas-posture/wiki)**
