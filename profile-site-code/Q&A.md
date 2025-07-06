# 🚀 AWS ProServe Rapid-Fire Interview Prep (Q&A)

---

## 🔶 AWS Services & Architecture

### Q: What’s the difference between Glue and EMR?
A: Glue is serverless and used for ETL jobs with minimal infrastructure management. EMR is more customizable, used for large-scale distributed processing like Spark/Hadoop clusters.

---

### Q: When would you choose Athena over Redshift?
A: Athena is best for ad-hoc queries on data stored in S3; it's serverless and pay-per-query. Redshift is optimized for structured data warehousing with faster performance for complex analytics.

---

### Q: How do you secure data in S3?
A: Use S3 bucket policies + IAM, enable default encryption (SSE-KMS), restrict public access, and optionally enable Object Lock and logging with CloudTrail.

---

### Q: What is Lake Formation used for?
A: It's used to define fine-grained access control over data in S3 (column, row-level), manage data lake permissions, and centralize governance across AWS analytics services.

---

### Q: What’s the difference between an IAM role and IAM policy?
A: An IAM policy defines permissions; a role is an identity with a set of policies. Roles are assumed by entities (users, services) to access AWS resources.

---

### Q: What’s CloudFormation vs Terraform?
A: Both are IaC tools. CloudFormation is AWS-native, tightly integrated. Terraform is third-party (HashiCorp), multi-cloud, and has a broader module registry.

---

## 🟧 Data Engineering & ETL

### Q: What’s the difference between ETL and ELT?
A: ETL extracts and transforms data before loading into the target; ELT loads raw data first, then transforms it within the target (common in modern data lakes/warehouses).

---

### Q: How do you optimize a slow Spark job?
A: Repartition data, avoid wide shuffles, broadcast small tables, cache intermediate results, enable adaptive query execution, and monitor stage/task time in Spark UI.

---

### Q: What is data skew and how do you handle it?
A: Uneven distribution of keys causes one partition to process more data. Fix it with salting, bucketing, custom partitioning, or broadcast joins.

---

### Q: What are Glue Crawlers?
A: They automatically scan data in S3 and populate the Glue Data Catalog with schema metadata for querying with Athena or Redshift Spectrum.

---

### Q: What is schema evolution and how do you handle it in Glue?
A: Schema evolution refers to changes in structure (new columns, types). Glue supports evolving schemas via Data Catalog updates and dynamic frames.

---

## 🟨 SQL & Python

### Q: Write a SQL to find top 3 products per region.
A:
```sql
WITH ranked AS (
SELECT region, product_id, SUM(sales) AS total_sales,
RANK() OVER (PARTITION BY region ORDER BY SUM(sales) DESC) AS rnk
FROM sales_data
GROUP BY region, product_id
)
SELECT * FROM ranked WHERE rnk <= 3;
```

---

### Q: What’s the difference between RANK() and ROW_NUMBER()?
A: RANK() gives the same rank to ties and skips numbers (1, 2, 2, 4), while ROW_NUMBER() assigns unique row numbers regardless of tie.

---

### Q: What’s the difference between Python list and tuple?
A: Lists are mutable and use more memory; tuples are immutable and generally faster for read-only data.

---

### Q: Difference between `map()` and `apply()` in Pandas?
A: `map()` works on Series and is element-wise; `apply()` works on Series or DataFrames and allows row/column-wise operations.

---

## 🟦 Security & Compliance

### Q: How do you enforce encryption at rest in S3?
A: Enable SSE-KMS or SSE-S3. Enforce via bucket policy that denies uploads without encryption headers.

---

### Q: What is AWS Macie?
A: A security service that uses ML to detect sensitive data (PII, credentials) in S3 and alerts for compliance breaches.

---

### Q: How do you implement row-level security in Athena or Redshift?
A: Use Lake Formation for Athena, and role-based views or RLS policies in Redshift with session_user or sys_context-like logic.

---

### Q: How would you ensure GDPR compliance in your data pipeline?
A: Use data tagging, anonymization, row-level access control, audit trails (CloudTrail), and design delete requests for "Right to be Forgotten."

---

## 🟩 GenAI / ML (Optional Based on Resume)

### Q: What is a vector database?
A: A database that stores high-dimensional vectors (embeddings) for similarity search—used in GenAI (e.g., Pinecone, Faiss, Weaviate).

---

### Q: How would you use LangChain in a data application?
A: Use LangChain to orchestrate LLM prompts and tools—e.g., dynamic SQL generation, summarization of BI insights, chatbot over structured data.

---

### Q: What’s the difference between Bedrock and SageMaker?
A: Bedrock provides API access to foundation models (e.g., Titan, Anthropic, Cohere) with no infrastructure. SageMaker is used for full ML lifecycle including custom training and hosting.

---

### Q: How do you prevent hallucination in LLMs?
A: Use retrieval-augmented generation (RAG), grounding with factual sources, prompt constraints, and model fine-tuning for specific domain language.

---

## 🟫 DevOps / Infra

### Q: How do you manage secrets in Terraform?
A: Use environment variables, secret managers (AWS Secrets Manager or SSM), and avoid hardcoding in `.tf` files. Encrypt backend states.

---

### Q: How do you monitor Glue jobs?
A: CloudWatch logs + metrics, Glue job bookmarks, failure notifications via SNS. You can also use AWS EventBridge to trigger alerts on failure.

---

### Q: What’s the difference between CloudTrail and CloudWatch?
A: CloudTrail tracks API calls across AWS (who did what). CloudWatch monitors performance (metrics, logs, alarms).

---

### Q: What is the use of Step Functions?
A: To orchestrate multiple AWS services into serverless workflows (e.g., invoke Lambda, run Glue, wait on S3, handle retries, parallel steps).

---
## ☁️ Cloud Basics – Rapid-Fire Q&A

---

### Q: What is cloud computing?
A: Cloud computing is the on-demand delivery of compute, storage, databases, and other IT resources over the internet with pay-as-you-go pricing, eliminating the need for owning physical infrastructure.

---

### Q: What are the benefits of cloud computing?
A: Cost-effective, scalable, highly available, elastic, faster time to market, managed services, and pay-as-you-go billing.

---

### Q: What are the 3 main cloud service models?
A:
- **IaaS (Infrastructure as a Service)**: raw compute, storage, networking (e.g., EC2, EBS)
- **PaaS (Platform as a Service)**: abstracted platforms to build/run apps (e.g., Lambda, Glue)
- **SaaS (Software as a Service)**: fully managed apps (e.g., QuickSight, Salesforce)

---

### Q: What are the 3 cloud deployment models?
A:
- **Public Cloud**: Shared infrastructure (e.g., AWS)
- **Private Cloud**: Dedicated cloud in a company’s data center
- **Hybrid Cloud**: Combination of both, often for data residency or legacy apps

---

### Q: What is elasticity vs scalability?
A:
- **Scalability**: The system’s ability to grow (or shrink) in capacity to handle increasing load.
- **Elasticity**: The ability to automatically scale up/down based on demand (real-time resource adjustment).

---

### Q: What is high availability?
A: Designing systems to be operational and accessible with minimal downtime, often using multi-AZ, auto-scaling, failover strategies.

---

### Q: What’s the shared responsibility model in AWS?
A:
- **AWS** is responsible for security **of** the cloud (hardware, networking, facilities)
- **Customers** are responsible for security **in** the cloud (data, OS config, IAM, encryption)

---

### Q: What is the AWS Well-Architected Framework?
A: A set of best practices across 6 pillars: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, and Sustainability.

---

### Q: Difference between Availability Zone and Region?
A:
- **Region**: A geographic area (e.g., us-east-1).
- **AZ**: One or more data centers in a region, isolated but connected with low latency.

---

### Q: What is an Edge Location?
A: AWS site used by CloudFront to cache content closer to users, improving latency.

---

### Q: What is serverless computing?
A: Running code or workloads without managing servers. AWS handles provisioning, scaling, and maintenance (e.g., Lambda, DynamoDB, Step Functions).

---

### Q: What is a VPC?
A: A logically isolated virtual network where you launch AWS resources. You control IP range, subnets, route tables, gateways, etc.

---

### Q: Difference between Security Group and NACL?
A:
- **Security Group**: Stateful, instance-level, allows inbound and outbound rules.
- **NACL**: Stateless, subnet-level, allows and denies traffic rules for inbound and outbound.

---

### Q: What is Auto Scaling?
A: Automatically adjusts the number of EC2 instances in a group based on load or schedule, to maintain performance and minimize cost.

---

### Q: What is a Load Balancer?
A: Distributes traffic across multiple targets (EC2s, containers, IPs) to improve availability and performance. Types: ALB, NLB, CLB.

---

### Q: What is CloudTrail?
A: A service that logs API calls across AWS services for auditing and compliance.

---

### Q: What is CloudWatch?
A: A monitoring service for AWS resources and applications—includes metrics, logs, dashboards, and alarms.

---

### Q: What is an S3 bucket policy?
A: A resource-based JSON policy that defines access permissions directly on the S3 bucket.

---

### Q: What is IAM?
A: Identity and Access Management: used to securely control access to AWS services and resources.

---

### Q: What is the purpose of an Availability Zone (AZ)?
A: AZs provide isolation for fault tolerance. Deploying across AZs ensures high availability during failures like power or hardware issues in one AZ.

## 🧑‍💼 Customer Scenario-Based Q&A

---

### Q: A non-technical client asks: “Why should we move to AWS instead of staying on-prem?”  
A: I’d explain that AWS offers flexibility, pay-as-you-go pricing, access to cutting-edge services like AI/ML, and improved resilience through high availability. Unlike on-prem, you don’t need to invest heavily upfront or worry about hardware lifecycle.

---

### Q: A customer says: “I already have data pipelines on-prem. How would migration to AWS look?”  
A: First, we assess existing pipelines (sources, transformations, schedules). Then we identify AWS services to replicate or modernize that setup—like using Glue for ETL, S3 as the data lake, and Redshift or Athena for querying. We prioritize quick wins (lift-and-shift) and gradually evolve toward cloud-native solutions.

---

### Q: A stakeholder says: “We’re concerned about data security in the cloud.”  
A: I’d walk them through the shared responsibility model. AWS handles physical security, networking, and availability. We control IAM, encryption, and audit controls. Services like S3, KMS, Macie, and GuardDuty provide strong encryption, threat detection, and access controls. Often, cloud security surpasses on-prem standards.

---

### Q: A client asks: “How do I know my analytics workloads will perform better in AWS?”  
A: AWS provides managed analytics tools like Redshift, Athena, and EMR that are optimized for scale and cost. We can auto-scale, cache, and tune resources dynamically. With monitoring tools like CloudWatch and auto-scaling options, you get predictable and improved performance with fewer bottlenecks.

---

### Q: “How do I avoid vendor lock-in if we adopt AWS?”  
A: AWS supports open standards like SQL, Spark, and Kubernetes. Services like Redshift Spectrum or Glue can integrate with external sources. We also use IaC tools like Terraform that are portable. Designing for modularity and abstraction ensures flexibility if you need multi-cloud or future migration.

---

### Q: “We don’t have a data team. How much will AWS services increase our workload?”  
A: AWS offers many serverless and managed options like Glue, Athena, and QuickSight, so there’s little to no infrastructure to manage. With automation and managed services, your team can focus on business insights, not operations. Plus, AWS partners (like ProServe) can accelerate setup and handover.

---

### Q: “We’re in healthcare/finance—can AWS meet our compliance needs?”  
A: Absolutely. AWS complies with HIPAA, GDPR, SOC2, PCI, and more. We can enforce encryption, access controls, and audit trails. Services like Macie and Config help detect sensitive data and ensure continuous compliance. We can also help implement necessary governance guardrails.

---

### Q: “What if our data volume grows 10x in 2 years?”  
A: That’s where AWS shines. Services like S3, Redshift, and EMR scale seamlessly with growing data. We design solutions with scalability in mind—from auto-scaling compute to partitioning strategies in data lakes. You won’t have to re-architect every time your usage spikes.

---

### Q: “How would you explain the difference between S3 and EBS to a business user?”  
A: S3 is like a virtual file cabinet—great for storing lots of files, documents, and backups—accessible anytime over the internet. EBS is more like a computer hard drive—you attach it to a server (EC2) and use it while the server runs. S3 is for long-term storage; EBS is for active processing.

---

### Q: “Why would I use Glue when I already have SQL-based ETL tools?”  
A: Glue is serverless, cost-efficient, and integrated with AWS-native services. It supports Python (PySpark) and dynamic frames, is easier to scale, and removes infrastructure overhead. It’s ideal for data lakes, real-time transformations, and governance via the Glue Catalog and Lake Formation.


## 🎯 Final Tips

- If you don’t know—say: “I haven’t used that yet, but I know it’s used for...”
- Practice aloud with a timer (30–45 seconds/answer).
- Use this sheet daily for recall; convert it into flashcards if you want spaced repetition.
