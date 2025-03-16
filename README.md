# Customer Data Processing and Modeling: Lessons Learned

## Project Overview
This project, conducted in Jupyter notebooks, spans four parts to process and analyze customer data: augmenting `customer_transactions.csv`, merging it with `customer_social_profiles.csv` using `id_mapping.csv`, validating data quality, and predicting behavior with a Random Forest model. Here’s what we reflected on the process and insights gained.

## What We Learned
### Part 1: Data Augmentation
**Task Overview:** I worked with `customer_transactions.csv` (customer IDs, purchase amounts, dates, categories) to create an enriched dataset.

**Lessons Learned:**  
- **Cleaning Builds Trust:** Filling missing data with averages or common values (customer ratings) was straightforward, but KNN imputation taught me how to leverage data patterns for smarter fills.  
- **Synthetic Data Mimics Reality:** Adding noise to purchases showed me how to reflect natural variations. Balancing with SMOTE helped me fix uneven categories, and generating 20% more transactions per customer taught me to predict behavior trends.  Where the shape increaded from 175 to 210

**Outcome:** `customer_transactions_augmented.csv` became a larger, more diverse dataset.

### Part 2: Merging Datasets
**Task Overview:** I merged the augmented data with social profiles, linking different IDs, and added features.

**Lessons Learned:**  
- **Merging Requires Strategy:** Using `id_mapping.csv` to connect `customer_id_legacy` and `customer_id_new` showed me how to bridge datasets. Keeping all transactions in a left merge taught me to handle unmatched data gracefully.  
- **Features Add Insight:** Crafting a `customer_engagement_score` from purchases and engagement scores helped me see how to combine metrics. I learned dates can get lost if not preserved, impacting time-based features like averages.  
- **Adaptability is Essential:** Skipping TF-IDF when text wasn’t available taught me to work with what’s given.  

**Outcome:** `final_customer_data_11.csv` blended transaction and social data effectively.

### Part 3: Data Consistency and Quality Checks
**Task Overview:** I ensured the data was clean and where used the duplicate and describe to check for  duplicate() values and how the data is using describe()

**Lessons Learned:**  
- **Quality Saves Time:** Removing duplicates and checking categories (e.g., 'Clothing') showed me how errors creep in. About 10% of the unmatched profiles taught me real data has gaps.  
- **Stats Tell the Story:** Summaries and plots of purchase amounts before/after augmentation helped me visualize my impact—augmented data spread out more.  
- **Feature Selection Focuses Effort:** A correlation heatmap revealed overlapping features, and picking the top 10 with an algorithm taught me to prioritize.  

**Outcome:** `final_dataset_ready_11.csv` was a polished, ML-ready dataset.

### Part 4: Predictive Modeling with Random Forest
**Task Overview:** I built a model to predict customer behavior, using the correctional heatmap results.
- ** We used random forest since it had the best RM2 of 0.86 than Linear regression.
-![image](https://github.com/user-attachments/assets/64d216c6-f702-45b0-8f70-f2e5f31ceaec)

 ### Part 4: The video presentation and document of outcomes
- ** Video: https://youtu.be/jX0IirA7tP8
- ** Document: https://docs.google.com/document/d/14tJpAruAJL5T5cP0JkCf1hbZ0GxfchU1abo3H0zKWjA/edit?usp=sharing 
- ** We have also attached the pdf report  at: https://github.com/Kylapurity/Formative2_dataprocessing/tree/main/report_document
  
## Setup Instructions to run the project
### Get the Project
Download the folder with Jupyter notebooks and data files.

### Directory Structure (based on your Jupyter environment):
```plaintext
project_folder/
├── combined_data_processing_and_training_databases_peer_group_11.ipynb
├── data_processing_task1.ipynb
├── data_processing_task2.ipynb
├── data_processing_task3.ipynb
├── requirements.txt
├── initial_datasets/
│   ├── customer_social_profiles.csv
│   ├── customer_transactions.csv
│   ├── id_mapping.csv
├── derived_datasets/
│   ├── customer_transactions_augmented.csv
│   ├── final_customer_data_11.csv
│   ├── final_dataset_ready_11.csv
├── model/
│   ├── model_dataset.ipynb
├── report_document/
│   ├── FORMATIVE 2_ GROUP 11 PROJECT SUMMARY REPORT.pdf
├── saved_model/
│   ├── best_random_forest_model.pk
```

### Install Python 3.11 and Libraries:
Open a terminal and run:
```bash
pip install -r requirements.txt
```

### Create `requirements.txt` with the following (based on your environment):
```plaintext
absl-py==2.1.0
anyio==4.6.0
argon2-cffi==23.1.0
argon2-cffi-bindings==21.2.0
arrow==1.3.0
asttokens==2.4.1
astunparse==1.6.3
async-lru==2.0.4
attrs==24.2.0
Babel==2.16.0
beautifulsoup4==4.12.3
bleach==6.1.0
blinker==1.8.2
Brotli==1.1.0
certifi==2024.8.30
cffi==1.17.1
charset-normalizer==3.3.2
click==8.1.7
comm==0.2.2
contourpy==1.3.0
cycler==0.12.1
debugpy==1.8.6
decorator==5.1.1
defusedxml==0.7.1
exceptiongroup==1.2.2
executing==2.0.1
fastjsonschema==2.20.0
flatbuffers==24.3.25
fonttools==4.54.1
fqdn==1.5.1
gast==0.6.0
google-pasta==0.2.0
grpcio==1.66.2
h11==0.14.0
h5py==3.12.1
httpcore==1.0.6
httpx==0.27.2
idna==3.10
importlib_metadata==8.5.0
importlib_resources==6.4.5
ipykernel==6.29.5
ipython==8.28.0
ipywidgets==8.1.5
isoduration==20.11.0
jedi==0.19.1
Jinja2==3.1.4
json5==0.9.25
jsonpointer==3.0.0
jsonschema==4.23.0
jupyter==1.1.1
jupyter_client==8.6.3
jupyter-console==6.6.3
jupyter_core==5.7.2
matplotlib==3.9.2
numpy==2.1.2
pandas==2.2.3
scikit-learn==1.5.0
seaborn==0.13.2
tensorflow==2.18.0
torch==2.1.0
```

### Launch Jupyter Notebook
In the terminal, navigate to the project folder and run:
```bash
jupyter notebook
```
