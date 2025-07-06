# ⭐ STAR STORIES – Abinaya Sankaralingam
### For Amazon Behavioral Interview (All 16 Leadership Principles Covered)

---

## ✅ Bill 64 – PII Purge Compliance Pipeline

**Situation:**  
I led the customer data integration system for a major Canadian bank, responsible for building scalable pipelines for real-time and batch processing. As part of a legal compliance initiative under Quebec’s Law 25 (Bill 64), we had to implement an automated purge system for sensitive PII data.

**Task:**  
Design and deliver a system that ensures timely deletion of customer records while maintaining auditability, traceability, and compliance SLAs.

**Action:**  
- Personally designed the purge pipeline, integrating with metadata and lineage layers.
- Collaborated with legal, security, and audit teams to align on logic, edge cases, and exception handling.
- Enabled lineage tagging of exceptions and tracked the audit trail end-to-end using metadata enrichment.
- Delivered full observability and retry logic to ensure resilience.

**Result:**  
- Achieved **99.6% SLA** for PII data deletion within legal windows.  
- Remaining 0.4% flagged and legally retained as per policy.  
- The pipeline passed **two rounds of internal audits** with zero exceptions and was adopted as a blueprint across two other departments.

**Leadership Principles:** Ownership, Dive Deep, Customer Obsession, Deliver Results, Earn Trust

---

## ✅ ETL Modernization – Legacy to Cloud Transformation

**Situation:**  
At Scotiabank, I was responsible for replacing a decade-old iWay ETL stack that lacked documentation, had high tech debt, and was critical for customer master data.

**Task:**  
Modernize the system into a scalable cloud-native architecture with improved documentation, maintainability, and compliance.

**Action:**  
- Set up the initial cloud infrastructure (Talend Cloud + GCP microservices).
- Reverse-engineered 85+ undocumented flows and categorized them by complexity and priority.
- Migrated high-priority flows to **Spring Boot microservices** for real-time processing and others to **Talend batch pipelines**.
- Created full documentation: process diagrams, logs, SOPs, peer review templates.
- Cross-pollinated modernization learnings with 3 other internal teams.

**Result:**  
- Delivered a **modern modular architecture** with **83% increased throughput**.  
- Enabled **real-time address updates** (from 24 hrs → real-time).  
- Achieved **98% PII purge success** under Quebec Law 25.  
- Reduced onboarding time for new engineers by 60% through documentation.

**Leadership Principles:** Dive Deep, Insist on High Standards, Learn & Be Curious, Ownership, Deliver Results

---

## ✅ Incentive Compensation – Pipeline + Leadership

**Situation:**  
At Comcast, I led the Incentive Compensation data team responsible for pulling Workday performance data, calculating commissions, and feeding dashboards for 25,000+ sales reps.

**Task:**  
Build reliable, accurate, and time-sensitive pipelines to support payroll deadlines and sales motivation.

**Action:**  
- Led a **25+ member onshore–offshore team** with Agile Scrum.
- Integrated HR and sales data, resolved complex rep hierarchy issues.
- Implemented early validation logic for upstream anomalies.
- Facilitated cross-functional syncs with Workday, Salesforce, QA, and business teams.

**Result:**  
- Commission errors reduced by **40%**.  
- Bonus calculation lag dropped from **7 days to <2 days**.  
- Delivered payouts **on time for 6+ consecutive quarters**.  
- Recognized by senior leadership for improved transparency and sales morale.

**Leadership Principles:** Hire & Develop the Best, Deliver Results, Ownership, Customer Obsession, High Standards

---

## ✅ Forecasting Platform – Quota Planning (MyGoals)

**Situation:**  
Sales managers and reps across the U.S. were using outdated Excel files for monthly quota planning, leading to confusion, versioning issues, and delays.

**Task:**  
Design an automated forecasting and quota planning platform using Jedox to streamline workflows.

**Action:**  
- Built role-based planning logic with auto-approvals and audit trails.
- Ran lunch-and-learn sessions, office hours, and feedback loops to drive adoption.
- Worked closely with business to build features in quick sprints based on feedback.

**Result:**  
- Reduced planning cycle from **20 days → 3 days**.  
- Migrated **13 of 15 regions (87%)** within 7 months.  
- Increased adoption rate by **5x** after redesign and feedback incorporation.  
- Improved quota visibility and reduced escalations by **70%**.

**Leadership Principles:** Think Big, Customer Obsession, Invent & Simplify, Deliver Results, Earn Trust

---

## ✅ Learning Impact – Tech Adoption & Documentation

**Situation:**  
The legacy customer integration system was undocumented and high-risk. I had to modernize it while understanding its full logic.

**Task:**  
Migrate flows to modern architecture while reducing onboarding effort and increasing system transparency.

**Action:**  
- Reverse-engineered undocumented flows and created modular documentation.
- Migrated flows strategically — real-time to Spring Boot, others to Talend.
- Shared documentation practices org-wide.

**Result:**  
- Reduced average onboarding time from **3 weeks → 4 days**.  
- Cut support escalations by **60%** in 2 quarters.  
- System resilience improved with automated retries, monitoring, and SOPs.

**Leadership Principles:** Dive Deep, Learn & Be Curious, Ownership, High Standards

---

## ✅ Prevented Production Outage – Bill 64 NFT Concern

**Situation:**  
Bill 64 purge pipeline passed UAT, but I noticed all tests used tiny datasets. Production would process millions of records, and performance risk was unvalidated.

**Task:**  
Raise performance concerns and avoid downstream disruption to other pipelines.

**Action:**  
- Flagged concern to project lead, proposed NFT with real volumes.
- NFT revealed **JVM heap memory** and pipeline queuing issues.
- Suggested phased purge design instead of bulk run.

**Result:**  
- Avoided system overload, saved [X] hours of downstream delay.  
- Purge completed within SLA with **0 performance incidents**.  
- Architecture was reused for 3 other regulatory purge initiatives.

**Leadership Principles:** Backbone, Bias for Action, Ownership, Dive Deep, Deliver Results

---

## ✅ Failure Story – Timezone Misconfiguration

**Situation:**  
Early in my career, I managed a critical Linux-based pipeline responsible for daily file generation consumed by customer-facing dashboards.

**Task:**  
Ensure file delivery on time to meet daily dashboard refresh.

**Action:**  
- Scheduled job assuming EST, but server was in PST.
- Caused stale/missing data in dashboards, customer insights impacted.
- I discovered the issue proactively (working offshore), alerted leadership, and implemented timezone-aware cron logic.

**Result:**  
- Issue resolved before onshore teams began their day.  
- Implemented a **timezone-agnostic scheduling wrapper** for all jobs.  
- Prevented recurrence across 20+ scheduled jobs.  
- Learned importance of infra awareness and proactive communication.

**Leadership Principles:** Ownership, Dive Deep, Earn Trust, Learn & Be Curious

---

## ✅ LMS for Sales Reps – Enablement Hub Success

**Situation:**  
Comcast hired me to build a POC LMS for sales reps to get regional deals, bundles, and enablement resources.

**Task:**  
Design a personalized, role-based LMS with region-level separation, real-time updates, and high usability.

**Action:**  
- Used IICS to fetch Workday data, integrated with Azure Blob + AD via AzCopy.
- Defined **30+ roles** across **16 regions** and **10 business streams**.
- Enabled personalization with Microsoft Graph API.
- Scaled it to include timesheets, payroll, KPIs, suggestion box, and search.
- After success, led scaling to Comcast Business, expanded team from 1 to 6.

**Result:**  
- Adopted as **default homepage for 16 regional sales teams**.  
- Improved rep onboarding time by **30%**.  
- Collected **100+ suggestions** via feedback module.  
- Became **top enablement story of FY2018** and scaled to Comcast Business.

**Leadership Principles:** Customer Obsession, Think Big, Invent & Simplify, Ownership, Earn Trust, Hire & Develop the Best, Success & Scale Broad Responsibility

# 🧩 Amazon Leadership Principles Matrix – Abinaya's STAR Stories

| STAR Story                          | CO | OW | IS | IR | LC | HD | HS | TB | B4 | FR | ET | DD | HB | DR | EE | SS |
|------------------------------------|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| Bill 64 Purge Pipeline             | ✅ | ✅ |    |    |    |    |    |    |    |    | ✅ | ✅ |    | ✅ | ✅ |    |
| ETL Modernization                  | ✅ | ✅ | ✅ | ✅ | ✅ |    | ✅ | ✅ |    |    | ✅ | ✅ |    | ✅ | ✅ |    |
| Incentive Compensation             | ✅ | ✅ | ✅ | ✅ |    | ✅ | ✅ |    |    |    | ✅ | ✅ |    | ✅ | ✅ |    |
| Forecasting Analytics (MyGoals)    | ✅ | ✅ | ✅ |    |    | ✅ | ✅ | ✅ |    | ✅ | ✅ |    |    | ✅ | ✅ |    |
| Learning Impact (Modernization)    |    | ✅ | ✅ |    | ✅ |    | ✅ |    |    |    | ✅ | ✅ |    | ✅ | ✅ |    |
| Bill 64 – NFT Performance Save     | ✅ | ✅ |    |    |    |    |    |    | ✅ |    | ✅ | ✅ | ✅ | ✅ | ✅ |    |
| Failure – Timezone Misconfig       | ✅ | ✅ |    |    |    |    |    |    |    |    | ✅ | ✅ |    |    | ✅ |    |
| LMS – Sales Rep Enablement Hub     | ✅ | ✅ | ✅ |    |    | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |    | ✅ | ✅ | ✅ |

**Legend:**
CO = Customer Obsession  
OW = Ownership  
IS = Invent and Simplify  
IR = Are Right, A Lot  
LC = Learn and Be Curious  
HD = Hire and Develop the Best  
HS = Insist on the Highest Standards  
TB = Think Big  
B4 = Bias for Action  
FR = Frugality  
ET = Earn Trust  
DD = Dive Deep  
HB = Have Backbone; Disagree and Commit  
DR = Deliver Results  
EE = Strive to be Earth’s Best Employer  
SS = Success and Scale Bring Broad Responsibility
