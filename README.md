# Employee Exit Survey

In this project, we'll work with exit surveys from employees of the [Department of Education, Training and Employment](https://en.wikipedia.org/wiki/Department_of_Education_(Queensland)) (DETE) and the [Technical and Further Education](https://en.wikipedia.org/wiki/Technical_and_further_education) (TAFE) institute in Queensland, Australia. You can find the TAFE exit survey [here](https://data.gov.au/dataset/ds-qld-89970a3b-182b-41ea-aea2-6f9f17b5907e/details?q=exit%20survey) and the survey for the DETE [here](https://data.gov.au/dataset/ds-qld-fe96ff30-d157-4a81-851d-215f2a0fe26d/details?q=exit%20survey). 

## Aim

To examine exit survey of educational institutions in Australia to determine whether employees who worked for the institute resigned due to some kind of dissatisfaction.

## Dataset

Below are a couple of columns in `dete_survey.csv` dataset:

* `ID`: An id used to identify the participant of the survey
* `SeparationType`: The reason why the person's employment ended
* `Cease Date`: The year or month the person's employment ended
* `DETE Start Date`: The year the person began employment with the DETE
* `NESB`: Non English speaking background

Below are a couple of columns in `tafe_survey.csv` dataset:

* `Record ID`: An id used to identify the participant of the survey
* `Reason for ceasing employment`: The reason why the person's employment ended
* `LengthofServiceOverall. Overall Length of Service at Institute (in years)`: The length of the person's employment (in years)

## Data Cleaning

* Reading dete_survey dataset with correct values
* Dropping unnecessary columns
* Renaming columns
* Filtering only resignation data for further analysis
* To verify the years in cease_date and dete_start_date columns make sense.
* Create a new column to store duration of employment in DETE dataset.

### Identifying dissatisfied employees.

We'll identify any employees who resigned because they were dissatisfied. Below are the columns we'll use to categorize employees as "dissatisfied" from each dataframe. 

* tafe_survey_updated:
    * Contributing Factors. Dissatisfaction
    * Contributing Factors. Job Dissatisfaction
* dete_survey_updated:
    * job_dissatisfaction
    * dissatisfaction_with_the_department
    * physical_work_environment
    * lack_of_recognition
    * lack_of_job_security
    * work_location
    * employment_conditions
    * work_life_balance
    * workload

If the employee indicated any of the factors above caused them to resign, we'll mark them as dissatisfied in a new column. To create the new column, we'll do the following:

* Convert the values in the 'Contributing Factors. Dissatisfaction' and 'Contributing Factors. Job Dissatisfaction' columns in the tafe_resignations dataframe to True, False, or NaN values.

* If any of the columns listed above contain a True value, we'll add a True value to a new column named dissatisfied. 

After our changes, the new dissatisfied column will contain just the following values:

* `True`: Indicates a person resigned because they were dissatisfied with the job
* `False`: Indicates a person resigned because of a reason other than dissatisfaction with the job
* `NaN`: Indicates the value is missing

## Data Analysis

* Combining both DETE and TAFE datasets into a single dataset.
* Cleaning the `institute_service` column and categorize employees according to the following definitions:

    * New: Less than 3 years in the workplace
    * Experienced: 3-6 years in the workplace
    * Established: 7-10 years in the workplace
    * Veteran: 11 or more years in the workplace

* Calculate the percentage of employees who resigned due to dissatisfaction in each experience level.

## Conclusion

We can conclude that employees with 7 or more years of service are more likely to resign due to some kind of dissatisfaction with the job than employees with less than 7 years of service. 
