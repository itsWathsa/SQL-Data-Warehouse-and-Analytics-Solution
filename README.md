# Esports Analytics Data Warehouse & Business Intelligence Solution

The Esports Analytics Data Warehouse is a SQL Server–based Business Intelligence solution developed to support analytical reporting and performance evaluation in the esports domain. The project demonstrates how operational esports data can be integrated, transformed, and loaded into a dimensional data warehouse to enable OLAP analysis, reporting, and business intelligence applications.

The solution combines SQL Server databases, SSIS ETL processes, SSAS multidimensional cubes, Power BI dashboards, and Excel-based OLAP analysis to provide a complete end-to-end BI implementation.

## Project Overview

The project models a complete data warehousing and business intelligence architecture for esports performance analytics.

Operational and external data sources are integrated through ETL processes and loaded into a dimensional warehouse optimized for analytical workloads.

The solution includes:

* Source databases and CSV-based data sources
* Staging area for data integration and transformation
* Dimensional data warehouse using a star schema
* SSIS ETL packages for data loading and processing
* Slowly Changing Dimension (SCD Type 2) implementation
* Accumulating Fact Table implementation
* SSAS Multidimensional Cube
* Excel OLAP analysis
* Power BI dashboards and reports

The warehouse stores over **1,000,000 player performance records** covering a two-year period from **January 2023 to December 2024**.

---

## Key Features

* Designed and implemented a dimensional data warehouse using a Star Schema architecture
* Integrated multiple source types including SQL Server databases and CSV files
* Developed a staging layer for data cleansing and transformation
* Built ETL workflows using SQL Server Integration Services (SSIS)
* Implemented Slowly Changing Dimension Type 2 (SCD Type 2) for historical player-team tracking
* Implemented an Accumulating Fact Table pattern for transaction completion analysis
* Developed an SSAS Multidimensional Cube for OLAP operations
* Demonstrated Roll-Up, Drill-Down, Slice, Dice, and Pivot operations
* Created interactive Power BI reports and dashboards
* Developed Excel-based OLAP reports for multidimensional analysis

---

## Data Sources

The solution integrates data from multiple source systems representing different data formats.

### SQL Server Operational Database

The operational esports database contains:

* Players
* Teams
* PlayerContracts
* MatchResults
* MatchPerformance

### Kaggle Dataset

The original esports analytics dataset includes player and match performance statistics such as:

* Kills
* Assists
* Deaths
* Accuracy Percentage
* Performance Score
* Win Probability
* Match Outcome
* MVP Awards

### Tournament Reference Data

Additional tournament data is integrated through CSV files containing:

* Tournament Names
* Regions
* Game Titles
* Prize Pools
* Start Dates
* End Dates

---

## Data Warehouse Design

The warehouse follows a dimensional modeling approach using a Star Schema.

### Fact Table

#### Fact_PlayerPerformance

Stores detailed player performance metrics at the grain of:

**One Player per Match**

Measures include:

* Kills
* Assists
* Deaths
* Accuracy Percentage
* Reaction Time
* Fatigue Index
* Performance Score
* Win Probability
* MVP Award
* KD Ratio
* Transaction Processing Time

### Dimension Tables

#### Dim_Player

Player master data with historical team tracking using SCD Type 2.

#### Dim_Date

Date dimension supporting hierarchical analysis from Day to Year.

#### Dim_Tournament

Tournament information including region, game title, and prize pool.

#### Dim_Map

Game map information enriched with map type and map size attributes.

#### Dim_MatchType

Tournament stage information from Qualifier through Final.

---

## ETL Development

The ETL layer was developed using SQL Server Integration Services (SSIS).

### Load_Staging

Extracts data from source systems and loads raw records into staging tables.

### Load_Dimensions

Loads dimension tables and implements Slowly Changing Dimension Type 2 processing for player history tracking.

### Load_Fact

Populates the Fact_PlayerPerformance table and resolves all surrogate keys through dimension lookups.

### Update_AccmFact

Updates transaction completion timestamps and supports the accumulating fact table design pattern.

---

## Slowly Changing Dimension (SCD Type 2)

The project implements SCD Type 2 within the Player dimension to preserve historical team membership information.

When a player changes teams:

* Existing records are expired
* A new dimension record is created
* Historical analysis remains accurate
* Team movement can be analyzed over time

---

## Accumulating Fact Table

An accumulating fact table pattern was implemented to track transaction lifecycle events.

Additional fields include:

* Transaction Create Time
* Transaction Complete Time
* Processing Time in Hours

This design enables performance monitoring and process completion analysis.

---

## SSAS Cube

The project includes a SQL Server Analysis Services (SSAS) Multidimensional Cube built on top of the data warehouse.

### Cube Features

* Five Dimensions
* Eleven Measures
* Calendar Hierarchy
* Tournament Stage Hierarchy
* Aggregated Performance Metrics
* Fast OLAP Query Performance

### OLAP Operations Demonstrated

* Roll-Up
* Drill-Down
* Slice
* Dice
* Pivot

---

## Power BI Reports

Interactive Power BI dashboards were developed for business analysis and reporting.

### Report Features

#### Matrix Analysis

Player performance breakdown across time periods and match types.

#### Cascading Slicers

Dynamic filtering by region and tournament.

#### Hierarchical Drill-Down

Analysis from year level down to month level.

#### Drill-Through Reports

Detailed player-level performance investigation.

---

## Technologies Used

* Microsoft SQL Server
* T-SQL
* SQL Server Management Studio (SSMS)
* SQL Server Integration Services (SSIS)
* SQL Server Analysis Services (SSAS)
* Visual Studio / SQL Server Data Tools (SSDT)
* Power BI
* Microsoft Excel
* Dimensional Modeling
* Star Schema Design
* OLAP Analysis

---

## Business Value

The solution provides a centralized analytical platform for esports performance management by enabling:

* Player performance analysis
* Tournament performance evaluation
* Regional comparison analysis
* Match outcome tracking
* Historical trend analysis
* Time-based performance monitoring
* Interactive business reporting and visualization

---

## Dataset Summary

| Component                 | Volume              |
| ------------------------- | ------------------- |
| Players                   | 500                 |
| Teams                     | 15                  |
| Tournaments               | 240+                |
| Maps                      | 10                  |
| Match Types               | 5                   |
| Match Performance Records | 1,000,000+          |
| Date Coverage             | Jan 2023 – Dec 2024 |


Data Warehousing and Business Intelligence (IT3021)
Sri Lanka Institute of Information Technology (SLIIT)
