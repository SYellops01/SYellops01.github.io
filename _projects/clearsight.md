---
title: "Finance Self Service"
subtitle: "An end-to-end pipeline exposing live eToro portfolio performance for a user. This solution leverages Docker for API Integration, Airflow for scheduling and dbt to transform data within Snowflake's modern data platform, presenting this in a Streamlit-in-Snowflake application"
slug: etoro-portfolio-project
model_name: "mart_etoro_portfolio"
type: "client"
summary: "Streamlit-in-Snowflake solution leveraging dbt to expose eToro portfolio data."
order: 1
thumbnail: /assets/images/projects/etoro/trading_thumbnail.jpg
stack: ["dbt", "Snowflake", "SQL", "Airflow", "Kafka", "Python"]
demo_url: ""
code_url: "https://github.com/SYellops01/etoro_portfolio_project"
---
<img width="1747" height="799" alt="image" src="https://github.com/user-attachments/assets/7d2ef458-db04-48e3-a0cd-68aa91890724" />

## The Problem

In eToro, it is not currently possible to view exposure across direct positions and those held within 'mirror' portfolios, making it difficult to view true portfolio performance and exposure across industries or sectors. This project addresses this shortcoming, allowing the end-user to view exposure and profit and loss across their whole portfolio, splitting this by sector, industry, individual mirrors or individual instruments.

## The Build

I designed and built a single source of truth for my portfolio in Snowflake, leveraging dbt for transformation and testing, persisting this output in a Streamlit-in-Snowflake app:
<img width="1571" height="733" alt="image" src="https://github.com/user-attachments/assets/301119c6-b1f4-4a6d-9780-401c99c3dec2" />

- **Dockerised infrastructure** to pull from API into minIO storage via Kafka. 
- **Airflow scheduler** to schedule ingestion of data to Snowflake from minIO buckets.
- A **staging layer** containing raw staging data from API calls.
- A **bronze layer** that passes staged data into raw, semi-structured VARIANT column in Snowflake, building flexibility into the ingestion process.
- A **silver layer** that parses data and derives columns into structured data.
- A **gold layer** baking in business logic, normalising data and accounting for edge cases.
- A **marts layer** exposed to the SiS app, fully tested with `dbt test` for uniqueness, referential integrity, and freshness.

## Impact

- Allows for analysis of portfolio performance at the instrument level, including positions held within 'mirrors'.
- Clearly exposes performance and exposure held across industries.
- Aggregates cash positions, including those held in mirrors, spotlighting liquidity.

<img width="1728" height="571" alt="image" src="https://github.com/user-attachments/assets/d5b91f7a-a213-4e0b-b754-8cd96bb4e833" />
<img width="1710" height="521" alt="image" src="https://github.com/user-attachments/assets/3b7cb8ab-b06a-4dcf-920b-ebddc6b9009f" />
