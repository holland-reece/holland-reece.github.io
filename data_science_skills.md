---
title: Holland Reece Brown
layout: default
---


# Data Science Portfolio

[Big Data Analytics](#big-data-analytics)

[Statistics and Machine Learning Methods](#statistics-and-machine-learning-methods)


## Big Data Analytics

- Working with big data can involve cross-referencing many sources to get an accurate picture of the dataset as a whole. Here is a truncated example of a Python class I wrote to organize and clean data from the Swedish population registry, InternetPsykiatri mental health records (XML format), and internal study spreadsheets (XLSX format) at Karolinska Institutet in Sweden. [TreVar study GitHub repo](https://github.com/holland-reece/TreVar/tree/main)
```python
class clean_clin_data:

    def __init__(self, participant_info_xlsx: str, raw_data_xml: str, output_directory: str, output_xml: str):
        self.rawxml = raw_data_xml
        self.outdir = output_directory
        self.outxml = output_xml

        # Read study IDs, names and Swedish personal numbers from XLSX into pandas dataframe
        self.pptinfo_path = participant_info_xlsx
        self.pptinfo = pd.read_excel(participant_info_xlsx, index_col=0)

    def deidentify(self):
        for study_id in (self.pptinfo.index):
            identifiers = clean_clin_data.deID_read_ppt_info(self, study_id) # Read participant's identifiers from spreadsheet
            clean_clin_data.deID_replace_identifiers(self, identifiers) # Replace identifers with studyID

        # Overwrite Excel spreadsheet tracking study participants' records located with new pandas dataframe
        self.pptinfo.to_excel(self.pptinfo_path, sheet_name='sheet1', index=True)
```

- As new data is collected, it is crucial to keep data organized and standardized in real time. Here is a snippet of SQL code I wrote to automate data organization (if a new row is added in one table, a corresponding table is automatically updated).
````SQL
DELIMITER $$
CREATE TRIGGER patient_insert # name trigger
	AFTER INSERT ON patient_record # trigger event (if this happens, run the Event)
	FOR EACH ROW
BEGIN # This executes if above triggering event happens
	INSERT INTO patient_demographics(patient_id, first_name, last_name)
    VALUES(NEW.patient_id, NEW.first_name, NEW.last_name); # use NEW or OLD to only refer to new inserted data or only old data
END $$
DELIMITER ;
````

- One of the first things I do when I clean and preprocess a raw dataset is check for duplicate data. Here is an example of how I might check for duplicate rows in a raw data table in SQL.
````SQL
# Create CTE containing query above and filter for row_num > 1
WITH duplicate_cte AS
(
SELECT *,
ROW_NUMBER() OVER(
PARTITION BY company, location,
industry, total_laid_off, percentage_laid_off, `date`
) AS row_num # use backticks for date bc it is a SQL keyword
FROM layoffs_staging # use the 'staging' version of the table
)
SELECT *
FROM duplicate_cte
WHERE row_num > 1; # if row number is > 1, there may be duplicates
````


## Statistics and Machine Learning Methods
- Statistical models for behavioral experiments can get complex, so it's crucial to work with team members and pool domain knowledge to build models correctly. Here is sample of a *mixed effect linear model for repeated measures* I built (in R) for a study of sickness behavior, collaborating with psychoneuroimmunologists at Stockholm University.
```R
# Step 1: Fit Mixed-Effects Model (use from prev code block)
#df1 <- merged_exteWQ2 # exteroception questions
df1 <- merged_interBQ2 # interoception questions

df_lps <- data.frame(dplyr::filter(df1, df1$session_cond == "lps")) # extract one session from df with one question
df_lpsmorning <- data.frame(dplyr::filter(df1, df1$session_cond == "lpsmorning")) # extract one session from df with one question
df_pl <- data.frame(dplyr::filter(df1, df1$session_cond == "pl")) # extract one session from df with one question
df_plmorning <- data.frame(dplyr::filter(df1, df1$session_cond == "plmorning")) # extract one session from df with one question

# Fit the model
df <- df_plmorning # run one session at a time
model <- lmer(resp ~ block + (1 | subjid), data = df)

# Summary stats of the model
summary(model)
fixef(model) # Full table of fixed effects
coef(summary(model)) # Full table of coefficients
anova(model) # Full table from ANOVA test

# Step 2: Generate Predictions ---------------------------------------------------
# Create a new data frame for predictions over trials and conditions
pred_data <- expand.grid(
  block = 1:10,
  session_cond = unique(df$session_cond)
)

# Add predictions from the model
pred_data$pred <- predict(model, newdata = pred_data, re.form = NA)  # re.form = NA excludes random effects
```

- Deep learning algorithms elucidate patterns we can't see on our own, but sometimes a simple regression accomplishes analysis goals best. In a machine learning course, I built and trained *lasso and ridge regression models using k-fold cross validation and forward feature selection* on a publicly available dataset (in Python, Jupyter notebook). I used area under the ROC curve and confusion matrices to choose optimal parameters and understand the performance of each model.
```python
# Use ROC curve to test best threshold for lambda
fpr, tpr, thresholds = metrics.roc_curve(y_test, pred, pos_label=1)
print(f"False Positive Rates (Specificity): {fpr}\nTrue Positive Rates (Sensitivity): {tpr}\nThresholds: {thresholds}\n")
print(f"Area Under ROC Curve: {roc_auc_score(y_test, prob[:,1], multi_class='ovr')}\n")

# Based on the area under the ROC curve in this example, the optimal value for lambda=1 
```

- For those times when deep learning is the best approach to understanding underlying patterns and finding new embeddings, here is a snippet of code from a *neural network I trained on a repository of medical images* (in Python using Google Colab and AWS).
```python
model.summary()

# Define loss function
loss_fn = tf.keras.losses.CategoricalCrossentropy(
    from_logits=True, name='categorical_crossentropy')

# Define optimizer,loss function and evaluation metric
optimizer = tf.keras.optimizers.Adam(lr = 0.1) # using Adam as optimizer here

model.compile(optimizer=optimizer,
             loss=loss_fn,
             metrics=['accuracy'])

# Train the model
model.fit(x_train_small, y_train_small_onehot,epochs=5)

# Evaluate model performance
y_test_onehot = to_categorical(y_test)
model.evaluate(x_test,y_test_onehot,verbose=2)
```

