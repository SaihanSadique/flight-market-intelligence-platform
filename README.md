# flight-market-intelligence-platform
Production-style airline analytics platform simulating a real-world aviation intelligence system using real world data.

## Architecture Overview

<img width="1536" height="960" alt="architecture" src="https://github.com/user-attachments/assets/a3140ab6-8f2a-477d-bdf1-47ce5e3b8f1e" />

# Data Sourcing
 - Extracted interstate and intrastate flight market data from the U.S. DOT Bureau of Transportation Statistics (TranStats) of ~ 10 GB Data
 - Simulated enterprise data sources by distributing datasets across:

Cloudflare R2

Amazon S3

Azure Blob Storage

MongoDB

Stored datasets in compressed (GZIP) format to optimize storage footprint
