## Data
1. data_ecuador_annual.zip: the raw and unmerged panel data.
2. ecuador_data.rds: the merged panel data, with an added year column.

Some information on the panel that we have:
* It contains a total of 13 time steps, from 2007 until 2019. Some variables are only available for about the last 5 timesteps.
* It follows about 70,000 individuals. However, for the variables used in our first model, we could only find about 400 complete series.
* The median age is 26, and the median level of education is educación básica (middle school).

We have identified the variables below as most important to our discussion:

### Define cluster convention
**Clusters**
* person&dagger; (level 1)
* household_id&dagger; (level 2)
* home_id&dagger; (level 3)
* conglomerado&dagger; (level 4)
* city&dagger; (level 5)

**Socioeconomic**
* income_labour
* hours_worked
* sex&Dagger;
* age&Dagger;
* level_of_education
* job_type
* job_category
* income_self_employed
* has_received_human_dev_bond&Dagger;
* amount_human_dev_bond
* income_pc&Dagger;
* has_received_handicap_bond
* amount_handicap_bond
* enrolled_classes
* years_of_schooling

**Psychosocial (preferences, subjective experience)**
* job_feeling
* security_neighb
* sad_due_to_LowIncome
* sad_due_manyworkhours
* poverty&Dagger; (self-perception of being poor or not)
* extr_poverty (self-perception of being extremely poor)

**Environmental (access to physical and technological infrastructure)**
* has_received_free_school_uniform&Dagger;
* has_received_school_breakfast&Dagger;
* frequency_of_school_breakfast
* medical_insurance
* social_security
* active_cellular
* mobile_has_wifi
* used_internet_last12months&Dagger;
* area (urban vs rural, I think)

&dagger; All cluster values can be relevant, and part of the task at hand is to figure out which ones are best to include, and how to do so.

&Dagger; These are the variables used in our first conceptual model, and which we think are the most relevant ones to start our analysis with.

## The code 
Note that, for now, **our variables of interest are those marked with a &Dagger; above.** This means that questions of imputation, modelling, and cleaning, apply chiefly to these variables. As time goes on the list of relevant variables will likely change.

0. **SaveAndMergePanel.py**: This file loads the yearly panel, merges it into a single table.
1. **TranslationAndCleaning.py**: Should translate the Spanish column names into English, adds some necessary columns, and fixes some typo's. This is where cleaning and defining of new variables takes place.
2. **Imputation.py**: Impute the required variables.
   * A very important step, and we are unsure how to proceed here. What is the most statistically rigorous way to impute these values? Also requires some input from 3.

### Some Comments
* Work has to be done to understand what data is missing, and (possibly) why.
* Some work also has to be done to understand what levels of clustering are most relevant, and for which variables (e.g., is someone most influenced by the average level of education in their household, neighborhood, or city?) 
* Comments are used in two ways: as titles of a particular section above the code, and to note some interesting results below the code.

## Possible next steps
### Visualization of distributions of relevant variables
### Intracluster correlation
#### Run a simple hierarchical analysis (multilevel analysis)
### Define an interaction matrix
#### make an edgelist where 1 equals similar activitie between two agents and 0 means no similar activity
