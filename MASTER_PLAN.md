# ST1519 Agile MLOps CA1 — Team Master Plan

> **Status:** Approved planning baseline — individual-code sharing policy provisional, pending tutor clarification  
> **Course:** Singapore Polytechnic, Diploma in Applied AI & Analytics · AY2026/2027 Semester 2  
> **Project:** SP-buy E-commerce Fraud Detection System  
> **Team:** QiShun (Product Manager), Darryan, Ethan  
> **Team size:** 3  
> **Sprint cadence:** **1 week per sprint**  
> **Repository:** https://github.com/wqs0526/ecommerce-fraud-detection-mlops  
> **Document owner:** QiShun — Product Manager / backlog coordinator  
> **Last reconciled:** 31 October 2026 — Steps 1–4 planning corrections  
> **Source of truth for requirements:** `SOC_AY2627_S2_ST1519_CA1_Spec(1).pdf` (lecturer's CA1 specification)  
> **Execution tracking:** [GitHub repository](https://github.com/wqs0526/ecommerce-fraud-detection-mlops), approved GitHub Issues, Project views and reviewed code/PRs  
> **Implementation baseline (user-reported, 31 Oct):** GitHub setup only; no technical implementation reported  
> **Repository verification:** 24 parent GitHub Issues and 98 sub-issues have been created. Verify the custom Project fields, native dependencies, teammate permissions and actual implementation layout before development.

## Contents

1. [Team rules and deadlines](#0-read-this-first)
2. [Product vision and stakeholders](#1-product-vision-and-stakeholder-value)
3. [Rubric and scoring strategy](#2-rubric-driven-delivery-strategy)
4. [Data requirements](#3-data-scope-and-controls)
5. [Proposed architecture](#4-proposed-end-to-end-architecture)
6. [Provisional individual-work policy](#provisional-academic-integrity-and-repository-policy-tutor-clarification-pending)
7. [GitHub workflow and repository](#5-github-delivery-structure)
8. [Team roles and independent deliverables](#6-team-roles-and-collaboration)
9. [Weekly sprint roadmap](#7-one-week-sprint-roadmap-and-milestones)
10. [Integration contracts and evidence corrections](#integration-contracts-and-evidence-corrections-planning-steps-34)
11. [Definition of Done](#8-technical-definition-of-done)
12. [Testing and evidence](#9-test-strategy-and-evidence-checklist)
13. [Model selection protocol](#10-model-experiment-and-promotion-protocol)
14. [Demo playbook](#11-demo-runbook)
15. [Risks and decisions](#12-risks-mitigations-escalation)
16. [Tutor-dependent decisions](#13-team-decisions-to-confirm)
17. [Weekly reporting](#14-weekly-product-manager-check-in-template)
18. [Project completion criteria](#15-definition-of-overall-project-completion)

---

## 0. Read this first

This is our shared execution guide, **not a replacement for the official CA1 specification**. We aim to deliver a reliable, reproducible, demonstrable MLOps solution that satisfies **every assessable requirement**, explains the engineering decisions clearly, and supports all team members at interview. An **A is our target, not a guaranteed outcome**.

**Rules for everyone:**
1. Read your GitHub Issue's **Description, Business Value, Acceptance Criteria, Dependencies, and Definition of Done** before starting.
2. For **permitted shared group code**, work on an Issue-backed branch, create a pull request (PR), and obtain teammate review before merging where practicable. Individually assessed code remains separately controlled pending tutor clarification.
3. Communicate blockers early; **do not wait** for unrelated work. Parallelise using agreed interfaces and representative local test data.
4. Every member must independently train **at least two model versions** and independently complete their **individual business analytics and Prefect submission**. **Do not share individual code or writing**.
5. The lecturer's new interview batch URLs **must not be obtained or processed before the scheduled interview**.
6. Use an approved **web-based** GenAI product for the specific robust-MLflow-architecture conversation (fewer than 10 prompting rounds); **do not use local coding agents** for that specified research task. Declare AI use accurately.
7. Never commit secrets, access keys, passwords or real `.env` files.
8. A PBI is only **Done** when its acceptance criteria and evidence are verified, not when code merely runs once.

### Key submission dates (Singapore time)

| Milestone | Deadline / window | Deliverable |
|---|---|---|
| **Part 1** | **Friday, 13 Nov 2026, 4:00 PM** | **One group Product Backlog submission template** on Brightspace |
| **Part 2** | **Friday, 27 Nov 2026, 4:00 PM** | Group and individual submission materials; complete SPA survey and integrity / AI declaration requirements |
| **Graded Scrum** | Weekly during lesson time (Weeks 5–6 identified for sync-ups) | Participation, task/PR review, contribution evidence |
| **Interview** | Week 7; tutor assigns slot | ≤10-minute group presentation, live group and individual demos, individual Q&A |

**Late penalty:** 50% deduction for a submission within 24 hours late; zero after 24 hours, subject to the documented exception policy. Plan to finish and verify submissions **before** deadline day.

---

## 1. Product vision and stakeholder value

### Business problem
SP-buy suffers economic and reputational harm from fraudulent orders and refund abuse. Manual review and hard-coded thresholds miss subtle cases and flag legitimate loyal customers. Trust & Safety analysts have limited time for daily investigation.

### Product vision
Build a repeatable fraud-detection MLOps workflow that turns newly supplied labelled CSV batches into **validated/cleaned data in AWS RDS**, **retrained and tracked ML experiments in MLflow**, and **up-to-date operational fraud insights via individually built Prefect flows**.

### Stakeholders and outcomes

| Stakeholder | Need | Evidence of value |
|---|---|---|
| **Trust & Safety Analyst** | Identify risky patterns while minimising unnecessary review of legitimate orders | Appropriate model evaluation, defensible feature choices, 3 insightful analytics queries and visualisations **per student** |
| **Operations Team** | Supply labelled customer/order/fraud data with consistent processing | A pipeline accepts **three URLs**, validates, transforms and loads a new batch, then triggers retraining |
| **IT Infrastructure Manager** | Maintain deployment and change configurations safely | Documented Docker/Elastic Beanstalk deployment, RDS, externalised configuration, more robust MLflow architecture |
| **AI/ML Team** | Compare, iterate and select reliable models | MLflow runs, params/metrics/artifacts, team model comparison, two registered models, champion promotion |

**Non-goals unless explicitly requested:** live transaction scoring API, customer-facing application, real-time streaming, dashboard web application, payment enforcement, automated order cancellation and additional AWS services not supported by Learner Lab. Avoid scope creep.

---

## 2. Rubric-driven delivery strategy

The percentages below are **the rubric's allocation within CA1**, and together total 100%. CA1 contributes **40% of the module grade**.

| Rubric | Weight | What we must visibly prove | Primary PBIs |
|---|---:|---|---|
| **A. Data Exploration** | **10%** | Data issues identified; justified cleaning, transformation and feature engineering; reusable Python code | 01–04 |
| **B. ETL Pipeline** | **25%** | Python automation of new CSV ingestion → cleaning/transformation → AWS RDS → all team models → MLflow; clear code and reliable **≤3-minute** demo | 12–16, 23 |
| **C. ML Experiments** | **25%** | Shared MLflow on Docker/Elastic Beanstalk, meaningful model iterations, experiment and artifact tracking, registry/champion, robust storage design | 05–11, 14 |
| **D. Agile & Scrum** | **15%** | Complete, specific PBIs; sensible task allocation; active scrum, PR and teammate review | 21–22 |
| **E. Interview / Demo / Q&A** | **10%** | Logical ≤10-minute presentation; live MLflow and fresh-batch processing; confidently explain code and architectural decisions | 16, 23–24 |
| **F1. Individual Analytics** | **5%** | Each student independently produces **3 meaningful RDS-based business queries**, interprets and visualises results | 17–18 |
| **F2. Individual Prefect** | **5%** | Each student's own local Prefect server/flow/tasks reliably gives refreshed analysis and minimum log output | 19 |
| **F3. Advanced AWS Prefect** | **5%** | Healthy Prefect server on Elastic Beanstalk with RDS backend and connected flow service | 20 |

**High-grade strategy (recommended, not additional formal requirements):**
- Prioritise the **50% combined ETL + ML experiments** foundation early; don't trade reliable integration for an elaborate optional feature.
- Make results explainable: show evidence of **why** an issue was cleaned, feature engineered, or model revised.
- Treat **false positives, recall, precision, PR-AUC and review workload** as important fraud-detection trade-offs; do not rank models on accuracy alone when fraud is rare.
- Demonstrate **repeatability and observability**: clean run identifiers, row-count checks, training metadata, meaningful logs and fast failure messages.
- Protect time for F3 because it has **5% on the individual rubric**, even though the specification calls it an advanced challenge. **Ask the tutor to clarify whether and how F3 is awarded per member** and prioritise accordingly.
- Prepare each member for individual Q&A on **the entire team's major architectural and modelling decisions**, not only their own code.

---

## 3. Data scope and controls

### Supplied historical datasets

| File | Purpose | Important fields from specification |
|---|---|---|
| `customers_base.csv` | Customer history | `country_code`, `customer_id`, `mobile_verified`, `num_orders_last_50days`, `num_cancelled_orders_last_50days`, `num_refund_orders_last_50days`, `total_payment_last_50days`, `num_associated_customers`, `first_order_datetime` |
| `orders_base.csv` | Order records | `country_code`, `order_id`, `collect_type`, `payment_method`, `order_value`, `num_items_ordered`, `refund_value`, `order_date` |
| `labels_base.csv` | Ground-truth label and customer-order link | `country_code`, `order_id`, `customer_id`, `is_fraud` (`1` fraud, `0` not fraud) |

### New batches
- Receive `customers_XXX.csv`, `orders_XXX.csv`, `labels_XXX.csv` through **public URLs**; the suffix varies.
- Treat the three files as one logical batch. Require matching inputs; validate before modifying persistent tables.
- Do not assume file row counts, order IDs, country codes, missingness or category levels match the base files.
- Preserve traceability of input URLs/batch identifier, ingestion timestamp, accepted/rejected counts and execution status where feasible.
- Use **explicit keys and join validation**. The labels table relates an order and customer; decide and document uniqueness at the appropriate level. Avoid accidental many-to-many row multiplication and silently unmatched labels.
- Keep data cleaning rules identical for historical and newly received data; no ad hoc manual fixes during demo.

### Critical model validity checks
- Inspect missingness, duplicates, invalid dates/ranges, imbalanced classes, unusual transaction values and categorical levels **before** choosing transformations.
- **Leakage audit:** check whether `refund_value`, prior refund statistics, or other fields would actually be available at order-review time. The specification lists them, but availability timing is not defined. Document assumptions and compare a leakage-safe feature subset if necessary. Never present post-outcome information as a genuine pre-shipment predictive feature without qualification.
- Split train/validation/test with a documented reproducible strategy; consider customer-level grouping or time ordering where justified to avoid overly optimistic evaluation.
- Fit preprocessing **only on training data**, then apply learned transformations to validation/test/new batches.
- Avoid resampling the validation/test distributions. If handling imbalance, resample or apply class weights only to training.
- Select a primary metric aligned to fraud-review capacity (e.g., precision/recall and PR-AUC) **after inspecting class prevalence**. Include confusion matrix, class-specific error analysis, and rationale for the champion.
- Note: the official dataset schema alone does **not** establish actual data quality problems, fraud prevalence or best algorithm. These must be discovered empirically.

---

## 4. Proposed end-to-end architecture

```text
Historical CSVs (base)         New labelled batch (3 public URLs)
          |                                    |
          +------------------+-----------------+
                             v
                  Python ingestion + validation
                             |
                   Reusable clean / transform
                             |
                  AWS RDS MySQL (latest data)
                      /                \
                     v                  v
           Team ML training         Individual analytics
           (3 members × ≥2)          (each student ×3 queries)
                     |                  |
          MLflow tracking / registry    Prefect local flow/tasks
            (Docker on EB)                |
                     |                  v
         Compare top 2; champion       Logs + plots / reports
                     |
                Model artifacts
```

**Required technologies:** Python, Jupyter, AWS RDS (MySQL), AWS Elastic Beanstalk + Docker (MLflow), MLflow tracking/model registry, and each student's Prefect installation. `pandas`, `matplotlib` and `seaborn` for individual analysis. The official brief requires AWS Academy Learner Lab-compatible services for MLflow improvements.

### Proposed engineering interfaces (agree early)

| Interface | Proposed contract | Responsible lead (TBD) |
|---|---|---|
| Input | CLI accepts `--customers-url`, `--orders-url`, `--labels-url`, with optional `--batch-id` | ETL lead |
| Processing | Shared importable Python cleaning/feature functions, stable schema and versioned rules | Data lead |
| RDS | Documented tables, primary keys, constraints, connection env variables and upsert/duplicate policy | DB lead |
| Model training | Each member exports a callable training entrypoint accepting training data/context and returning run information | All 3; ML coordinator |
| MLflow | Common tracking URI, experiment naming convention, logged params/metrics/model artifacts and registration criteria | MLflow lead |
| Analytics | Each student's independently written Prefect flow queries latest team RDS and publishes output/logs | Each student |
| Orchestration | One command to process batch, update RDS and run all training tasks | Integration lead |

The CLI names, table design and code-level interfaces above are **recommendations**, not stated file or API requirements in the lecturer's brief. Decide them as a team and update this section once agreed.

### Storage and deployment resilience
- Initial MLflow: Docker container on Elastic Beanstalk with SQLite backend and local artifact folder is acceptable as the **baseline** in the specification.
- Identify risks of container-local SQLite/artifacts (replacement/redeployment, persistence, contention and recoverability).
- Complete the documented short **web-based GenAI** exploration; choose a better backend/artifact approach that works in Learner Lab, implement changes, test persistence where possible, and record changed services.
- **Do not assume** S3 permissions, RDS engine/permissions or public-access rules: verify Learner Lab availability and budget first. Avoid exposing DB ports publicly where unnecessary.
- Externalise RDS hostname/port/user/password, MLflow URI and other environment-specific values. Provide `.env.example` with placeholders only.

---

## Provisional academic-integrity and repository policy (tutor clarification pending)

**Decision status: OPEN — 31 October 2026.** This is a risk-control measure while the team awaits the lecturer's decision, not a claim that the lecturer approved any particular GitHub storage or collaboration arrangement.

### Group and individual boundaries

- **Shared group work:** Team-developed data ingestion, reusable cleaning and features, AWS RDS and MLflow infrastructure, common orchestration interfaces, architecture contracts, group documentation, and Scrum records may be coordinated in the shared repository under normal team review, subject to lecturer rules.
- **Independently assessed work:** Every member independently develops at least two model versions, three business analytics queries, accompanying visualisations, one local Prefect workflow, any individually claimed advanced AWS Prefect implementation, and any assessed individual writing.
- **Precaution until tutor reply:** Keep individually assessed source code and writing in separate independently controlled workspaces (local or individually private repositories). Do **not** place these files in shared GitHub branches/folders accessible to teammates or exchange them directly. Shared GitHub Issues may record the task, high-level progress, safe evidence, and agreed interfaces; they do not require uploading individually assessed code into the shared repository.
- **Existing sub-issue language:** For 05.T1–T3, 06.T1–T3, 17.T1–T3, 18.T1–T3, 19.T1–T3, 20.T2–T4, and 24.T2–T4 (21 issues), interpret instructions to "commit to GitHub" or "share evidence" as **only to the student's independently controlled workspace or as permitted by the tutor**. Do not disclose private independent implementation or writing in team-readable issue descriptions/attachments.
- **Group retraining integration:** PBI-14 still must automatically run the required independently developed team models. Agree on input/output schemas and callable model contracts without exchanging individual implementation code. The actual packaging, execution and permitted access mechanism must be confirmed with the tutor before integrating individually assessed code into shared systems. Do not claim this is already resolved.
- **Shared evidence:** Avoid publishing credentials, personal data, forbidden assessment code, or sensitive screenshots. Preserve individual authorship and commit history where allowed.

### Questions for tutor (decision pending)

1. May independently developed code and individual writing be stored in separate paths or branches of the shared repository, or must each member use a private workspace?
2. May teammates inspect/review independently assessed code for integration, or only discuss interfaces and outputs?
3. How may the shared ETL/retraining orchestrator execute independently developed model implementations without breaching individual-work rules?
4. What are the required individual submission locations and formats, including separately assessed advanced AWS Prefect work?

**Decision record:** Tutor clarification not yet received; owner: QiShun; requested/response date: **TBD**; final rule: **TBD**. Once the lecturer replies, document the exact approved constraints and update the affected issues, repository access rules and integration design. Do not mark the pending questions completed in checklists yet.

---

## 5. GitHub delivery structure

### Current planning state (parent and sub-issues created; verify custom Project settings)
- GitHub repository and Project exist.
- **24 created parent PBIs and 98 created sub-issues across 6 Epics**; hybrid types: User Story, Feature, Technical Enabler, Spike and Bug (bugs created as needed).
- Fibonacci story points are provisional, not a promised amount of hours.
- Project views exist: **Product Backlog**, **Sprint Board**, **Sprint Planning**.
- The issue descriptions document dependencies; verify **native** GitHub issue relationships in the Project UI. **Blocked by** is a strict prerequisite; **Relates to** indicates collaboration; **Parent / sub-issue** links must be checked rather than inferred from titles.
- **Approved planned owners and sprint allocations are documented below.** Confirm that GitHub Project custom fields and actual team commitments match; the conditional advanced work remains uncommitted.

### Epics and traceability

| Epic | Purpose | PBIs |
|---|---|---|
| **E1** Data Exploration & Preparation | Investigate, clean and engineer reliable features | 01–04 |
| **E2** ML Model Development & Registry | Train, evaluate, log and champion models | 05–08 |
| **E3** MLflow Infrastructure & Architecture | Shared deployment and more robust AWS design | 09–11 |
| **E4** Automated ETL & Database | RDS, batch processing, retraining and reliability | 12–16 |
| **E5** Business Analytics & Prefect | Independent insights, visualisations and flow automation | 17–20 |
| **E6** Agile Management, Testing & Delivery | Backlog, scrum, integration and submission | 21–24 |

### Approved complete PBI index (planning baseline, 31 October 2026)

| PBI | Title | Epic | Accountable lead | Sprint | Parent SP | Sub-issues |
|---|---|---|---|---|---:|---:|
| [01](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/4) | Explore Historical Datasets | E1 | QiShun | S1 | 5 | 4 |
| [02](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/5) | Implement Reusable Data Cleaning | E1 | Ethan | S2 | 5 | 3 |
| [03](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/6) | Engineer Fraud Detection Features | E1 | QiShun | S2 | 8 | 3 |
| [04](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/7) | Validate Data Processing Consistency | E1 | Ethan | S3 | 5 | 3 |
| [05](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/8) | Develop Baseline Fraud Detection Models | E2 | All three | S2 | 5 | 4 |
| [06](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/9) | Optimise and Compare Model Versions | E2 | All three | S3 | 8 | 4 |
| [07](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/10) | Track Machine Learning Experiments | E2 | Darryan | S2 | 5 | 3 |
| [08](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/11) | Register and Promote Champion Model | E2 | Darryan | S3 | 5 | 2 |
| [09](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/12) | Deploy MLflow on AWS Elastic Beanstalk | E3 | Darryan | S1 | 8 | 4 |
| [10](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/13) | Investigate Robust MLflow Architecture | E3 | Darryan | S2 | 3 | 2 |
| [11](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/14) | Implement and Document Robust MLflow Infrastructure | E3 | Darryan | S3 | 8 | 3 |
| [12](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/15) | Provision AWS RDS MySQL Database | E4 | Ethan | S1 | 5 | 4 |
| [13](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/16) | Automate Data Ingestion and Loading | E4 | QiShun | S3 | 8 | 4 |
| [14](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/17) | Automate Retraining on Updated Data | E4 | Darryan | S3 | 8 | 4 |
| [15](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/18) | Externalise System Configuration | E4 | Ethan | S2 | 3 | 2 |
| [16](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/19) | Ensure Pipeline Reliability and Performance | E4 | Ethan; QiShun benchmarks | S4 | 8 | 4 |
| [17](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/20) | Develop Fraud Business Analytics | E5 | All three | S3 | 5 | 3 |
| [18](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/21) | Visualise Fraud Trends and Patterns | E5 | All three | S4 (start S3) | 3 | 3 |
| [19](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/22) | Automate Analytics with Prefect | E5 | All three | S4 (start S3) | 8 | 4 |
| [20](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/23) | Deploy Prefect to AWS | E5 | QiShun provisional; individual tasks all three | Conditional S4 | 13 | 5 |
| [21](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/24) | Establish GitHub Product Backlog | E6 | QiShun | S0–S2 | 3 | 4 |
| [22](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/25) | Manage Sprint Planning and Scrum Reviews | E6 | QiShun coordinates | S1–S4 | 3 | 16 |
| [23](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/26) | Verify End-to-End System Integration | E6 | Ethan | S4 | 5 | 4 |
| [24](https://github.com/wqs0526/ecommerce-fraud-detection-mlops/issues/27) | Prepare Submission and Live Demonstration | E6 | Ethan coordinates | S4 | 5 | 6 |

**Totals:** 24 parent PBIs; **98** sub-issues; **142 SP** across all parents (**129 SP mandatory/cross-sprint plus 13 SP conditional PBI-20**). Sub-issues remain unpointed to prevent double counting. PBI-21/22 are cross-sprint coordination and should not be double-counted when reporting sprint throughput.

**Planned sprint distribution excluding cross-sprint coordination and conditional advanced work:** S1 = 18 SP (12 tasks); S2 = 29 SP (17 tasks); S3 = 47 SP (23 tasks); S4 = 29 SP (21 tasks). Cross-sprint PBI-21/22 = 6 SP (20 tasks); conditional PBI-20 = 13 SP (5 tasks). Sprint 3 is capacity-sensitive, not automatically committed until team confirms capacity.

**PBI-05, PBI-06, PBI-17, PBI-18 and PBI-19 are shared tracking umbrellas**, **not substitutes** for three independent student implementations. During sprint planning each student should separately track their own work/evidence without sharing their individual submission code or writing.

### Repository-specific onboarding and suggested layout (not asserted to exist)

**Repository:** [`wqs0526/ecommerce-fraud-detection-mlops`](https://github.com/wqs0526/ecommerce-fraud-detection-mlops). The team reports that the repository is now public; its current folders and access permissions still need to be checked. The parent issues are numbered #4–#27 and the planned sub-issues extend through #125; however, do **not** infer the current directory listing, commit history or GitHub Project custom fields without verification. QiShun should verify public access and grant teammates repository write and Project access as appropriate; avoid publishing credentials or unnecessary public data. **Do not create new folders purely to match this example**—first inspect `README`, branches, `.github/ISSUE_TEMPLATE`, existing files and team conventions.

**First repository-fit checklist (QiShun leads; all verify):**
- [ ] Confirm all three can view the repository, 24 parent Issues, 98 sub-issues, all Project views and issue relationships.
- [ ] Verify `MASTER_PLAN.md` at the repository root is current, link it from README, and review changes by PR where permitted.
- [ ] Confirm `.gitignore`, `.env.example` and secret-handling instructions before adding cloud configuration.
- [ ] Record actual directories and entrypoints in README; adapt suggested layout instead of assuming it exists.
- [ ] Apply branch protection/review conventions supported by the repository/account; verify they do not block timely merges.
- [ ] Set weekly GitHub Iterations to **7 days** and agree on exact start day.

### Suggested repository layout (adapt after verification)

```text
/
├── README.md
├── MASTER_PLAN.md                  # this document
├── .gitignore
├── .env.example                    # placeholders, no secrets
├── docs/
│   ├── architecture.md
│   ├── data_dictionary.md
│   ├── decisions.md                 # decisions / rationale / trade-offs
│   ├── deployment.md
│   ├── demo_runbook.md
│   └── testing.md
├── notebooks/
│   └── eda.ipynb
├── src/
│   ├── ingestion/
│   ├── preprocessing/
│   ├── database/
│   ├── training/
│   └── orchestration/
├── infrastructure/
│   └── mlflow/
├── tests/
└── individual/                     # only if lecturer permits this arrangement
    ├── member_a/                   # independent authoring; don't share code/writing
    ├── member_b/
    └── member_c/
```

**Do not assume individual submissions belong in the shared repository.** The course instructions as recorded in this plan prohibit sharing individual code or writing; tutor clarification on storage/access is pending. Safer default: keep individual implementations in private, independently authored workspaces and only share non-code interface requirements and high-level progress; confirm permissible submission location with tutor.

### Branch / PR convention
- One Issue → one feature branch where practicable: `feature/pbi-13-batch-ingestion`, `infra/pbi-09-mlflow-eb`, `docs/pbi-24-demo-runbook`.
- PR contains `Closes #<issue>` where applicable, brief summary, test evidence, screenshots/log references when useful, and known limitations.
- At least one teammate reviews major shared PRs; reviewer checks requirements and tests, not just formatting.
- Avoid direct merges to main for major changes; resolve conflicts and keep a stable demo-capable main branch.
- Update Project status and relevant Issue comments during scrum. Never close a partially completed PBI without documenting the gap.

### Scrum operating rhythm (suggested)
- **Backlog refinement:** Product Manager reviews priority, acceptance criteria, dependencies and provisional estimate with team.
- **Sprint planning (Week 4):** pick a realistic subset; split into sub-issues; assign an owner/reviewer; define sprint goal.
- **Weekly graded scrum:** each member states completed evidence, next work, blockers, dependencies and PRs reviewed. Show board changes and meaningful technical decisions.
- **Mid-sprint integration sync (recommended):** test shared interfaces, merge small PRs early and time the pipeline.
- **Sprint review / retrospective:** demonstrate actual working results, record failed assumptions and adjust backlog/estimates.

---

## 6. Team roles and collaboration

The following shared-workstream responsibilities reflect the agreed planning baseline; confirm reviewer assignments and any later changes during sprint planning. Each PBI should have a named owner and reviewer. Ownership of shared work does not replace the individual requirements.

| Member | Shared focus | Accountable parent PBIs / coordination | Review and assistance |
|---|---|---|---|
| **QiShun — Product Manager** | Backlog, EDA, features, ETL and team coordination | **01, 03, 13, 21**; coordinate **22**, 16.T3 benchmarking, 23.T1 integration, 24.T5 presentation; **20 provisional** | Aligns data/ETL interfaces with Ethan and retraining interface with Darryan; tracks milestones and sprint evidence |
| **Darryan** | MLflow infrastructure, model registry and automated retraining | **07–11, 14**; support group model tasks 05/06 and retraining verification 16.T4 / 23.T2 | Coordinates reproducible experiment tracking, training contracts and retraining integration |
| **Ethan** | Cleaning, data consistency, RDS, external configuration, QA, final acceptance and submission | **02, 04, 12, 15, 16, 23, 24**; supports 13.T3 database loading | Coordinates data validation, integrity testing, acceptance evidence and group submission check |

**Shared parent PBIs:** **05, 06, 17, 18, 19** have an individually owned sub-issue for each member. Shared parent story points do not assign all individual effort to one person. **PBI-20 is conditional:** 20.T1 feasibility, 20.T2–T4 independently attributable deployment tasks, 20.T5 verification; no tutor approval or feasibility success is implied.

**All three independently complete:** at least two ML model versions each; three meaningful business analytics queries each; individually authored visualisations/analysis and local Prefect flow each; individual submissions and Q&A. Do **not** share individual code or writing, as specified by the lecturer.

### Independent deliverables tracker

| Requirement | QiShun | Darryan | Ethan |
|---|:---:|:---:|:---:|
| ML model version 1 and 2, logged and explained | ☐ | ☐ | ☐ |
| Three independently authored business queries | ☐ | ☐ | ☐ |
| Independently authored plots and interpretations | ☐ | ☐ | ☐ |
| Own working Prefect server, tasks and flow | ☐ | ☐ | ☐ |
| Own flow demonstrated within 180 seconds | ☐ | ☐ | ☐ |
| Individual submission and declarations completed | ☐ | ☐ | ☐ |
| Understand major team architecture and modelling decisions | ☐ | ☐ | ☐ |

### Team working agreements

- Weekly planning, sprint review and retrospective follow the **one-week iteration** cadence; attend lecturer-scheduled scrum meetings.
- Plan based on actual availability and use Fibonacci story points for relative complexity, not hours. Split oversized PBIs into reviewable sub-issues.
- Each shared PBI has an owner, a reviewer, testable acceptance criteria and evidence linked in its GitHub Issue.
- Use early PRs, interface contracts and short integration checks so different workstreams can progress in parallel.
- Support cross-training on architecture decisions so every member can answer individual Q&A.
- Do not post credentials or independently authored submission code/writing into shared discussions.

---

## 7. One-week sprint roadmap and milestones

**Approved planning cadence:** seven calendar days; Monday–Sunday is a team planning convention, not an additional requirement imposed by the lecturer. GitHub Iteration fields must be checked against these dates.

| Sprint | Dates (SGT) | Approved parent PBI allocation | Story points | Sub-issues | Required focus and evidence |
|---|---|---|---:|---:|---|
| **S0 — Backlog setup** | 26 Oct–1 Nov | **21 begins; 22 planning** | Cross-sprint | Part of cross-sprint 20 | GitHub backlog, ownership, estimation and dependencies; 24 parents/98 sub-issues created; technical implementation not yet verified |
| **S1 — Foundations** | 2–8 Nov | **01, 09, 12** | **18** | **12** | Historical EDA, initial Docker/Elastic Beanstalk MLflow, AWS RDS; minimal safe env configuration in PBI-09 without waiting for PBI-15 |
| **S2 — Data/models and Part 1** | 9–15 Nov | **02, 03, 05, 07, 10, 15** | **29** | **17** | Reusable cleaning/features, all three individual baselines, MLflow logging conventions, robust-architecture research and formal configuration; Part 1 submitted **Fri 13 Nov 4 PM** |
| **S3 — Retraining integration** | 16–22 Nov | **04, 06, 08, 11, 13, 14, 17** | **47** | **23** | Validation; individual model improvement; top-two registry/champion; persistent MLflow; three-URL ETL, combined-data retraining; individual analytics. Start PBI-18/19 preparation if feasible. **Target permitted first end-to-end benchmark: Thu 19 Nov** |
| **S4 — Mandatory verification and submission** | 23–29 Nov | **16, 18, 19, 23, 24** | **29** | **21** | Full reliability/performance and acceptance tests; each member's own three charts and local Prefect **server + flow + tasks**; submission and demo preparation **before Fri 27 Nov 4 PM** |
| **Cross-sprint management** | S0–S4 | **21, 22** | **6** | **20** | Part 1 submission, backlog and weekly graded Scrum/PR review evidence; count parent SP only once |
| **Advanced conditional work** | Conditional S4 | **20** | **13** | **5** | Feasibility gate; AWS-hosted Prefect and independently attributable evidence only if feasible and permitted; do not displace mandatory work |

**Mandatory parent subtotal excluding cross-sprint management:** 123 SP. **Including PBI-21 and PBI-22:** 129 SP. **Including conditional PBI-20:** 142 SP. These are plan estimates, not measured capacity or a promise that all work will fit.

**Fixed deadlines:** Part 1 — **13 November 2026 at 4 PM SGT**; Part 2 — **27 November 2026 at 4 PM SGT**; Week 7 interview time set by tutor. **The Part 2 deadline occurs two days before Sprint 4 ends.** Submit and verify deliverables before that deadline; the remaining Sprint 4 days do not extend the assessment deadline.

**Important sequencing corrections:** PBI-09 (S1) is **not blocked by PBI-15 (S2)**; secure minimal configuration is sufficient for the initial MLflow server, with standardisation later. PBI-07 logging conventions/utilities can start alongside PBI-05; its end-to-end verification depends on model runs. PBI-17 queries can start against existing historical RDS data before PBI-13 incoming-batch ETL completes, but freshness testing depends on that ingestion. PBI-16.T3 is allocated to S4, with a **planned early Sprint 3 integration/baseline checkpoint** coordinated with PBI-13/14.

**Risks:** Sprint 3 has the highest relative commitment (47 SP) and several hard integration prerequisites. Track a working vertical slice early, address missing contracts, and renegotiate sprint commitment when actual capacity or blockers dictate. No test is passed merely because its GitHub checklist exists. **Do not access the tutor-reserved interview CSV URLs before the interview.**

### One-week sprint operating procedure

- **Day 1 — Planning (15–30 min):** review acceptance criteria, estimate capacity, select sprint goal, put selected PBI sub-issues into GitHub Iteration, assign owners and PR reviewers.
- **Days 2–5 — Build and daily async check-in:** comment in assigned Issues with `Done / Next / Blocker / Evidence`; open small PRs; hold one midweek integration smoke test.
- **Day 6 — Review and QA:** demonstrate actual outputs, verify acceptance criteria, measure elapsed pipeline time, review PRs, reassign cross-component blockers.
- **Day 7 — Retrospective and replan:** capture improvements, carry unfinished work explicitly, update GitHub views and next-sprint backlog.
- **Scheduled graded lesson scrum always takes precedence** over this illustrative rhythm; record attendance, peer reviews and decisions as evidence.

### Sprint goal and completion standards

A sprint is **not completed** simply because tickets moved to Done. Its planned demonstration must be usable from the latest integrated code, accepted by at least one teammate, and accompanied by linked evidence. Carry unfinished PBIs forward; do not silently reduce their acceptance criteria to fit the seven-day window. If a weekly sprint starts on another day, update dates in the GitHub Iteration field and in this plan consistently.



### Integration contracts and evidence corrections (planning Steps 3–4)

- **PBI-19 individual local Prefect (issues #103–105):** Each member must install/start their own **local Prefect server**, configure the API endpoint, demonstrate flow runs/task states/logs in the local UI, execute three own RDS analytics queries and regenerate three charts in **under 180 seconds**. These acceptance criteria were merged into the individual GitHub descriptions; actual execution has not yet been demonstrated.
- **13.T4 ETL completion contract (issue #92):** Three configurable URLs, batch identity, committed row counts, explicit success/failure and only report success after the required RDS commit. Downstream retraining must not start after a failed/incomplete load.
- **14.T2 common model training contract (issue #94):** Agree on feature/label inputs, model owner/version, dataset/batch context, metrics, artifact references and errors. The mechanism for integrating independently assessed implementations remains **pending tutor clarification**.
- **14.T3 retraining orchestrator contract (issue #95):** Consume verified ETL result; run all required member models from combined historical + new labelled RDS data; record per-model status, MLflow run references and total result; required model failure cannot yield overall success. Confirm lecturer's precise interpretation of the model-count requirement before reducing the six-version planning scope.
- **16.T3 runtime benchmark (issue #109):** Attempt the first **complete** permitted end-to-end benchmark by **19 Nov (S3 planning target)**. Record stage times, total wall time, expected/actual model runs, data sizes and MLflow evidence. Final qualification requires repeated complete successful group runs **under 180 seconds**, not ETL-only timing.
- **Academic integrity:** Do not upload independently assessed source/writing to group-visible paths until tutor clarifies. Group interface documents and permitted shared orchestration code may be developed; final permissible execution/packaging of individual models is unresolved.

## 8. Technical Definition of Done

### Data / feature engineering (PBI-01–04)
- [ ] Jupyter EDA documents actual discovered issues with tables/plots.
- [ ] Cleaning/feature rules have business and technical rationale, plus unit tests where appropriate.
- [ ] CSV joining and identifier uniqueness checked; no accidental row loss or duplication.
- [ ] Train/validation/test leakage and temporal availability assumptions documented.
- [ ] Reusable functions produce consistent schema for base and new batches.

### ML development / tracking (PBI-05–08)
- [ ] Each member has ≥2 distinguishable model versions, with a documented improvement hypothesis.
- [ ] Evaluation includes appropriate metrics for class imbalance and false positives, not accuracy alone.
- [ ] Metrics, key parameters, model files and run identity accessible in MLflow.
- [ ] Team comparison recorded; two models registered; champion designation evident live.
- [ ] Model training callable by automated orchestration, not only interactive notebooks.

### Cloud / data pipeline (PBI-09–16)
- [ ] MLflow responds on Elastic Beanstalk; Docker setup repeatable and documented.
- [ ] RDS schema and connection documented; secrets not committed.
- [ ] Ingestion accepts three publicly accessible URLs for an unknown suffix batch.
- [ ] Validation, cleaning, transformation, load and all training tasks run through one controlled entrypoint.
- [ ] Outputs can be checked in RDS and MLflow, with meaningful batch-tagged logs.
- [ ] Error handling prevents silently corrupted or double-counted data.
- [ ] Realistic end-to-end group execution consistently completes **≤180 seconds** in rehearsals.
- [ ] Robust MLflow alternative explored via compliant GenAI conversation; changed services documented and tested.

### Independent business analytics / Prefect (PBI-17–20)
- [ ] Each student's work is independently authored, using current RDS data.
- [ ] Three meaningful business questions per student have queries, explanations and relevant plots.
- [ ] Local Prefect server and flow/tasks function; each run refreshes results and shows at least query results in flow logs.
- [ ] Individual flow demo consistently completes **≤180 seconds**.
- [ ] If attempted: AWS Prefect server healthy on EB, RDS backend and connected flow service verified.

### Scrum / delivery (PBI-21–24)
- [ ] GitHub board, PBIs, sprint tasks and dependencies reflect real work.
- [ ] Substantial shared PRs reviewed; review comments and resolutions visible.
- [ ] Individual contributions supported by commits, PRs, experiments, tasks and demo evidence.
- [ ] All deliverables and declarations submitted; 10-minute presentation and Q&A rehearsed.

---

## 9. Test strategy and evidence checklist

### Automated tests (recommended)

| Test layer | Scenario | Evidence |
|---|---|---|
| **Schema** | Missing column, wrong type, empty file, invalid label, unknown category | Explicit validation report; no silent write |
| **Keys** | Duplicated IDs, unmatched labels, join multiplicity | Input/output counts and deterministic policy |
| **Transformation** | Base vs suffix batches; date parsing; null/negative values; unseen categories | Stable output columns and unit test assertions |
| **Database** | Fresh insert, retry, rerun same batch, partial failure | Reconciled counts; no unintended duplicates |
| **ML** | Reproducibility, no preprocessing leakage, class imbalance | Documented split, metrics and saved model |
| **MLflow** | Training run parameters/metrics/artifact; registry promotion | Live dashboard confirmation |
| **End-to-end** | Three local/publicly accessible permitted test URLs | One-command run → RDS changes → all runs visible |
| **Performance** | Cold/warm realistic tests, 2+ consecutive runs | Timed group and per-member results ≤180 s |
| **Prefect** | RDS refresh, flow logs, charts after new batch | Each member's own flow run evidence |
| **Recovery** | Temporary network timeout or unavailable service | Actionable failure, safe retry, no data corruption |

### Timing budget (planning target, not a measured result)
Aim to finish **comfortably below** the formal 180-second maximum. Measure actual timings on available hardware and cloud resources. Use a timing table in test logs:

| Stage | Measured time (s) | Notes |
|---|---:|---|
| URL retrieval + validation | TBD | Three CSVs |
| Clean + transform | TBD | Existing + new data handling |
| RDS writes + verification | TBD | Network overhead |
| All team model trainings + MLflow logging | TBD | Must include all members' tasks |
| **Group total** | **TBD / 180 max** | Test repeatably |
| Member 1 Prefect total | TBD / 180 max | Independent run |
| Member 2 Prefect total | TBD / 180 max | Independent run |
| Member 3 Prefect total | TBD / 180 max | Independent run |

Do **not** quietly omit model tasks to meet the time limit. Optimise algorithm choices, feature computation and remote requests while preserving required behaviour.

### Evidence store (suggested)
Keep non-sensitive screenshots/log snippets and short decision records in `docs/` or linked GitHub Issue/PR comments. Capture enough to substantiate claims, but plan to show the **actual live MLflow dashboard** in the interview, as required.

---

## 10. Model experiment and promotion protocol

1. Agree on the **same evaluation dataset/split and metrics** for the team, keeping a true holdout untouched during tuning.
2. Each member logs v1 baseline and v2 meaningful improvement, noting the hypothesis and changed parameters/features.
3. Log dataset/batch version, model family, run owner, parameters, training duration, metrics and artifact metadata to MLflow where feasible.
4. Compare **precision, recall, F1, PR-AUC**, false-positive counts and operational review trade-offs as appropriate to observed imbalance; include runtime for demo feasibility.
5. Select **top two models** through a documented team review; register them in MLflow and designate a **champion**.
6. When new model versions are trained, compare fairly against champion and update the promotion decision with rationale.
7. Never claim generalisation from training-only scores; explain limitations and any uncertainty.

**Suggested naming:** `batch_<suffix>__<member>__<model>__v<version>`; adapt to MLflow's run naming conventions. Avoid putting credentials or sensitive personal data in run names.

---

## 11. Demo runbook

### Pre-demo checks (permitted before interview)
- [ ] Laptop(s), Python environment, dependencies and permitted network access validated.
- [ ] AWS RDS reachable; MLflow Elastic Beanstalk deployment healthy; appropriate local Prefect services ready.
- [ ] Existing history available; trained models / registry visible.
- [ ] Verify all environment variables are set without exposing credentials.
- [ ] Team knows exactly which person runs each step and who explains results.
- [ ] Test commands on **allowed non-interview data only**.

### Live group sequence (tutor-supplied URLs only at assigned slot)
1. Receive the three URLs from tutor.
2. Run the documented one-command ETL interface, passing **only those supplied URLs**.
3. Show concise batch input, processed row counts and RDS query evidence of newly inserted data.
4. Show MLflow **live**: fresh experiment runs for all three members, parameters, metrics/artifacts, model comparison, registered top two and champion.
5. Report measured elapsed time and any controlled validation messages; finish group pipeline within 3 minutes.
6. Each member independently executes their own Prefect flow and shows refreshed query output / charts within 3 minutes per flow.

### Proposed ≤10-minute presentation outline

| Time | Topic |
|---|---|
| 0:00–1:00 | Problem, stakeholders and solution objective |
| 1:00–2:30 | EDA findings, cleaning and feature engineering rationale |
| 2:30–4:30 | Models, comparison, iterative improvement and live MLflow dashboard |
| 4:30–6:00 | RDS/MLflow architecture and robustness decisions |
| 6:00–7:30 | Automated ETL/retraining flow and reliability strategy |
| 7:30–8:30 | Independent analytics / Prefect value (overview only) |
| 8:30–9:30 | Team contribution split, scrum evidence, limitations |
| 9:30–10:00 | Buffer / transition to separately assessed live demo |

**Note:** Tutor may structure the interview so the timed live pipelines occur after presentation. Verify the exact format in advance; do not attempt to cram the full live demo inside the 10-minute presentation unless instructed.

### Individual Q&A preparation
Every student should be able to explain: schema keys, data cleaning rationale, leakage considerations, class imbalance, metric choice, why model v2 changed, why top two/champion were selected, MLflow's backend/artifact architecture, Docker/EB/RDS configuration, safe secrets, orchestration, performance bottlenecks, exception handling, own independent three queries and Prefect code, and meaningful contribution to team PRs.

---

## 12. Risks, mitigations, escalation

| Risk | Impact | Mitigation / trigger |
|---|---|---|
| AWS Learner Lab service restrictions / expiration | Service unavailable at demo | Verify allowed services early; document repeatable deployment; rehearse restart; keep local development fallback (not substitute for graded AWS deployment) |
| MLflow artifact/DB lost on container recreation | Experiment evidence disappears | Improve storage after research; backup/restore plan, recreate-and-retest exercise |
| End-to-end runtime >180 s | Direct demo marks at risk | Benchmark early; profile training/data transfer; use appropriate fast models without omitting member tasks |
| Input batch contains unexpected data | Pipeline fails or corrupts data | Schema validation, safe joins, explicit failures, local variation tests |
| Fraud-target leakage | Misleadingly strong metrics | Time-of-prediction audit and leakage-safe evaluation |
| Individual work shared inadvertently | Academic integrity risk | Independent coding/writing; clarify repository/submission rules with tutor |
| Too much time on advanced AWS Prefect | Core pipeline incomplete | Gate advanced work after stable group pipeline; clarify F3 grading |
| Unbalanced team workload | Delays and weak contribution evidence | Assign reviewer/owner, weekly sync and reallocate based on evidence |
| Last-minute merge or cloud breakage | Demo failure | Freeze feature additions before submission; tested main branch and runbook |
| Tutor batch accessed prematurely | Penalty | Strictly wait until assigned interview slot; use permitted mock data for rehearsals |

**Escalation rule:** If a blocker threatens a milestone, comment on the GitHub Issue, notify the other two team members at the next available sync, identify a workaround and update sprint scope. Do not silently defer the problem.

---

## 13. Team decisions to confirm

This plan intentionally leaves unresolved project decisions visible rather than inventing them.

- [ ] Names / GitHub usernames for 3 members; agree on technical leads and reviewers.
- [ ] Link to actual GitHub repository and Project; update markdown links once known.
- [ ] Confirm actual dataset files have been received; record real observations after EDA.
- [ ] Agree on Python environment, dependencies and model interfaces.
- [ ] Choose AWS RDS schema and ingestion idempotency strategy.
- [ ] Confirm MLflow deployment/storage design within Academy Learner Lab and the compliant GenAI research record.
- [ ] Finalise metrics, data split and champion-promotion rule after observing dataset characteristics.
- [ ] **Pending tutor response:** Confirm where independent code/writing may be stored, whether peer review is permitted, and how the group may invoke independently authored models without sharing source.
- [ ] Clarify advanced F3 Prefect grading per individual with module tutor.
- [ ] Obtain official PB and Part 2 templates; check submission requirements and file naming.
- [ ] Confirm exact Week 7 interview slot and service access conditions.

---

### Additional decisions
- [ ] **QiShun / Darryan / Ethan** accept or adjust the proposed ownership and shared review arrangements; nominate a lead/reviewer per PBI during sprint planning.
- [ ] Agree actual **one-week sprint start day**, iteration naming and lesson-time scrum schedule.
- [ ] **Verify repository and Project access for all members**, give Darryan and Ethan necessary write/Project access, verify AWS Academy Learner Lab, and record the actual directory structure before creating any suggested folders.
- [ ] Agree how to split and estimate three members' independent PBI-17/18/19 work without sharing individual code or writing.
- [ ] Agree minimum vertical-slice completion by Sprint 3 and fall-back plan if cloud services are unavailable.

### Decision and verification register — 31 October 2026

| Decision / check | Current status | Owner | Required follow-up |
|---|---|---|---|
| PBI-09 no longer blocked by PBI-15 | **Resolved — GitHub issue corrected** | Darryan / Ethan | Verify Project native relationship and maintain safe minimal configuration |
| Individual source sharing, review and submission locations | **Open — tutor clarification pending** | QiShun | Record official tutor response; then revise provisional policy and the 21 individual issues if needed |
| Group retraining integration mechanism for individual models | **Open — tutor clarification pending** | Darryan / QiShun | Agree approved packaging/entrypoint mechanism without impermissible source sharing |
| PBI-19 local server/UI requirements | **Descriptions updated; implementation not tested** | All three | Each member independently demonstrates local server/flow/logs and runtime |
| ETL / training / orchestration interface requirements | **Descriptions updated; code interfaces not yet built** | QiShun / Darryan / Ethan | Implement and contract-test 13.T4, 14.T2, 14.T3 |
| First complete group benchmark | **Planned, not executed** | QiShun with Darryan/Ethan | Target 19 Nov using permitted test data; measure complete pipeline |
| Exact minimum model count retrained | **Tutor interpretation to confirm** | Darryan | Maintain six-model-version plan unless official clarification permits a different scope |
| Advanced AWS Prefect individual 5% and metadata backend | **Conditional; clarification and Learner Lab feasibility pending** | QiShun / all | Obtain tutor interpretation; test permissions and supported Prefect metadata engine; Go/No-Go |
| Project custom fields, native parent/child links and iterations | **Not fully independently verified** | QiShun | Audit GitHub Project UI for owner/status/priority/epic/iteration/parent relationships |
| Sprint 3 capacity and reviewer assignment | **To validate at Sprint Planning** | All three; QiShun coordinates | Agree realistic commitment, reviewer ownership and midpoint integration gates |
| Part 1 / Part 2 submission receipts | **Not yet submitted as of 31 Oct** | QiShun / Ethan | Verify actual platform confirmation at fixed deadlines; do not mark completed early |

## 14. Weekly Product Manager check-in template

```markdown
### Scrum update — YYYY-MM-DD
**Sprint goal:**
**Completed PBIs / PRs (links):**
**Evidence / demo:**
**In progress (owner, remaining work):**
**Blockers / dependencies / risks:**
**Models logged per member:** Member 1 __ / Member 2 __ / Member 3 __
**Independent analytics/Prefect status:** M1 __ / M2 __ / M3 __
**Group pipeline timing:** __ s (target ≤180 s)
**Individual pipeline timings:** M1 __ s / M2 __ s / M3 __ s (each ≤180 s)
**Decision(s) and rationale:**
**Next sprint commitments:**
**Reviewer confirmations:**
```

---

## 15. Definition of overall project completion

The team can legitimately declare CA1 delivery-ready only when:

- [ ] Official Part 1 PB template submitted on time; all stakeholder requirements trace to PBIs.
- [ ] EDA and cleaning/feature engineering are evidenced and reusable.
- [ ] RDS stores processed historical and new data, with validated schema and operational loading.
- [ ] Three team members each have **≥2** model versions and MLflow experiment evidence.
- [ ] Two leading models are in the registry and champion selection is demonstrable.
- [ ] Shared MLflow is running on Docker/Elastic Beanstalk; architecture improvements researched and implemented/documented as required.
- [ ] A new **tutor-provided** batch can be ingested **during the interview**, retrain all models, and log fresh runs **within 180 s**.
- [ ] Each member independently provides three meaningful RDS analytics queries, charts/insights and a working Prefect flow **within 180 s**.
- [ ] Advanced Prefect AWS component attempted/completed according to confirmed grading strategy and available time.
- [ ] Submissions, SPA and academic integrity/AI declarations completed; contribution evidence is defensible.
- [ ] ≤10-minute group presentation, live demonstration and individual technical Q&A have been rehearsed.

**Final principle:** **Prove a working, repeatable system with measurable evidence.** Good GitHub organisation supports assessment, but does not replace quality ML experiments, resilient data pipelines, independent student work or a successful live demonstration.

---

*Maintained by the Product Manager. Changes to requirements or acceptance criteria should be reviewed with the team and reflected in the relevant GitHub Issues. If this file conflicts with the lecturer's specification, the specification takes precedence.*
