# Steps for Calculating Incidence Rates

## Assignment Objective

Calculate the incidence rates of `Asthma_possible` and `Asthma_narrow` in females and males from 2010 to 2022, aged 0 to 120 years, stratified by year and by year and age bands.

**Age Bands:** - 0–19 years\
- 20–39 years\
- 40–59 years\
- 60+ years

------------------------------------------------------------------------

## Step 1: Define the Study Objectives

### 1. State the Aim

Clearly identify the condition or event (e.g., asthma diagnoses) for which you want to calculate incidence rates.

### 2. Define the Study Population

-   Specify inclusion criteria (e.g., age, sex, time period: 2010–2022).\
-   Specify exclusion criteria (e.g., incomplete data, subjects outside the age range).

------------------------------------------------------------------------

## Step 2: Understand and Prepare the Data

### 1. Identify Key Variables

Ensure the dataset contains: - **Event date** (e.g., `start_date_record` in the EVENTS table)\
- **Observation period** (e.g., observation start/end dates in OBSERVATION_PERIODS)\
- **Individual identifiers** (e.g., `person_id`)\
- **Covariates** (e.g., birth date, sex)

### 2. Clean the Data

-   Remove duplicates.\
-   Handle missing/invalid data (e.g., use complete case analysis).\
-   Standardize date formats and check for valid entries.

### 3. Create the Study Population

-   Merge PERSONS with OBSERVATION_PERIODS.\
-   Exclude subjects with impossible birthdates.\
-   Impute missing `birth_date` and `death_date` values:
    -   Default month: July (07)\
    -   Default day: 15\
-   Convert date variables from character strings to date format.\
-   Apply inclusion/exclusion criteria to observation start and end dates.

### 4. Fix the Code List for Filtering

-   Ensure tags (e.g., "possible" and "narrow") are stored and formatted correctly.\
-   Validate columns for coding system, code, and tags.\
-   Address missing or empty codes.

------------------------------------------------------------------------

## Step 3: Aggregate Person-Time

### 1. Determine Observation Periods

-   Define start and end dates for follow-up (e.g., enrollment to event, study end, or death).\
-   Censor data at the first event occurrence.

### 2. Stratify the Data

Define strata by year and age groups:

**Age Bands:** - 0–19\
- 20–39\
- 40–59\
- 60+

### 3. Sum Person-Time

Calculate total person-time (in years) for each stratum.

------------------------------------------------------------------------

## Step 4: Identify and Count Events

### 1. Define the Event of Interest

Specify criteria for what qualifies as an "event" (e.g., diagnosis codes for asthma).

### 2. Count Events per Stratum

Count only one event per subject per stratum.

------------------------------------------------------------------------

## Step 5: Calculate Incidence Rates

### 1. Formula

$$
IR = \frac{\text{Number of events}}{\text{Total person-time}}
$$

### 2. Calculate IR for Each Stratum

-   Divide the event count by total person-time for each stratum.\
-   Express rates per 1,000 person-years:\
    $$
    IR \times 1000
    $$

------------------------------------------------------------------------

## Step 6: Visualize Results

### 1. Create Plots

-   **Time Trends:** Plot year vs. incidence rate.\
-   **Stratified Rates:** Display incidence rates by age groups or other stratifications.

### 2. Highlight Key Findings

Use bar charts, line graphs, or heatmaps to emphasize trends and comparisons.
