# 💰 Cloud Cost Intelligence Platform

![Cloud](https://img.shields.io/badge/Cloud-GCP%20%7C%20AWS-orange)
![FinOps](https://img.shields.io/badge/FinOps-Cost%20Optimization-blue)
![Savings](https://img.shields.io/badge/Savings-%242.3M%20Annual-success)
![Teams](https://img.shields.io/badge/Teams-8%2B%20Engineering%20Teams-informational)
![Reduction](https://img.shields.io/badge/BigQuery-~30--35%25%20Cost%20Reduction-green)

> **Delivered ~$2.3M in annual cloud savings across 8+ engineering teams** by building a real-time cost attribution and optimization governance platform — shifting the organization from reactive cost discovery to proactive spend management.

---

## 🧩 The Problem

Cloud costs grow rapidly in large organizations without clear attribution to teams, services, or workloads.

Engineering teams lacked visibility into which queries, dashboards, or services were driving spend — leading to inefficiencies and budget overruns. Without real-time insights, cost spikes were discovered after the fact, making corrective action expensive and slow.

The core challenge wasn't technical — it was behavioral: teams couldn't optimize what they couldn't see.

---

## 💡 The Solution

Built a centralized **Cloud Cost Intelligence Platform** that provides real-time visibility into cloud spend and usage across services, teams, and workloads.

The platform attributes costs to individual teams, surfaces high-cost queries and workloads, and enforces governance through dashboards and optimization workflows — enabling proactive spend management at scale.

---

## 📊 Program Impact

| Metric | Result |
|---|---|
| Annual Cloud Savings | ~$2.3M |
| BigQuery Cost Reduction | ~30–35% |
| Engineering Teams Onboarded | 8+ |
| Cost Attribution Coverage | End-to-end (user → service → dashboard) |
| Insight Mode | Real-time |

---

## 🏗️ Architecture

```
            ┌────────────────────────────┐
            │   Cloud Billing + Logs     │
            │  (GCP Billing API / AWS)   │
            └────────────┬───────────────┘
                         │
            ┌────────────▼────────────┐
            │   Data Ingestion Layer  │
            │ (Audit Logs / Metrics)  │
            └────────────┬────────────┘
                         │
            ┌────────────▼────────────┐
            │   Processing Layer      │
            │ (Aggregation / Mapping) │
            └────────────┬────────────┘
                         │
    ┌────────────────────▼────────────────────┐
    │      Cost Attribution Engine            │
    │ (User • Service • Dashboard Mapping)    │
    └────────────┬───────────────┬────────────┘
                 │               │
    ┌────────────▼──────┐ ┌──────▼────────────┐
    │ Optimization Rules │ │ Visualization     │
    │ (Scheduling, Tuning│ │ (Grafana Dashboards│
    │  Partitioning)     │ │  + Alerting)      │
    └───────────────────┘ └───────────────────┘
```

**Key components:**
- **Ingestion Layer** — Pulls billing and audit log data from GCP Billing API and Cloud Monitoring
- **Attribution Engine** — Maps cost to teams, users, dashboards, and individual services
- **Optimization Rules** — Identifies inefficiencies (unpartitioned tables, high-frequency queries, idle resources)
- **Visualization** — Grafana dashboards surfacing actionable cost breakdowns in real time

---

## 🎬 Platform Outputs

The platform delivers:
- Real-time cost dashboards broken down by team, service, and workload
- High-cost query identification with optimization recommendations
- Scheduling and partitioning recommendations for BigQuery
- Cost trend analysis and anomaly detection
- Attribution reports for engineering leads and finance stakeholders

---

## ⚙️ How It Works

1. **Ingest** — Billing logs and usage metrics are pulled from GCP Billing API and Cloud Monitoring into a centralized pipeline
2. **Attribute** — Costs are mapped to users, dashboards, and services via the Attribution Engine
3. **Analyze** — The optimization engine identifies inefficiencies: high-frequency queries, unpartitioned tables, idle resources
4. **Surface** — Insights are pushed to Grafana dashboards, enabling teams to take targeted action
5. **Govern** — Teams review spend weekly; optimization recommendations are tracked to closure

---

## ⚙️ Setup

### Prerequisites
- Python 3.9+
- GCP service account with Billing and BigQuery permissions (or equivalent AWS IAM role)
- Access to Cloud Billing export (BigQuery sink)

### Install
```bash
git clone https://github.com/yourusername/cloud-cost-intelligence-platform.git
cd cloud-cost-intelligence-platform
pip install -r requirements.txt
```

### Run
```bash
python main.py
```

---

## 🧪 Example

**Input:** GCP Cloud Billing export + BigQuery audit logs + Cloud Monitoring metrics

**Output:**
- Cost attribution dashboard by team and service
- High-cost query list with optimization recommendations
- Weekly savings opportunity report with projected impact

---

## ⚖️ Tradeoffs & Design Decisions

**Why visibility-first over automated enforcement:**
Shipping dashboards before enforcement rules drove faster adoption — teams voluntarily optimized once they could see their own spend. Enforcement without visibility creates friction and resistance.

**Why Grafana over a custom UI:**
Grafana's existing familiarity across engineering teams shortened time-to-adoption. Building a custom UI would have added 6–8 weeks of delivery risk with marginal benefit at this stage.

**What I'd do differently:**
Introduce automated cost guardrails and budget alerts earlier in the rollout. Reactive optimization has diminishing returns — proactive thresholds would have accelerated savings compounding.

---

## 🧠 What I Learned

- **Visibility drives behavior change more effectively than policy enforcement** — showing a team their spend profile creates accountability without mandates
- **Cost optimization is as much a cultural problem as a technical one** — governance frameworks and team rituals matter as much as tooling
- **Attribution granularity is the hard problem** — mapping cost to the right owner at the right level (user vs. service vs. team) requires significant data modeling investment upfront

---

## 🚀 Next Steps

- [ ] Automated cost alerts with Slack/email notifications
- [ ] Budget enforcement policies with soft and hard caps
- [ ] Predictive cost modeling using historical trend data
- [ ] Self-serve optimization recommendations via an internal developer portal

---

## 🛠️ Built With

- **BigQuery** — Cost data storage, query analysis, and aggregation
- **GCP Billing API** — Real-time billing data ingestion
- **Cloud Monitoring** — Usage metrics and audit log collection
- **Grafana** — Dashboard visualization and alerting
- **Python** — Data pipeline, attribution engine, optimization rules
