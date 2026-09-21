# Chennai Green & Pollution Analytics

A SQL-based **Chennai Green & Pollution Analytics System** developed using MySQL to manage and analyze environmental data across different areas and zones of Chennai. The project focuses on analyzing **pollution levels, AQI, tree plantation, funding, workers, transportation, nurseries, salaries, and maintenance activities** to generate meaningful environmental insights.

## Project Overview

The Chennai Green & Pollution Analytics System is designed to simulate real-world environmental management and analytics operations. The system helps analyze pollution levels and identify areas that may require increased tree plantation and maintenance activities.

The project focuses on:

- Database Design
- Relational Database Management
- Pollution Data Analysis
- AQI Analysis
- Tree Plantation Analytics
- Funding Analysis
- Worker Management
- Nursery Resource Management
- Worker Transportation Management
- Maintenance Tracking
- SQL Query Optimization
- Reporting & Insights Generation

This project demonstrates practical SQL and database management skills using a real-world environmental analytics scenario.

## Features

### Pollution Management
- Store pollution information for different areas
- Track AQI levels
- Maintain NO₂ and SO₂ values
- Identify highly polluted areas
- Categorize areas based on AQI levels
- Compare AQI between different areas

### Area & Zone Management
- Maintain Chennai area details
- Organize areas into different zones
- Track location types
- Analyze pollution and plantation activities by zone

### Tree Plantation Management
- Store plantation records
- Track different tree types
- Maintain the quantity of trees planted
- Identify areas with low plantation activity
- Analyze total trees planted in each area

### Worker Management
- Maintain worker details
- Track different worker types
- Assign workers to plantation activities
- Track worker work hours
- Maintain worker salary information

### Worker Transportation Management
- Maintain transportation details for workers
- Track transport-related information
- Associate transportation records with workers
- Support analysis of worker transportation requirements

### Nursery Management
- Store nursery details
- Track nursery locations
- Maintain available tree types
- Track total trees available
- Maintain nursery contact information

### Funding Management
- Store funding received by different areas
- Track environmental/government funding
- Identify highly funded areas
- Compare funding with plantation activities
- Identify funded areas with limited or no plantation activity

### Maintenance Management
- Track maintenance activities
- Maintain maintenance-related records
- Analyze maintenance requirements
- Support monitoring of plantation and green-area maintenance

### Salary Management
- Maintain worker salary information
- Analyze salary information by worker
- Support worker-related cost analysis

## Technologies Used

| Technology | Description |
|---|---|
| **MySQL** | Database Management System |
| **SQL** | Query Language |
| **MySQL Workbench** | Database Modeling and Query Execution |

## Database Tables

The project contains **12 tables**:

| Table Name | Description |
|---|---|
| `pollution` | Stores AQI, NO₂ and SO₂ pollution information |
| `zones` | Stores Chennai zone information |
| `workers` | Stores worker details and worker types |
| `nurseries` | Stores nursery and available tree information |
| `areas` | Stores Chennai area information |
| `planting` | Stores tree plantation records and quantities |
| `funding` | Stores funding received by areas |
| `planting_worker` | Connects workers with plantation activities and work hours |
| `trees` | Stores tree type information |
| `salary` | Stores worker salary information |
| `worker_transports` | Stores worker transportation information |
| `maintenance` | Stores maintenance activity information |

## Entity Relationship Highlights

- One **zone** can contain multiple areas.
- One **area** can have pollution information.
- One **area** can have multiple planting records.
- One **area** can receive funding.
- Workers can be assigned to plantation activities through `planting_worker`.
- One worker can have salary information.
- Workers can have transportation information.
- Nurseries maintain information about available trees.
- Tree records support analysis of different tree types.
- Maintenance records help track maintenance activities.
- Relationships between these tables allow combined environmental analysis using SQL joins.

## SQL Concepts Used

The project demonstrates the following SQL concepts:

- DDL
- DML
- Constraints
- Primary Keys
- Foreign Keys
- Joins
- Aggregate Functions
- `GROUP BY`
- `HAVING`
- `ORDER BY`
- Subqueries
- Multi-row Subqueries
- Correlated Subqueries
- CTEs
- Window Functions
- `RANK()`
- `DENSE_RANK()`
- `ROW_NUMBER()`
- `LAG()`
- `LEAD()`
- `CASE`
- Views
- Stored Procedures
- Triggers
- Indexing
- Partitioning

## Sample Analytical Queries

### 1. Find Areas with AQI Greater Than 200

```sql
SELECT area_id,
       aqi
FROM pollution
WHERE aqi > 200;
```

### 2. Find Areas with AQI Greater Than Average AQI

```sql
SELECT area_id,
       aqi
FROM pollution
WHERE aqi > (
    SELECT AVG(aqi)
    FROM pollution
);
```

### 3. Find Areas with More Than 500 Trees

```sql
SELECT area_id,
       SUM(quantity) AS total_trees
FROM planting
GROUP BY area_id
HAVING SUM(quantity) > 500;
```

### 4. Rank Areas Based on AQI

```sql
SELECT area_id,
       aqi,
       RANK() OVER (
           ORDER BY aqi DESC
       ) AS aqi_rank
FROM pollution;
```

### 5. Find Top 3 Funded Areas

```sql
SELECT area_id,
       received_amount,
       ROW_NUMBER() OVER (
           ORDER BY received_amount DESC
       ) AS funding_rank
FROM funding
LIMIT 3;
```

### 6. Find Workers Not Assigned to Planting

```sql
SELECT w.worker_id,
       w.worker_name
FROM workers w
LEFT JOIN planting_worker pw
       ON w.worker_id = pw.worker_id
WHERE pw.worker_id IS NULL;
```

### 7. Find Funding Without Planting

```sql
SELECT f.area_id,
       f.received_amount
FROM funding f
LEFT JOIN planting p
       ON f.area_id = p.area_id
WHERE p.area_id IS NULL;
```

## Project Objectives

- Analyze pollution levels across Chennai.
- Identify areas with high AQI.
- Analyze tree plantation activities.
- Identify areas requiring additional plantation.
- Track environmental funding.
- Analyze worker participation.
- Manage nursery resources.
- Track worker transportation.
- Monitor maintenance activities.
- Analyze worker-related costs.
- Generate data-driven environmental insights.
- Support better green-area planning.

## Learning Outcomes

This project helped improve my knowledge of:

- Advanced SQL
- Database Design
- Relational Database Modeling
- Joins
- Subqueries
- CTEs
- Window Functions
- Views
- Stored Procedures
- Triggers
- Indexing
- Partitioning
- Query Optimization
- Data Analysis
- Real-world SQL Problem Solving

## Future Enhancements

- Power BI Dashboard Integration
- Web Application Integration
- Real-time AQI Data Integration
- Interactive Chennai Pollution Map
- Automated Pollution Alerts
- AI-Based Pollution Prediction
- Automated Plantation Recommendations
- Real-time Environmental Monitoring
- Predictive Maintenance Analysis

## How to Run the Project

### Step 1: Install MySQL

Install:

- MySQL Server
- MySQL Workbench

### Step 2: Create Database

```sql
CREATE DATABASE chennai_green_analytics;

USE chennai_green_analytics;
```

### Step 3: Create Tables

Create the required 12 tables:

```text
pollution
zones
workers
nurseries
areas
planting
funding
planting_worker
trees
salary
worker_transports
maintenance
```

### Step 4: Insert Data

Insert sample pollution, area, zone, plantation, worker, nursery, funding, transportation, salary, tree, and maintenance data.

### Step 5: Execute Analytical Queries

Run SQL queries to analyze:

- AQI and pollution levels
- High-pollution areas
- Tree plantation
- Funding
- Worker activities
- Worker transportation
- Nursery resources
- Maintenance activities
- Area and zone performance

## Project Conclusion

The **Chennai Green & Pollution Analytics System** is a MySQL-based environmental analytics project that demonstrates practical knowledge of database design, relational data modeling, advanced SQL, and data analysis.

The system combines pollution, AQI, tree plantation, funding, workers, nurseries, salaries, transportation, and maintenance data to generate meaningful environmental insights.

Through this project, SQL can be used not only to store environmental data but also to **identify high-pollution areas, analyze plantation activities, compare funding, track resources, and support data-driven green planning for Chennai**.
