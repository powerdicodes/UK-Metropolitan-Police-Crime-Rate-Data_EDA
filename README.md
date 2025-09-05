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
1. Q1 Street Crime Level Dataset: UK_CrimeData_Q1_2025 (January to March 2025)
2. Q2 Street Crime Level Dataset: UK_CrimeData_Q2_2025 (April to June 2025)
3. Q1 Outcomes Dataset: UK_CrimeOutcomes_Q1_2025 (January to March 2025)
4. Q2 Outcomes Dataset: UK_CrimeOutcomes_Q2_2025 (April to June 2025)

This approach allows for:
* Easier file management and quicker downloads
* Compatibility with GitHub hosting constraints
* flexible analysis for quarterly trends
> Both files are stored in the /data directory and maintain a consistent schema

For eploratory data analysis (EDA) it is recommended to combine both quarterly datasets into a single table before analysis. This ensures:
* Complete time-series continuity from January to June 2025 
* Accurate aggregations and filtering across the full date range 
* Simplified query logic for dashboards and reporting

You can combine the files:
* By merging them in a spreadsheet before importing
* Or by importing both into a staging table and using a UNION ALL query to consolidate the data
> Ensure the column order and data types match exactly when combining

## Data Cleaning
Prior to being uploaded and analyzed, the original dataset was cleaned and processed in Microsoft Excel, including:
* Assesment of any empty or invalid rows and its possible impact to the quality of the data
* Standardizing column names 
* Imputating or correcting missing values where appropriate
* Ensuring consistent formatting for dates and categories
> This pre-cleaned structure ensures readines for loading into Power BI, SQL databases, or any analysis tools.

## Database Issues Log

| **Table**              | **Column**              | **Issue**                                                 | **Row Count** | **Magnitude%** | **Magnitude\$** | **Solvable?** | **Resolution**                                                                                    | **Decision Context / Remarks**                                                                                  |
| ---------------------- | ----------------------- | --------------------------------------------------------- | ------------- | -------------- | --------------- | ------------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `UK_CrimeData_2025`  | `Crime ID`              | Missing Crime ID details                                  | 91,280        | 20.19%         | n/a             | ✅ Yes         | No action needed                                                                                  | Missing Crime IDs could possibly relate to "Anti-Social Behaviour" in the Crime Types column                    |
| `UK_CrimeData_2025`  | `Last outcome category` | Imputation needed for outcomes not in the public interest | 544           | 0.12%          | n/a             | ✅ Yes         | Narrowed down to one single category                                                              | Affected crime types were all similar                                                                           |
| `UK_CrimeData_2025`  | `Last outcome category` | No outcome for Anti-Social Behaviour                      | 91,280        | 20.19%         | n/a             | ✅ Yes         | Inquiry with the concerned department. Imputed as “Further action is not in the public interest.” | For analysis/visualization purposes, outcome is standardized                                                    |
| `UK_CrimeOutcomes_2025` | `Outcome type`          | Need to extract latest outcome using helper columns       | n/a           | n/a            | n/a             | ✅ Yes         | Created helper columns to determine the latest outcome based on timestamp and outcome rank        | Since timestamps are in months, verification was required to ensure latest records reflect most recent outcomes |

Other observations
* No duplicates noted in the Crime ID column
