* collapse application_type into INDIVIDUAL and OTHER; if predictive, split later
* collapse pub_rec_bankruptcies into 0 and 1+; if predictive, split later
* lump purpose into 4 levels plus OTHER; if predictive, split later
* possibly remove acc_now_delinq if 1+ is not predictive as would be constant
* collapse delinq_2yrs to 0, 1+; if predictive, split later
* possibly remove observations with NEVER for last_credit_pull_d_years_since; then convert to numeric as years since with no bins
* unlog and uncap all numeric variables for tree-based models
* collapse territory into regions
* run RF on subgrade and loan_default vs. grade and loan_default
* run RF on territory and loan_default vs. region and loan_default

* save RDS of final training data cleaning

* create new RMD for data cleaning of holdout, save to RDS

* create three RMDs, one for each tree, and read in train and holdout RDSs
