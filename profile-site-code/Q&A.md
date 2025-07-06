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

## 🎯 Final Tips

- If you don’t know—say: “I haven’t used that yet, but I know it’s used for...”
- Practice aloud with a timer (30–45 seconds/answer).
- Use this sheet daily for recall; convert it into flashcards if you want spaced repetition.
