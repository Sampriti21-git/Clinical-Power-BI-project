## Diabetes Management Analytics Dashboard---

## Project Overview:

This project is an end-to-end clinical data analysis solution built entirely in Microsoft Power BI. It analyzes a comprehensive, multi-source dataset of diabetic patients to monitor glycemic control, medication patterns, and complication trends.

The goal is to provide a single, interactive dashboard for healthcare professionals and data analysts to derive actionable insights from patient data, such as identifying high-risk patient groups or evaluating treatment intensity.

## Project Files:

-   Dashboard.pbix: The final, interactive Power BI dashboard file containing all transformations, measures, and visuals.
-   Diabetes Data worksheet.xlsx - Patients.csv: The core patient demographic data, including diabetes type and duration.
-   Diabetes Data worksheet.xlsx - Lab_Results.csv: Patient-specific lab values, primarily focusing on HbA1c and glucose levels.
-   Diabetes Data worksheet.xlsx - Medications.csv: A log of all prescribed medications, doses, and dates for each patient.
-   Diabetes Data worksheet.xlsx - Complications.csv: Patient-level data on the presence of common diabetes-related complications (e.g., Neuropathy, Retinopathy).

## Key Skills & Tools Demonstrated:

-   *Microsoft Power BI Desktop*
-   *ETL (Power Query)*: Advanced data cleaning, merging, and transformation.
-   *Data Modeling*: Building a robust Star Schema and resolving relationship ambiguities.
-   *DAX (Data Analysis Expressions)*: Authoring complex measures for KPIs and analysis.
-   *Dashboard Design*: Creating a clean, interactive, and single-page dashboard.
-   *Clinical Data Analysis*: Applying domain knowledge to create meaningful metrics.

## Project Workflow: A Four-Stage Process

This project was built following a standard business intelligence workflow, from data ingestion to final visualization.

### Stage 1: ETL (Power Query)
The four raw CSV files were loaded into the Power Query Editor for transformation and cleaning.
-   *Medications Table:* To solve the one-to-many relationship issue (one patient, multiple meds), the table was grouped by Patient_ID. The Text.Combine and List.Transform functions were used to create a new column that aggregates all medications and their doses into a single, clean text string for each patient (e.g., "Metformin (500 mg BID), Glimepiride (1 mg OD)").
-   *Complications Table:* This "wide" table was *unpivoted* to create a "long" format. This transformation was essential for enabling analysis and filtering by the type of complication.
-   *Calculated Columns:* New columns such as Age Group were created to facilitate demographic filtering.

### Stage 2: Data Modeling (Model View)
A robust *Star Schema* was built to manage the data efficiently.
-   The Patients table was established as the central *dimension table* (the "one" side).
-   The Lab_Results, Medications (now aggregated), and Complications (unpivoted) tables were set as *fact tables* (the "many" side).
-   This model resolves all "ambiguous paths" and ensures that filters and slicers propagate correctly through the dashboard.

### Stage 3: Analysis & DAX Measures
Over a dozen DAX measures were written to power the dashboard's KPIs and charts. Key measures include:
-   Average HbA1c: The primary metric for glycemic control, with conditional formatting.
-   % of Patients with Good Control: Calculates the percentage of patients with HbA1c < 7%.
-   Combination Therapy %: A measure that identifies patients on two or more medications to track treatment intensity.
-   Complication Rate %: A measure that calculates the percentage of patients who have at least one reported complication.

### Stage 4: Visualization (Dashboard Design)
A single-page, interactive dashboard was designed for a clean user experience.
-   All visuals are designed to work together to tell a cohesive story about the patient population.
-   *Edited Interactions:* Slicer interactions were manually edited. For example, some slicers were set to filter charts but not the main patient detail table, providing a stable reference list.

## Dashboard Features:

-   *KPI Cards:* A top-level row displaying the most critical metrics: Average HbA1c, % Patients with Good Control, Combination Therapy %, and Complication Rate %.
-   *Charts for Complications:* A multi-column bar chart shows the total count of patients for each specific complication (Neuropathy, Retinopathy, etc.).
-   *Charts for Medication:* A donut chart visualizes the breakdown of patients on Monotherapy vs. Combination Therapy.
-   *Interactive Slicers:* The dashboard can be filtered by Age Group, Gender, Type of Diabetes, and Family History.
-   *Detailed Patient Table:* A comprehensive table view shows individual patient details. This table was enhanced with:
    -   Data from multiple tables (Patient info, Lab results, and the combined medication list).
    -   Conditional formatting (e.g., coloring HbA1c values based on risk).

## How to Use:

1.  Download and open the Dashboard.pbix file in Microsoft Power BI Desktop.
2.  Allow the file to load and refresh the data from the included CSV files if prompted (they may need to be in the same directory).
3.  Interact with the dashboard using the slicers at the top of the page.
4.  Click on elements within the charts (e.g., the "Type 1" bar) to cross-filter other visuals on the page.

## Author:
Sampriti Sarkar
