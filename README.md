# MediTrack — Hospital Management SQL Project

A MySQL database project for managing core hospital operations, including patient records, doctors, appointments, prescriptions, and billing. The project demonstrates relational database design and practical SQL querying for operational and revenue analysis.

## Project Overview

**MediTrack** is a sample hospital-management database built in MySQL 8.0. It contains five related tables and example queries for retrieving records, aggregating metrics, joining data across tables, and creating database objects for reusable analysis.

> **Note:** The dataset is fictional and intended for learning and demonstration only. It should not be used for real clinical or patient-care decisions.

## Database Schema

The database is named `MediTrack`.

| Table | Purpose | Key fields |
|---|---|---|
| `Patients` | Stores patient demographics and contact details | `Patient_ID` (primary key), `Email` |
| `Doctors` | Stores doctors, specializations, consultation fees, and experience | `Doctor_ID` (primary key) |
| `Appointments` | Connects patients with doctors for dated appointments | `Appointment_ID` (primary key), `Patient_ID` and `Doctor_ID` (foreign keys) |
| `Prescriptions` | Stores medicines prescribed during appointments | `Prescription_ID` (primary key), `Appointment_ID` (foreign key) |
| `Billing` | Stores appointment charges and payment information | `Bill_ID` (primary key), `Appointment_ID` (foreign key) |

### Relationships

- One patient can have multiple appointments.
- One doctor can have multiple appointments.
- An appointment can have multiple prescriptions.
- An appointment can have a billing record.

## Dataset

The sample data in the project contains:

- 20 patient records
- 15 doctor records
- 10 appointment records
- 13 prescription records
- 10 billing records

All 10 recorded appointments are marked as `Completed`, and all 10 billing records are marked as `Paid`.

## SQL Skills Demonstrated

- Database and table creation (`CREATE DATABASE`, `CREATE TABLE`)
- Primary and foreign keys
- Data insertion (`INSERT INTO`)
- Filtering with `WHERE`
- Sorting and limiting results (`ORDER BY`, `LIMIT`)
- Joins across related tables
- Aggregate functions: `COUNT`, `SUM`, `AVG`, and `MAX`
- Grouping and filtering grouped results (`GROUP BY`, `HAVING`)
- Subqueries
- Window functions for cumulative revenue
- Indexes, including a unique index
- Views for reusable summaries

## Example Business Questions

The project uses SQL to answer questions such as:

1. Which doctors have the highest consultation fees?
2. Which medicines were prescribed to a particular patient?
3. How many appointments have been completed?
4. What is the total billing amount by patient?
5. Which payment methods generate the most revenue?
6. Which doctor specialization has the highest recorded revenue?
7. Which doctors have no appointments in the sample data?
8. What is the cumulative revenue over appointment dates?
9. Which appointments have more than one prescription?
10. Which bills are greater than the average bill amount?

## Key Findings from the Sample Data

- **Total recorded billing:** 6,800.00 (currency not specified in the source project).
- **Highest single bill:** 1,000.00.
- **Highest-revenue payment method:** Credit Card, with 3,500.00 across 4 transactions.
- **Other revenue by payment method:** UPI 1,250.00; Cash 1,200.00; Debit Card 850.00.
- **Highest-revenue specialization in the recorded appointments:** Oncology, with 1,000.00.
- **Doctors without a recorded appointment:** 5.
- **Bills above 700.00:** 4 records, based on the `HighValueBills` view condition (`Amount > 700`).

These findings describe only the included sample data and are not representative of a real hospital.

## Getting Started

### Requirements

- MySQL Server 8.0 or compatible
- MySQL Shell or another MySQL client

### Run the project

1. Open your MySQL client and connect to your local MySQL server.
2. Create and select the database:

   ```sql
   CREATE DATABASE MediTrack;
   USE MediTrack;
   ```

3. Create the five tables using the table definitions in the project.
4. Insert the sample records into each table.
5. Run the analysis queries to reproduce the results.

**Suggested repository structure:**

```text
MediTrack-SQL-Project/
├── README.md
├── schema.sql       # Database and table definitions
├── data.sql         # Sample INSERT statements
└── queries.sql      # Analysis queries, indexes, and views
```

The original project document records SQL statements and their results. If you upload separate `.sql` files to GitHub, place the corresponding statements in the suggested files above.

## Database Objects Created

### Indexes

- `idx_patient_id` on `Appointments(Patient_ID)`
- Unique index `idx_email` on `Patients(Email)`

### Views

- `HighValueBills`: returns billing records where `Amount > 700`
- `RevenueSummary`: summarizes total revenue by payment method

Example:

```sql
SELECT *
FROM RevenueSummary;
```

## Limitations

- The dataset is small and illustrative.
- The recorded appointments all occur in January 2024.
- Each patient has one appointment in the sample data, so the dataset does not demonstrate repeat visits.
- All billing records are marked as paid; unpaid-bill workflows are not represented.
- The source project does not specify the currency for billing amounts.
- The project document contains command-line output as well as SQL. For a clean, reproducible GitHub repository, keep schema definitions, sample data, and analysis queries in separate `.sql` files.

## Future Improvements

- Add a single, reproducible SQL script that builds the database from scratch.
- Add appointment statuses such as `Scheduled`, `Cancelled`, and `No-show`.
- Add payment tracking for unpaid and partially paid bills.
- Add doctor availability and appointment scheduling constraints.
- Add more sample data to support trend analysis over multiple months.
- Add a dashboard using Power BI, Tableau, or Python.

## Author

**AG**  
SQL | Data Analysis | Database Design

---

If you found this project useful, feel free to ⭐ the repository.
