# Zendesk Workforce Management Analytics Dashboard (BigQuery + Power BI)
Cloud-based analytics project with BigQuery SQL analysis and Power BI interactive dashboards

## Overview
This project demonstrates an end-to-end cloud analytics workflow for workforce management using Google BigQuery for data warehousing and SQL analysis, integrated with Power BI for interactive visualization. The project analyzes 1,000 synthetic support tickets across 20 agents over a 2-week period, providing actionable insights into team performance, workload distribution, and operational efficiency.

## Power BI Dashboard Preview
The working dataset could be found here
['Zendesk WFM Raw data'](./data/zendesk_wfm_raw_data.csv)

![Workload Distribution by Agent](power_bi/Workload%20Distribution%20by%20Agent.png)

## Business Questions / Problem Statements
The following questions were defined to guide the analysis and dashboard design:

1. What is the overall ticket volume and distribution across different statuses (Open, Pending, Solved)?
2. How is the workload distributed across support agents, and are there significant imbalances?
3. What is the breakdown of tickets by priority level (High, Normal, Low)?
4. Which agents handle the most high-priority tickets, and how does this compare to their overall workload?
5. How do ticket creation patterns vary across different time periods (by day, by hour)?
6. What is the average ticket resolution rate per agent?
7. Which departments or ticket types receive the highest volume?
8. What is the distribution of tickets by status within each agent's workload?

## BigQuery SQL Analysis
All business questions were answered using SQL queries in Google BigQuery. The ['sql_queries/'](./sql_queries) folder contains 8 production-ready queries corresponding to each business question. Full query and partial results are shown.

## What’s Inside
### 1. BigQuery Data Warehouse

Dataset: zendesk_support
Table: zendesk_wfm_raw_data
Records: 1,000 support tickets
Dimensions: Agent, Status, Priority, Department, Ticket Type, Timestamps
Metrics: Resolution time, First response time, Ticket counts

### 2. SQL Analysis (BigQuery)

8 production-ready SQL queries analyzing different aspects of WFM operations
Window functions for rankings and time-series analysis
Aggregations with conditional logic for KPI calculations
Date/time parsing for temporal pattern analysis

### 3. Power BI Dashboard

Page 1: Executive Overview
Page 2: Workload Distribution by Agent
Page 3: Time Based Ticket Distribution
Page 4: Multi Dimensional Analysis

## Data Model & Schema
### Key Fields:

- ticket_id: Unique identifier (500001-501000)
- status: open | pending | solved
- priority: high | normal | low
- agent_name: Assigned support agent (20 unique agents)
- department: Technical Support | Billing | Customer Success | Product | Sales
- created_at: Ticket creation timestamp
- closed_at: Resolution timestamp (null for open/pending)
- resolution_time_hours: Time to resolution (calculated)
- first_response_time_hours: Time to first agent response

### Distribution Highlights:

- Status: 59% Solved, 25% Pending, 16% Open
- Priority: 48% Normal, 41% High, 11% Low
- Departments: 41% Technical Support, 25% Billing, 20% Customer Success
- Date Range: April 1-14, 2024 (2 weeks, business hours emphasis)

## How to Interact
### Accessing BigQuery Queries

1. Navigate to the sql_queries/ folder in this repository
2. Open any .sql file to view the query
3. To run in BigQuery:

- Go to Google Cloud BigQuery Console
- Copy the SQL query
- *Important*: The queries reference the BigQuery table path:

`zendesk-wfm-analytics.zendesk_support.zendesk_wfm_raw_data`
 Where:
 - `zendesk-wfm-analytics` = GCP Project ID
 - `zendesk_support` = BigQuery Dataset name
 - `zendesk_wfm_raw_data` = Table name (matches the CSV filename)

- Click "Run" to execute
- Results appear below the query editor

Note on Naming: The CSV file is named zendesk_wfm_raw_data.csv, and when uploaded to BigQuery, it becomes a table with the same name (zendesk_wfm_raw_data) within the zendesk_support dataset. The full table path includes the project ID, which is why queries reference the complete path shown above.

## Tools & Technologies Used
- Google Cloud Platform (GCP): Cloud infrastructure
- BigQuery: Data warehousing and SQL analysis
- SQL: Data querying and aggregation (window functions, CTEs, date functions)
- Power BI Desktop: Interactive dashboard development
- Python: Synthetic data generation (pandas, numpy)
- Git/GitHub: Version control and documentation

## Technical Highlights
### BigQuery SQL Techniques

- Window Functions: RANK(), ROW_NUMBER() for agent rankings
- Date/Time Functions: EXTRACT(), DATE(), WEEKNUM() for temporal analysis
- Conditional Aggregations: COUNTIF(), CASE WHEN for metric calculations
- Common Table Expressions (CTEs): Complex multi-step queries
- Array Functions: ARRAY_AGG() for nested aggregations

### Power BI Features

- DAX Measures: Custom KPI calculations (Resolution Rate, Avg Resolution Time)
- Calculated Columns: Time dimensions (Hour of Day, Day of Week)
- Relationships: Connected date tables for time intelligence
- Conditional Formatting: Color-coded performance indicators
- Interactive Filters: Cross-visual filtering and drill-down

## Key Insights from Analysis

1. Workload Imbalance: Top 5 agents handle 35% of all tickets (70-76 tickets each), while bottom 5 handle only 15% (30-35 tickets each)
2. Resolution Performance: Average resolution time is 21 hours, with high-priority tickets resolved 40% faster
3. Peak Hours: 60% of tickets arrive between 9 AM - 2 PM, with peaks at 10 AM and 2 PM
4. Department Focus: Technical Support receives 41% of all tickets, significantly more than other departments
5. Status Health: 59% of tickets are resolved, 25% pending, 16% still open

## Notes for Reviewers
This project demonstrates:

- Cloud platform proficiency: Setting up and managing GCP BigQuery infrastructure
- SQL expertise: Writing production-grade analytical queries with advanced functions
- BI tool mastery: Creating executive-ready dashboards in Power BI
- Data storytelling: Translating business questions into actionable insights
- End-to-end analytics: Complete workflow from data ingestion to visualization
- Documentation: Clear technical documentation and knowledge transfer

## Future Enhancements

- Scheduled BigQuery queries for automated reporting
- Additional dashboards for SLA tracking and customer satisfaction
- Integration with real Zendesk API for live data
- Predictive analytics for workload forecasting
- Agent performance scoring model
