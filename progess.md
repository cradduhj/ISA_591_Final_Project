# Next Steps

loan_default:	Whether the loan has defaulted. Values: “Yes”, “No”.
* 2 levels: No - 80.38%, Yes - 19.62%
* response variable
* don't think it needs any changes

loan_amnt: The listed amount of the loan applied for by the borrower.
* slight right-skew, multimodal distribution

term:	The number of payments on the loan (36 or 60 months).
* 2 levels: "36 months" - 76.35%, "60 months" - 23.65%
* don't think it needs any changes

int_rate:	Interest rate on the loan.
* slight right-skew, multimodal

installment: The monthly payment owed by the borrower if the loan originates.
* light right-skew

grade: Loan grade assigned by Lending Club.
* 7 levels: "A" - "G"
* **remove grade or clasify sub_grade as range (1,5)**

sub_grade: Loan subgrade assigned by Lending Club.
* 35 levels: 1 - 5 for each "A" - "G"
* **remove grade or clasify sub_grade as range (1,5)**

emp_title: Job title supplied by the borrower.
* 112646 levels, a few common values
* has a few blank/empty values as well that we need to deal with or label

emp_length:	Employment length in years (“< 1 year” to “10+ years”).
* 12 levels: "<1" - "10+"
* possibly group these into fewer, semi-equally weighted levels
* has a few blank/empty values as well that we need to deal with or label
* **reclassify blanks as "unreported" for now**

home_ownership:	Home ownership status: RENT, OWN, MORTGAGE, OTHER.
* 5 levels: MORTGAGE, RENT, OWN, OTHER, NONE
* possibly group OTHER and NONE together
* **group OTHER and NONE together**

annual_inc: Self-reported annual income of the borrower.
* a few very large outliers
* very right-skewed
* if we removed these large outliers, would probably be normally distributed
* can we ethically include income in predicting loan default?
* **we want to try to cap or log transforming the variable**

verification_status: Whether income was verified: Verified, Not Verified, etc.
* 3 levels: "Verified", "Source Verified", "Not Verified"
* don't think it needs any changes

issue_d: The month when the loan was funded.
* 115 levels
* June 2007 - December 2016
* does issue date really matter?
* could we combine levels into seasons & years or even just years?
* **split into 'years since' and also into seperate months(possibly seasons later on)**

purpose: Category provided by the borrower for the loan request.
* 14 levels
* pretty equally weighted levels
* could possibly combine a few? not sure

title: Loan title provided by the borrower.
* 31659 levels
* a few very highly weighted levels
* seems like subcategory of purpose really
* has a few blank/empty values as well that we need to deal with or label

dti: Debt-to-income ratio.
* a few very large outliers
* very right-skewed
* if we removed these outliers, would probably be normally distributed
* probably multicollinear with income or other variables?
* **remove largest observation and try capping or log transforming like annual_inc**

earliest_cr_line:	Month of the borrower’s earliest reported credit line.
* 659 levels
* month/year format
* consider converting to years (or range of years) since earliest credit line (would certainly reduce levels)
* **years since or range of years since**

open_acc:	Number of open credit lines.
* a few large outliers
* moderately right-skewed
* if we removed these outliers, would probably be normally distributed
* **capping, convert factor and set ranges, log transfrom**

pub_rec: Number of derogatory public records.
* very right-skewed
* majority zeros
* a few large values
* consider combining into "0", "a few", "a lot", etc.
* **conver to factor and level as "0 , 1 , >1" possibly removing the single observation with >19 pub_rec**

revol_bal: Total revolving balance.
* a few very large outliers
* very right-skewed
* if we removed these outliers, would probably be normally distributed
* **not really sure, possibly try a transformation?**

revol_util:	Revolving line utilization rate (credit used / total credit).
* a few large outliers
* very right-skewed
* if we removed these outliers, would probably be normally distributed
* 177 missing values
* probably multicollinear with revol_bal, etc.
* consider PCA, removing, combining with others
* **impute missing values with 0, possibly remove or manage the largest outlier**

total_acc: Total number of credit lines in the borrower’s credit file.
* slightly right-skewed
* has a couple large outliers
* if we removed these outliers, would probably be normally distributed
* **explore the ratio with open_acc**

initial_list_status: Initial listing status of the loan: f (fractional) or w (whole).
* 2 levels: "f" - 60.05%, "w" - 39.95%
* if dictionary is true, labels should be renamed for clarity

application_type:	Type of application: individual, joint, direct pay.
* 3 levels
* "individual" accounts for 99.82% of values
* combine into "individual" and "other"?
* consider removing if not predictive since basically a constant
* **will likely leave this be since it is only 3 levels and the direct pay level seems to be highly correlated with defaulting**

mort_acc:	Number of mortgage accounts.
* very right-skewed
* lots of zeros with a few large outliers
* consider removing outliers
* 22854 missing values
* **impute missing with 1 for mortgage ownership and 0 for all others**

pub_rec_bankruptcies:	Number of public record bankruptcies.
* 336 missing values
* very right-skewed
* values range from integers 0 to 8
* consider converting to categorical with a few levels
* **convert to factor with levels "0 , 1 , >1"**
* **how to handle missing? they correspond to missings in mort_acc**

address: Borrower’s address.
* 99.58% unique values
* a few addresses shared by multiple people
* are these the same people or family members? does that matter?
* could we combine address into cities, counties, states for more predictive power?
* **combine into zipcodes, combine into states, compare**

delinq_2yrs: Number of 30+ days delinquency incidents in past 2 years.
* very right-skewed
* a few large outliers
* range is 0 - 29
* consider converting to categorical with a few levels (0, a few, many, etc.)

fico_range_low:	Lower end of FICO score range.
* right-skewed, multimodal
* probably multicollinear with fico_range_high
* consider combining with high as median?

fico_range_high: Upper end of FICO score range.
* right-skewed, multimodal
* probably multicollinear with fico_range_low
* consider combining with low as median?

inq_last_6mths:	Number of credit inquiries in the past 6 months.
* right-skewed
* range is 0 - 8
* consider converting to categorical with a few levels (0, a few, many, etc.)

mths_since_last_delinq:	Months since last delinquency (NA if never).
* right-skewed
* a few large outliers
* could be multicollinear with other delinquency variables
* 126517 missing values
* since NA if never, consider labeling as something different ("never", etc.)

last_credit_pull_d:	Most recent date credit was pulled.
* has a few blank/empty values as well that we need to deal with or label
* 137 levels
* could we combine levels into seasons & years or even just years?

acc_now_delinq:	Number of accounts currently delinquent.
* very right-skewed
* range is 0 - 6
* consider converting to categorical with a few levels (0 and 1+, 0 and 1 and 2+, etc.)

hardship_flag: Whether borrower is under hardship plan (Y/N).
* 1 level: No
* remove since constant and no predictive power

debt_settlement_flag:	Whether borrower is in a debt settlement program (Y/N).
* 2 levels: "N" - 98.69%, "Y" - 1.31%
* don't think any changes are needed

