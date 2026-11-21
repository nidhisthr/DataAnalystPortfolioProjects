# COVID-19 Data Exploration Using SQL Server

This project uses SQL queries to explore COVID-19 cases, deaths, population-level infection rates, and vaccination progress. The analysis is written in T-SQL and is intended to practise extracting, aggregating, and comparing public-health indicators across locations and dates.

## Analysis Scope

The SQL script explores the following questions:

- How do reported COVID-19 cases and deaths compare over time?
- What is the reported death percentage relative to total cases?
- How do cumulative cases compare with population size across countries?
- Which countries and continents have the highest recorded case and death counts in the loaded dataset?
- What do global case totals, death totals, and the overall death percentage look like?
- How does cumulative vaccination coverage develop by location over time?

## SQL Techniques Demonstrated

- Filtering and sorting records with `WHERE` and `ORDER BY`.
- Aggregating data with `SUM()` and `MAX()`.
- Grouping results by country/location and continent with `GROUP BY`.
- Joining case/death and vaccination tables by location and date.
- Calculating percentages and derived metrics.
- Using window functions to calculate running vaccination totals by location.
- Structuring intermediate analysis with a Common Table Expression (CTE).
- Creating and querying a temporary table.
- Creating a view for subsequent reporting or visualisation.

## Technology

- Microsoft SQL Server
- T-SQL
- SQL Server Management Studio (SSMS) or another compatible SQL client

## Database Requirements

The script expects an existing SQL Server database named `PortfolioProject` with these tables:

- `CovidDeaths`
- `CovidVaccinations`

The SQL file references them as `PortfolioProject..CovidDeaths` and `PortfolioProject..CovidVaccinations`. The repository contains the analysis script, not the source tables or a database backup. Import the source data and create the expected schema before running the queries.

## How to Run

1. Prepare a SQL Server instance.
2. Create or restore a database named `PortfolioProject`.
3. Import the COVID-19 deaths/cases data into `CovidDeaths` and vaccination data into `CovidVaccinations`.
4. Confirm that the tables contain the columns used by the queries, including location, continent, date, cases, deaths, vaccinations, and population.
5. Open [`COVID Portfolio Project.sql`](./COVID%20Portfolio%20Project.sql) in SSMS.
6. Run the analysis sections after confirming the database and table names.

## Important Validation Before Reuse

The current script should be reviewed before being used for a formal portfolio demonstration:

- **Infection-rate percentage calculation:** The `PercentagePopulationInfected` expressions multiply by `100.0` and then multiply by `100` again. Remove the extra final `* 100` so the result is expressed as a percentage only once. Apply the correction to both the row-level and country-level infection-rate calculations.
- **View creation batch:** In SQL Server, `CREATE VIEW` must be the first statement in its batch. Add a `GO` batch separator before the `CREATE VIEW` statement (after the preceding temporary-table query) when running the script in SSMS.
- **Dataset transparency:** Add the original data source, data version/date range, and applicable license or attribution here. These details are not specified in the current repository.
- **Reproducibility:** Document the required table schema or provide a permitted schema/data-loading script so another analyst can set up the database.

Validate the corrected percentages and run the full script against a clean database before describing the resulting figures as final findings.
