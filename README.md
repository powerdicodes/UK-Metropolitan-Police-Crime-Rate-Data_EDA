# UK London Metropolitan Police Service 2025 Crime Data_EDA

About the Dataset:

London Street-Level Crime Data (2025)

This dataset, sourced from data.police.uk, provides monthly street level crime records including outcomes 
across all areas of England, Wales, and Northern Ireland. For London, governed by the Metropolitan Police Service.


## Key Data Columns Explained (UK Police Crime Data)

| **Column Name**           | **Description**                                                                                         |
|---------------------------|---------------------------------------------------------------------------------------------------------|
| **Crime ID**              | Unique identifier for each crime report. Useful for tracking and linking updates.                       |
| **Month**                 | Reporting month in `YYYY-MM` format, representing when the crime was recorded.                          |
| **Reported by**           | Police force that recorded the crime (e.g., *Metropolitan Police Service*, *City of London Police*).    |
| **Crime type**            | General category of the offence (e.g., *Drugs*, *Burglary*, *Violence and sexual offences*).            |
| **Last outcome category** | The most recent outcome of the case (e.g., *No suspect identified*, *Under investigation*).             |
| **LSOA name**             | Lower Layer Super Output Area – a small geographic area used for demographic statistics.                |
| **Location**              | Anonymised approximate location (e.g., *On or near High Street*, *Near Shopping Centre*).               |
| **Latitude, Longitude**   | Approximate coordinates for mapping. These are slightly adjusted for privacy.                           |


Attribution

> **Source:** [data.police.uk](https://data.police.uk/data/)  
> **License:** Contains public sector information licensed under the [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).


## Additional information regarding the datasets:

Due to GitHub's file upload limit per file, the original dataset crime records in London for January to June 2025 was split into two separate files:
1. Q1 Street Crime Level Dataset: UK_Crime_Q1_2025 (January to March 2025)
2. Q2 Street Crime Level Dataset: UK_Crime_Q2_2025 (April to June 2025)
3. Q1 Outcomes Dataset: UK_Outcomes_Q1_2025 (January to March 2025)
4. Q2 Outcomes Dataset: UK_Outcomes_Q2_2025 (April to June 2025)

This approach allows for:
1. Easier file management and quicker downloads
2. Compatibility with GitHub hosting constraints
3. flexible analysis for quarterly trends
> Both files are stored in the /data directory and maintain a consistent schema

For eploratory data analysis (EDA) it is recommended to combine both quarterly datasets into a single table before analysis. This ensures:
1. Complete time-series continuity from January to June 2025 
2. Accurate aggregations and filtering across the full date range 
3. Simplified query logic for dashboards and reporting

You can combine the files:
1. By merging them in a spreadsheet before importing
2. Or by importing both into a staging table and using a UNION ALL query to consolidate the data
> Ensure the column order and data types match exactly when combining

Data Cleaning:
Prior to being uploaded and analyzed, the original dataset was cleaned and processed in Microsoft Excel, including:
1. Assesment of any empty or invalid rows and its possible impact to the quality of the data
2. Standardizing column names 
3. Imputating or correcting missing values where appropriate
4. Ensuring consistent formatting for dates and categories
> This pre-cleaned structure ensures readines for loading into Power BI, SQL databases, or any analysis tools.

