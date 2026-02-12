# Zendesk Workforce Management Analytics Dashboard (Google Sheets)
Google Sheets project with Coefficient API integration, Pivot-based analysis, and Dashboard with Zendesk data

## Overview
This project showcases an end-to-end workforce management analytics workflow using Zendesk Support ticket data integrated with Google Sheets. The workbook includes automated data retrieval via Coefficient, pivot-table analysis, and an interactive dashboard following Zendesk's visual design system.

## Dashboard Link
[Zendesk Workforce Management](https://docs.google.com/spreadsheets/d/1CSOUjWRBKLgGxfPsBrbxhauatoRHm0XgV_4kZ93iFJ4/edit?gid=788165603#gid=788165603)

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

## What’s Inside the Workbook
The Google Sheets file is organized as a complete WFM analysis pipeline:

- Zendesk Import sheet: Raw ticket data automatically synced via Coefficient
- Pivot Tables sheets: Multiple pivot tables analyzing status, agents, priority, and workload distribution
- Dashboard sheet: Interactive visualizations with KPI cards and charts using Zendesk color palette

## Data Integration Highlights
Key setup and configuration steps:
- Connected Zendesk Support to Google Sheets using Coefficient add-on (no-code API integration)
- Automated real-time ticket data synchronization eliminating manual CSV exports
- Created 50 synthetic tickets across 5 support agents with realistic WFM attributes
- Structured data with key dimensions: Status, Priority, Agent, Requester, Timestamps, Department
- Configured auto-refresh to ensure dashboard reflects current ticket state

## How to Interact
1. Open the Google Sheets workbook
2. Go to the Dashboard sheet
3. Review KPI metrics at the top
4. Explore pivot charts showing workload distribution and ticket trends
5. Navigate to individual Pivot Tables sheets for detailed breakdowns
6. Data refreshes automatically via Coefficient integration

## Tools Used
- Zendesk Support (ticket management system, free trial)
- Coefficient (Google Sheets add-on for API integration)
- Google Sheets (pivot tables, formulas, dashboard design)
- Charts & conditional formatting (dashboard visualization with Zendesk color palette)

## Notes for Reviewers
This project is designed to demonstrate:
- Integration skills: No-code API connection between enterprise SaaS tools
- WFM analytics: Understanding of support operations metrics and KPIs
- Data transformation: Converting raw ticket data into actionable insights
- Dashboard design: Creating executive-ready visualizations with professional branding
- Practical application: Simulating real-world workforce management reporting needs
