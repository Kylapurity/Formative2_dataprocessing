Customer Data Processing and Modeling: Lessons Learned
Project Overview
This project, conducted in Jupyter notebooks, spans four parts to process and analyze customer data: augmenting customer_transactions.csv, merging it with customer_social_profiles.csv using id_mapping.csv, validating data quality, and predicting behavior with a Random Forest model. Here’s what I learned from each step, reflecting on the process and insights gained.
What I Learned
Part 1: Data Augmentation
Task Overview: I worked with customer_transactions.csv (customer IDs, purchase amounts, dates, categories) to create an enriched dataset.
Lessons Learned:  
Cleaning Builds Trust: Filling missing data with averages or common values (e.g., 'Electronics') was straightforward, but KNN imputation taught me how to leverage data patterns for smarter fills.  

Synthetic Data Mimics Reality: Adding noise to purchases showed me how to reflect natural variations. Balancing with SMOTE helped me fix uneven categories, and generating 20% more transactions per customer taught me to predict behavior trends.  

Transformation Smooths Data: Log transformations on skewed purchases (e.g., big outliers) revealed how to normalize data for better analysis.  

Outcome: customer_transactions_augmented.csv became a larger, more diverse dataset.

Part 2: Merging Datasets
Task Overview: I merged the augmented data with social profiles, linking different IDs, and added features.
Lessons Learned:  
Merging Requires Strategy: Using id_mapping.csv to connect customer_id_legacy and customer_id_new showed me how to bridge datasets. Keeping all transactions in a left merge taught me to handle unmatched data gracefully.  

Features Add Insight: Crafting a customer_engagement_score from purchases and engagement scores helped me see how to combine metrics. I learned dates can get lost if not preserved, impacting time-based features like averages.  

Adaptability is Essential: Skipping TF-IDF when text wasn’t available taught me to work with what’s given.  

Outcome: final_customer_data_11.csv blended transaction and social data effectively.

Part 3: Data Consistency and Quality Checks
Task Overview: I ensured the merged data was clean and ready for modeling.
Lessons Learned:  
Quality Saves Time: Removing duplicates and checking categories (e.g., 'Clothing') showed me how errors creep in. About 10% unmatched profiles taught me real data has gaps.  

Stats Tell the Story: Summaries and plots of purchase amounts before/after augmentation helped me visualize my impact—augmented data spread out more.  

Feature Selection Focuses Effort: A correlation heatmap revealed overlapping features, and picking the top 10 with an algorithm taught me to prioritize.  

Outcome: final_dataset_ready_11.csv was a polished, ML-ready dataset.

Part 4: Predictive Modeling with Random Forest
Task Overview: I built a model to predict customer behavior, like purchase interest.
Lessons Learned:  
Targets Drive Models: Choosing purchase_interest_score as the goal showed me how critical the target is. Splitting data taught me fair testing.  

Random Forest Finds Patterns: It handled complex data well, and I learned to trust it to highlight key factors, like spending habits, via feature importance.  

Prep is Everything: Clean, selected features from earlier steps boosted performance—I learned skipping steps hurts results.  

Outcome: Predictions and insights tied the project together.

Setup Instructions
Get the Project: Download the folder with Jupyter notebooks and data files.

Directory Structure (based on your Jupyter environment):

project_folder/
├── customer_transactions.csv
├── customer_social_profiles.csv
├── id_mapping.csv
├── part1_augmentation.ipynb
├── part2_merging.ipynb
├── part3_quality_checks.ipynb
├── part4_random_forest.ipynb
├── combined_data_processing_databases_group_11.ipynb
├── data_processing_task1.ipynb
├── data_processing_task2.ipynb
├── data_processing_task3.ipynb
├── best_random_forest_model.pkl
├── final_dataset_ready_11.csv
├── README.md

Install Python 3.11 and Libraries:
Open a terminal and run:
bash

pip install -r requirements.txt

Create requirements.txt with the following (based on your environment):

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
jsonschema-specifications==2023.12.1
jupyter==1.1.1
jupyter_client==8.6.3
jupyter-console==6.6.3
jupyter_core==5.7.2
jupyter-events==0.10.0
jupyter-lsp==2.2.5
jupyter_server==2.14.2
jupyter_server_terminals==0.5.3
jupyterlab==4.2.5
jupyterlab_pygments==0.3.0
jupyterlab_server==2.27.3
jupyterlab_widgets==3.0.13
keras==3.6.0
kiwisolver==1.4.7
libclang==18.1.1
Markdown==3.7
markdown-it-py==3.0.0
MarkupSafe==3.0.1
matplotlib==3.9.2
matplotlib-inline==0.1.7
mdurl==0.1.2
mistune==3.0.2
ml-dtypes==0.4.1
nbclient==0.10.0
nbconvert==7.16.4
nbformat==5.10.4
nest-asyncio==1.6.0
notebook==7.2.2
notebook_shim==0.2.4
numexpr==2.10.1
numpy==2.1.2
opt-einsum==3.4.0
overrides==7.7.0
packaging==24.1
pandas==2.2.3
pandocfilters==1.5.1
parso==0.8.4
pexpect==4.9.0
pillow==11.0.0
platformdirs==4.3.6
prometheus-client==0.21.0
prompt_toolkit==3.0.48
protobuf==5.28.2
psutil==6.0.0
ptyprocess==0.7.0
pure-eval==0.2.3
pyarrow==17.0.0
pycparser==2.22
Pygments==2.18.0
pyparsing==3.1.4
python-dateutil==2.9.0.post0
python-json-logger==2.0.7
pytz==2024.2
PyYAML==6.0.2
pyzmq==26.2.0
referencing==0.35.1
requests==2.32.3
rfc3339-validator==0.1.4
rfc3986-validator==0.1.1
rich==13.9.3
rpds-py==0.20.0
Send2Trash==1.8.3
six==1.16.0
sniffio==1.3.1
soupsieve==2.6
stack-data==0.6.3
tensorboard==2.18.0
tensorboard-data-server==0.7.2
tensorflow==2.18.0
tensorflow-intel==2.18.0
termcolor==2.5.0
terminado==0.18.1
threadpoolctl==3.5.0
tinycss2==1.4.0
tornado==6.4.2
traitlets==5.14.3
types-python-dateutil==2.9.0.20241206
typing_extensions==4.12.2
tzdata==2025.1
uri-template==1.3.0
urllib3==2.3.0
uvicorn==0.34.0
wcwidth==0.2.13
webcolors==24.11.1
webencodings==0.5.1
websocket-client==1.8.0
Werkzeug==3.1.3
wheel==0.45.1
widgetsnbextension==4.0.13
wrapt==1.17.2

Launch Jupyter:
In the terminal, navigate to the project folder and run:
bash

jupyter notebook

Open the .ipynb files in your browser.
