Project 6 – Marketplace Trust & Safety Analytics
Business Case Project Brief for Students

Project Description
An e-commerce marketplace wants to identify risky sellers, detect suspicious transaction patterns, and create trusted analytical outputs for its trust-and-safety team. Students must design and implement an end-to-end governed data platform that integrates order activity, returns, seller profiles, and complaint data.
Business Context
    • Marketplaces face a persistent challenge: growth in transactions can hide problematic behavior such as refund abuse, counterfeit activity, unusual return rates, or emerging seller fraud patterns.
    • Operational teams usually have fragments of this information in different systems, but without a unified data platform it is difficult to create consistent risk indicators or explain why one seller should be reviewed before another.
    • The project should reflect a realistic trust-and-safety analytics use case where governance is mandatory because customer information and seller-sensitive business data are involved.
Project Objectives
    • Build seller-centric analytics: Students should design datasets that summarize seller behavior, transaction quality, and complaint indicators in a form suitable for risk review.
    • Detect suspicious patterns: The platform should support anomaly-oriented analysis such as unusual return rates, order spikes, complaint concentration, or other suspicious signals.
    • Prioritize investigation: Students should produce outputs that help a trust-and-safety analyst decide which sellers or patterns deserve attention first.
    • Govern customer and seller data responsibly: The analytical design must include controlled access and masking so the platform remains useful without exposing unnecessary personal data.
Data Sources
    • Order events stream: A continuous feed of marketplace transactions, including seller, buyer, order amount, order status, and timestamps.
    • Returns or refund events stream: A stream of return requests, approved refunds, disputes, or reversal events linked to orders or sellers.
    • Seller profile batch data: A batch dataset with seller metadata such as registration date, region, category, verification status, or support tier.
    • Customer complaint batch data: A dataset containing complaint tickets, complaint categories, severity, and timestamps that can be linked to sellers or orders.
Sample Data to Be Ingested
Order event (JSON)
{
  "order_id": "O123",
  "seller_id": "S55",
  "customer_id": "C71",
  "amount": 120.5,
  "timestamp": "2026-01-01T10:00:00",
  "status": "completed",
  "category": "electronics"
}
Return event (JSON)
{
  "return_id": "R901",
  "order_id": "O123",
  "seller_id": "S55",
  "timestamp": "2026-01-08T15:30:00",
  "reason": "damaged_item",
  "status": "approved"
}
Complaint record (JSON)
{
  "complaint_id": "CMP44",
  "seller_id": "S55",
  "timestamp": "2026-01-09T09:10:00",
  "severity": "high",
  "category": "counterfeit_claim"
}
Architecture Requirements
    • Hybrid ingestion design: Students must ingest at least one streaming commerce event source via Kafka and combine it with slower batch reference or complaint data.
    • Layered storage in HDFS: The project must implement raw, refined, and curated layers and should justify how those layers support both traceability and analyst-friendly outputs.
    • Metadata and queryability: Hive Metastore must register the main curated structures so they can be queried and documented consistently.
    • Orchestration and control: Airflow should coordinate ingestion checks, transformations, risk-score dataset generation, quality checks, and publication of governed outputs.
Processing Requirements
    • Normalize transaction and complaint data: Students should standardize timestamps, statuses, seller references, and categories so different source systems can be compared consistently.
    • Create seller behavior aggregates: The project should compute metrics such as order count, refund ratio, complaint density, average ticket size, or other indicators that make seller behavior analytically comparable.
    • Design suspicious-pattern logic: Students may choose how to identify suspicious patterns, but they should explain the business reasoning behind their derived indicators or anomaly heuristics.
    • Produce investigation-oriented curated outputs: The final datasets should support analyst workflows rather than only raw exploration, meaning the outputs should be grouped, scored, or prioritized in a meaningful way.
Governance Requirements
    • Protected customer information: Customer-level identifiers should be masked or restricted in broader analytical outputs so trust analysts can work with the data without unnecessary exposure.
    • Role separation: Students should define at least a distinction between trust-and-safety users and more general business users, and explain which datasets each group can access.
    • Quality and consistency checks: The project should validate duplicate transactions, impossible status sequences, missing seller mappings, and suspicious gaps between event types.
    • Lineage and documentation: Students should document how raw orders, returns, and complaints contribute to the final seller-risk outputs.
Expected Outputs
    • Seller risk dataset: A curated dataset that summarizes seller behavior and highlights indicators useful for investigation.
    • Fraud-pattern or anomaly dataset: A dataset or view that isolates suspicious combinations of events, ratios, or activity spikes.
    • Analytical SQL examples: Students should provide example queries demonstrating how investigators or analysts would use the platform outputs.
Project Plan
    • Define the trust-and-safety use case in business terms and map it to the needed source data and derived indicators.
    • Design the layered storage model and the key curated seller-centric analytics outputs.
    • Implement ingestion, transformations, governance controls, and publication logic orchestrated with Airflow.
    • Demonstrate how the final datasets support investigation, prioritization, and transparent reasoning about suspicious sellers.
Bonus
    • Add a lightweight explainability layer that shows why a seller was flagged.
    • Generate real-time or near-real-time investigation alerts from streaming indicators.
    • Use Iceberg for curated risk tables if students want stronger table management and maintenance patterns.
Student Deliverables

Deliverable

Architecture design
Data model and storage design
Orchestration
Governance evidence
Demonstration


What it should contain
Chosen architecture, major components, data flow, and justification of technical decisions.
Definition of raw, refined, and curated structures, key fields, and partitioning/organization choices.
Airflow workflows that coordinate ingestion, transformation, validation, and publication.
Ownership, access assumptions, quality checks, and documentation of lineage and trust.
Queries, notebook, dashboard, or another clear walkthrough showing how business users would consume the outputs.

