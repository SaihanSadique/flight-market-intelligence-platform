# flight-market-intelligence-platform
Production-style airline analytics platform simulating a real-world aviation intelligence system using real world data.

## Architecture Overview

<img width="1536" height="960" alt="architecture" src="https://github.com/user-attachments/assets/a3140ab6-8f2a-477d-bdf1-47ce5e3b8f1e" />

# Data Sourcing
 - Extracted interstate and intrastate flight market data from the U.S. DOT Bureau of Transportation Statistics (TranStats) of ~ 10 GB Data
 - Simulated enterprise data sources by distributing datasets across:
   * Cloudflare R2
   * Amazon S3
   * Azure Blob Storage
   * MongoDB
   * Azure blob
 - Stored datasets in compressed (GZIP) format to optimize storage footprint

# Ingestion & Landing (Bronze Layer)

- Built Azure Data Factory pipelines to ingest data from multiple cloud sources
- Landed raw datasets into a structured Bronze layer
- Preserved source schema and added ingestion metadata
- Designed the landing layer to simulate a production staging environment

# Transformation & Enrichment (Silver Layer)

- Used Azure Databricks to implement Medallion Architecture (Bronze → Silver → Gold)
- Standardized and cleansed datasets
- Engineered derived metrics:
  * Total Flights
  * Total Passengers
  * Average Revenue
  * Fare per Mile
- Applied Delta Lake optimizations including partitioning and VACUUM for storage efficiency

# Aggregation & Modeling (Gold Layer)
- Performed route-level and carrier-level aggregations to reduce BI compute overhead
- Designed and built:
   * Fact Route table
   * Fact Carrier table
   * Structured Gold layer as an analytics-ready Lakehouse serving layer
