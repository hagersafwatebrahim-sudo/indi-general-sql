# 🇮🇳 India General Elections Result Analysis 2024 - SQL Queries

This repository contains a comprehensive set of SQL queries designed to analyze and extract deep insights from the India General Elections 2024 dataset. The queries range from basic aggregations to advanced analytical calculations using Windows functions, CTEs, and complex Joins.

## 📌 Project Overview
The goal of this project is to perform a detailed data analysis on the election results across different states, constituencies, candidates, and political alliances (NDA, I.N.D.I.A, and Others). It provides insights into seat distribution, vote margins, voting methods (EVM vs. Postal), and performance breakdown by state.

## 🗂️ Database Schema Insight
The analysis is performed across the following interconnected tables:
- constituencywise_results: Stores final statistics and winning candidate information for each constituency.
- constituencywise_details: Contains detailed vote counts (EVM & Postal) for every candidate in each constituency.
- partywise_results: Holds data on seats won by individual parties.
- statewise_results: Maps constituencies to their respective states.
- states: Reference table for state IDs and names.

---

## 🚀 Key Insights & SQL Capabilities Covered

### 1. General & High-Level Aggregations
- Total Seats: Computing the total number of parliamentary constituencies available for the election.
- Seats per State: Breaking down the availability of election seats across each unique state.

### 2. Alliance Performance Analysis (NDA vs. I.N.D.I.A vs. Others)
- Dynamic categorizations and computations of total seats won by the major coalitions (NDA and I.N.D.I.A) using custom conditional logic (CASE WHEN).
- Grouped insights to identify which political alliance dominated the 2024 elections globally and state-by-state.

### 3. Deep-Dive Candidate & Constituency Analysis
- Winning Metrics: Extracting the winning candidate's name, party affiliation, alliance, total votes, and margin of victory for specific target constituencies (e.g., Amethi).
- Vote Distribution: Analyzing the ratio and distribution of EVM (Electronic Voting Machine) votes versus Postal votes.
- Top Performers: Querying the Top 10 candidates who received the absolute highest number of EVM votes across the country.

### 4. Advanced Analytical Queries
- Winner & Runner-up Identification: Utilizing Common Table Expressions (CTEs) and advanced Window functions (ROW_NUMBER() OVER (PARTITION BY ... ORDER BY ...)) to cleanly isolate the 1st and 2nd place candidates for every constituency within a state.
- Comprehensive State Metrics: Detailed metrics for specific states (e.g., Maharashtra) showing Total Seats, Total Candidates, Total Parties involved, and complete breakdown of vote types.

---

## 💻 Sample Queries Included

### Database Optimization: Adding Alliance Column
`sql
ALTER TABLE partywise_results ADD party_alliance VARCHAR(50);

-- Example Update for I.N.D.I.A Alliance
UPDATE partywise_results 
SET party_alliance = 'I.N.D.I.A' 
WHERE party IN ('Indian National Congress - INC', 'Samajwadi Party - SP', 'Aam Aadmi Party - AAAP', ...);
