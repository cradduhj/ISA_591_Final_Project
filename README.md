# ISA_591_Final_Project
This is a GitHub repository for our ISA 591 Final project.

# Part 2: Tree-Based Models
In this phase, you will use the clean, preprocessed loan default data to develop three tree-based models and evaluate their effectiveness on the dataset.  For this part of the project, use your preprocessed training data to develop three models, described below.

* Decision Trees: Using the pruning method we discussed in class, develop the best single decision tree model that you can.  You may experiment with different trees until you find the one that is the best in terms of prediction.  
* Random Forest: Using the methods we discussed in class, develop the best Random Forest tree that you can.  Tune hyperparameters to improve model performance. 
* XGBoost: Using the methods we discussed in class, develop the best XGBoost model that you can.  Tune hyperparameters to improve model performance.

## Adjusting Probability Threshold
You may need to adjust the probability threshold when necessary. In other words, using 50% as the default threshold of the models might NOT be optimal. Checking for other thresholds can be helpful. You are expected to check for a different optimal cutoff. Each of the models you fit may have a different threshold.

## Balancing the training sample
You should consider balancing the training sample by UNDERSAMPLING the majority class.  Do not oversample the minority class, or you will run into significant computational resource issues (i.e., your model-fitting algorithms will never converge).  Balancing the training sample can improve model performance, but it does not always do so.  Part of your investigation is to consider both unbalanced and balanced training samples, and decide which works best for your models.

## Selecting your Best Tree-Based Model
After training each model above, evaluate and compare them on the test set (remember, this data set is NOT oversampled) using a variety of metrics to understand their strengths and weaknesses. 

Common metrics include:

* Accuracy: The proportion of correct predictions out of the total number of predictions, giving a general sense of the model’s effectiveness.
* Precision: The number of true positive predictions divided by the sum of true positive and false positive predictions, indicating the accuracy of positive predictions.
* Recall: The number of true positive predictions divided by the sum of true positives and false negatives, showing the model’s ability to identify all relevant instances.
* F1 Score: The harmonic mean of precision and recall, providing a balanced measure when there is an uneven class distribution. This is the metric used to rank the final predictions in Part 5.
* ROC-AUC (Receiver Operating Characteristic - Area Under Curve): A measure of the model’s ability to discriminate between positive and negative classes across various thresholds, offering insight into performance beyond a single cutoff.

Comparison of Results: Comparing models trained on the original and test datasets allows students to assess the impact of class-imbalance handling techniques, hyperparameter values, and other aspects of the model.  You should reflect on each model’s performance to understand the trade-offs between complexity, interpretability, and accuracy. You must decide which is your BEST TREE-BASED Model.

## Part 2 Final Deliverable
* Three knitted RMarkdown files containing the development and evaluation of the best (1) single tree model, (2) random forest model, and (3) XGBoost Model. These files should be organized and fully documented with both inline documentation in code blocks and text annotation (not in code blocks) that explain and interpret the model-building process.  I do not need to see everything you tried, but I do need to see the final steps you used to create the best of each model type.  
* A fourth knitted Rmarkdown file that compares the performance of the three models and gives your rationale for the BEST TREE-BASED Model.  This file should contain a discussion of why you selected the model you chose as BEST.
* **Important Note:**  RMD files will not be accepted.  You have four files to turn in.  They should be named as follows: group#section_last1-last2_modeltype.html. I have been very forgiving of students who have turned in the wrong files (e.g., RMD rather than HTML) or have not turned in all of the files.  There will be no leniency on incorrect/incomplete file uploads for this or future assignments.  It is your and your partner's responsibility to double-check the files you uploaded.  

# Part 1: EDA

## Objective:
The goal of this phase is to explore the dataset, understand its structure, detect any patterns or anomalies, and clean the data to prepare it for model building. Proper EDA and data preprocessing are essential for enhancing the quality of the dataset and ensuring the models can learn effectively from the data. 

The main objective of this assignment is for you to learn. In keeping with this objective, here are a few tips:

* You will need to make several judgment calls when cleaning this data.  This is the normal part of the analytics process.  
* If you make a mistake or a bad call, you can always undo it...If you've written literate code.
* You may have to learn something about the loan process to fully complete this assignment. 
* If you choose to use an AI tool as an assistant, your guiding principle should be that you are a trained professional who will vet the code, verify the results, and guide the analysis. Ultimately, you are responsible for the integrity of your work. 

## Important Tips: 
* As you work with this data, be mindful that any operations you perform on the data must also be performed on the holdout and scoring data.  As you write your code, try to write it in a clear and well-documented way that can be easily adapted to perform the same operations on a new dataset with the same format.
* If you aren't sure whether you want to perform a specific operation (e.g. a variable transformation) because you are unsure it will improve the model, that is ok.  You can make notes that it might work, figure out the code to perform it, try it (or comment the code out), and decide later when you are in the modeling phases of the project.  I often have great ideas that don't work out it practice.  Trial and error are part of the modeling process.

## Important Steps You Might Want to Take
1. Data Overview and Summary Statistics:
* Gain an initial understanding of the dataset by summarizing key statistics (e.g., mean, median, standard deviation) for numerical variables 
* Generate frequency tables for categorical variables.

2. Data Visualization:
* Use visualization techniques such as histograms and box plots to understand the distribution of numeric variables.
* Visualize correlations between numerical variables using a heatmap or pair plots to identify relationships between features.
* Create bar charts or pie charts to examine the distribution of categorical variables and their potential association with loan status.

3. Handling Missing Data:
* Investigate missing values in the dataset and determine the appropriate strategy to address them (e.g., removing rows/columns, imputing missing values with the mean, median, or mode).
* Examine patterns of missingness to ensure they do not introduce bias.
* Include missing variable indicators if necessary

4. Outlier/Anomaly Detection:
* Identify outliers in numerical variables.
* Decide whether to handle outliers by removing them or adjusting the data (e.g., capping or transforming values).

5. Data Transformation:
* Consider applying transformations if necessary to reduce skewness in highly skewed variables. Note this doesn't always improve model performance, but can be helpful in some cases.

6. Dimension Reduction:
* If there are many highly correlated features, consider dimensionality reduction techniques such as Principal Component Analysis (PCA) to capture the most important information while reducing the number of features used by the model.  This is another case where PCA may help, but may not help in the predictive modeling process. 
* If you use PCA, see me for details on how to apply the same PCA model and weights to new data.
* Perform feature selection to remove redundant or irrelevant features that do not contribute to the prediction of loan default.
* For categorical variables with a large number of levels (unique values), reduce dimensionality by grouping similar categories together, encoding only the most frequent categories.
* Drop uninformative variables.

7. Encoding Categorical Variables:
* Because some models may require only numerical predictors, convert categorical variables into numerical formats using techniques such as dummy-encoding.
* Ensure that encoded variables maintain meaningful information for the predictive models.

8. Feature Creation:
* Interaction Features: You can create interaction terms between variables that may have a combined effect on loan default risk. For example, interactions between debt-to-income ratio and credit score or between loan amount and interest rate might have a significant effect on the response.
* Ratio Features: You can also generate ratios between key numerical variables. For example, the ratio of loan amount to annual income or loan amount to collateral value can be used to provide additional insights into an applicant’s ability to repay.
* Binned Variables: You can group continuous variables into bins or categories. For example, age could be binned into ranges (e.g., <25, 25-40, >40), and loan amounts could be categorized into small, medium, and large loans.
* Time-Based or Duration Variables: If time/date data is available, extract meaningful features.

## Deliverables
* An organized, knitted RMarkdown file with code and documentation on all steps taken.
* The RMarkdown must have a floating table of contents with numbered sections similar to your class notes and HW templates.
* Your R Markdown should include code in blocks, with in-line code documentation. 
* All annotation and explanation of the results of the code should NOT appear inside code blocks, but should be clearly formatted output, text and figures outside of the code blocks.
* I know how to read output; however, you should always annotate your output to explain the key insights to the reader.  This will make sure that I know that you know how to read output.
* Your final training data set saved as an RDS file. The filename should be group#section_last1-last2_train.rds (replace # with your group number, section with your section, last1 and last2 with the last names of the team members as given in your group name).  Example code is below. saveRDS(your_df_name, file = "group#section_last1-last2_train.rds")
