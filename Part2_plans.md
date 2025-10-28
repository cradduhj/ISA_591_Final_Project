* possibly collapse territory into regions (consider territory as control variable? ask Dr. Farmer)
* reverse transform some of the numeric columns if they don't perform well in the models (consider tree models that don't care about skew)
* reverse bin the "years since" variables that may do better as numeric in terms of predictive power




* collapse application_type into INDIVIDUAL and OTHER; if predictive, split later
* collapse pub_rec_bankruptcies into 0 and 1+; if predictive, split later
* lump purpose into 4 levels plus OTHER; if predictive, split later
* possibly remove acc_now_delinq if 1+ is not predictive as would be constant
* collapse delinq_2yrs to 0, 1, 2+ to start, possibly 1+; if predictive, split later
* possibly remove observations with NEVER for last_credit_pull_d_years_since
* 
