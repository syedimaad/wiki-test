**[What is auto ML?]{.underline}**

Auto ML is automated machine learning. Auto ML is a ready to use
mechanism which provides methods and processes that can be easily used
by non ML experts to make their models train easily without having to
deal with the classic machine learning algorithm processes like
preprocessing the data, cleaning the data, constructing appropriate
features, selecting an appropriate model, optimize hyperparameters of
the model, etc.

The computational complexity of these tasks is beyond the scope of
non-ML experts so here AutoML comes into the picture with its off-the
shelf machine learning models that can be used easily without the
\"expert\" knowledge.

**[AutoML systems:]{.underline}**

Some autoML systems developed recently are AutoWeka, AutoSkLearn,
AutoPytorch, etc.

Apart from these I have also read about AutoML for Google cloud, along
with the various steps it follows- create a model, deploy a model,
display a model evaluation, etc.

[Steps involved in detail:]{.underline}

1.  Before creating a model first we need to create a dataset and import
    in order to be able to train the model. So to create a dataset (more
    like upload the dataset) first we visit the auto ML tables page in
    the google cloud console and then we select the dataset.

2.  We have to mention the name of the dataset and also specify the
    region where the dataset will be used. Then our dataset will be
    created. After that we will have to import the dataset.

3.  To import the dataset we go to the import tab and specify the source
    of the data- bigQuery, cloud storage or our local computer system.
    (If we are loading CSV files from our local computer system then we
    must also provide with a cloud storage. The files are first loaded
    to that cloud storage before being imported to the autoML tables).

4.  Next step is to train the model. Once the import is done then we
    move on to the train the model tab. We go to the Train tab and
    select the dataset to be trained. Then we select the target column
    for our model. This is the value that the model is trained to
    predict. Whether it is a regression model or classification model
    depends on the datatype of the target column.

5.  Review the datatype,nullability and data stats for each column in
    the dataset.

6.  There is a \"Edit Additional Parameters\" section which provides
    options to control the split of the dataset or if we want to weigh
    the training examples by the values in a column. We then do a quick
    final review of the dataset.

7.  Once the dataset is up to mark and to our satisfaction we click on
    \"train the model\".

8.  After that there are some specifics asked like Training budget which
    specifies a number to denote the number of node hours to spend
    training the model, Input feature selection in which by default all
    the columns are selected but we can modify that in theAdvanced
    option and select the metrics of our own. Then we click on Train the
    model, to begin the training process.

[Model Architecture:]{.underline}

We may use cloud logging to view details about the autoML tables model.
Using the cloud logging we can view the final hyperparameters of the
model and also the various other hyperparameters and the objects used
during the training of the model and its tuning.

Note: A basic prior knowledge of cloud logging is required before use.

- In the autoML tables page tab under the model section we can view
  final hyperparameters log by clicking Model and to view the tuning
  trial hyperparameters we click on the Trial tab.

- Reading model architecture logs- Activity logs are structured as
  described in the LogEntry type documentation.

- Payload Contents- The contents of a log entry are provided in JSON
  format.

- List of Hyperparameters- The data provided for each type of log differ
  for each model. Following are some models that are present:

  - AdaNet Models

  - AdaNet Auto Ensemble Model

  - DNN Linear Model

  - Gradient Boosted Decision Tree Model

  - FeedForward Neural Network model

- We can view our project activity log in the logs explorer in the GCC.

- We can export our logs to BigQuery, Cloud, Pub/ Sub.

**[Evaluating Models-]{.underline}**

Once the training is done, the \'test dataset\' feature is used to
evaluate the quality and accuracy of the newly gained model, thereafter
providing us with an aggregate set of evaluation metrics which tells us
how well the model did on the dataset.

If we have included weights in our training data, it does not affect the
evaluation metrics.

[Evaluation Metrics for Classification models-]{.underline}

AUC PR, AUR ROC, Accuracy, Log loss, F1 score, Precision, recall, false
positive rate, confusion matrix, feature importance.

[Evaluation Metrics for Regression models-]{.underline}

MAE, RMSE, RMSLE, r\^2, MAPE, feature importance.

**[Batch Predictions-]{.underline}**

After training a model, we can make an asynchronous request for a batch
of predictions using the \'batchPredict\' method. We simply need to
provide the input data to the batchPredict method in a table format.
Then each row would provide us with values for the features we trained
the model.

- For batch predictions we specify a data source and the result
  destination in a BigQuery table or in a CSV file in cloud storage.

- The data source must contain tabular data including all the columns
  used to train the model.

- Using CSV files in cloud storage:

  - columns order may differ from the data used while training.

  - max size is10gb.

  - multiple files upto 100gb can be included.

The result can be found in the Recent Prediction tab at the bottom of
Batch Prediction page of the Test and Use tab of the model in use.

**[Implementing AutoMl GCP on a toy dataset:]{.underline}**

**[USING AUTOML VISION:]{.underline}**

The dataset used here is the income census dataset. containing
information about people from a 1994 Census database, including age,
education, marital status, occupation, and whether they make more than
\$50,000 a year. The dataset consists of over 30k rows, where each row
corresponds to a different person. For a given row, there are 14
features that the model conditions on to predict the income of the
person

To implement autoML GCP on a toy dataset following steps were added:

First we need to set up the local environment. We need to make sure that
we have the following requirements ready:

- The google cloud sdk

- python3

- virtual env

- Jupyter notebook in venv

The steps to intsall the above are-

- Install and initialize Cloud SDK

- Install Python3

- Install virtual env

- Install jupyter in virtual env

- Run Jupyter notebook in shell

- Open notebook in the dashboard

The next step is to set up the GCP project:

- Select or create a GCP project (selected ads-poc-12358 here)

- Enable billing for your project

- Enable AI Platform and compute engine APIs

- lastly enable AUTOML API

Install packages and dependencies that are not already installed in the
notebook.

Setting up the GCP project id:

- Enter the project id for the project that you have selected or
  created.

- Also enter the compute region (\'us-central1\' is the only and by
  default value)

Authenticate the GCP Account:

This is an important step,

- In the GCP console, under the Create Service account key page, select
  a project.

- Next to the project click on the three dots

- Click on manage keys

- Select the key and download it (this is for working with already
  generated keys)

- For generating a new key click on generate new key and click on
  download JSON file (this will only happen if you have the permission
  to do so)

- In the service account, from Role drop down list, select Storage\>
  Storage Object Admin

Then enter the path of the service account JSON key in the
GOOGLE_APPLICATION_CREDENTIALS variable.

The next step is to create a cloud storage bucket.

- BUCKET_NAME= \"YOUR BUCKET NAME\", this name should be unique for all
  the names in thecloud storage bucket.

- Then validate access to the cloud storage bucket by examining the
  contents of the bucket.

Import various libraries and dependencies required like autoML, the
autoML library needs to be downloaded accordind to its latest version,
so be sure to give it a search as to what the latest command is.

Initialize the constants like dataset display name, name of the input
csv file and the model display name.

Initialize the autoML client(again use the latest version and format
being used)

To import the training data first we have to create the dataset on the
GCP using create_dataset(), which has one parameter already declared as
the dataset display name.

Next we import the data to our AutoML tables from the GCS.

Then we begin training the model. We mention the number of hours for
which we would train the model( note that it may take extra time as
well).

We have various Training models for each time we run the model training.
We can get a list of models and see which is required or not.

Then deploy the model and get online predictions and batch predictions
using the batch_predict.

The results are stored in a csv file in the GCP, which can be downloaded
for our use and analysis.

**[IMPLEMENTATION OF TOY DATASET USING VERTEX AI:]{.underline}**

\

The toy dataset used is a bank marketing dataset.

There are a number of Vertex AI jupyter notebook tutorials already
defined.

  ----------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------
  Feature Used            Type                                                                                                                                                                                                                                    Description
  AutoML                  [[Text classification model]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/automl/automl-text-classification.ipynb)                                                                Create, train and deploy a text classification model on Vertex AI.
  AutoML                  [[Time-series forecasting model]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/automl/sdk_automl_tabular_forecasting_batch.ipynb)                                                  Create, train, and use an AutoML time-series forecasting model for batch prediction.
  Custom training         [[Batch prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/custom/sdk-custom-image-classification-batch.ipynb)                                                              Use the Vertex AI SDK for Python to train and deploy a custom image classification model for batch prediction.
  Custom training         [[Online prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/custom/sdk-custom-image-classification-online.ipynb)                                                            Use the Vertex AI SDK for Python to train and deploy a custom image classification model for online prediction.
  Vertex Explainable AI   [[Tabular binary classification for batch prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/explainable_ai/sdk_automl_tabular_binary_classification_batch_explain.ipynb)   Use the Vertex AI SDK to create tabular binary classification models and perform batch prediction with explanation using a AutoML model.
  Vertex Explainable AI   [[Tabular binary classification for online prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/explainable_ai/sdk_automl_tabular_classification_online_explain.ipynb)        Use the Vertex AI SDK to create tabular classification models and do online prediction with explanation using a AutoML model.
  ----------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------

  ------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------
  Vertex Explainable AI     [[Custom training image classification model for batch prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/explainable_ai/sdk_custom_image_classification_batch_explain.ipynb)                                          Use the Vertex AI SDK to train and deploy a custom image classification model for batch prediction with explanation.
  Vertex Explainable AI     [[Custom training image classification model for online prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/explainable_ai/sdk_custom_image_classification_online_explain.ipynb)                                        Use the Vertex AI SDK to train and deploy a custom image classification model for online prediction with explanation.
  Vertex Explainable AI     [[Training tabular regression models for batch prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/explainable_ai/sdk_custom_tabular_regression_batch_explain.ipynb)                                                    Use the Vertex AI SDK to train and deploy a custom tabular regression model for batch prediction with explanation.
  Vertex Explainable AI     [[Custom training tabular regression model for online prediction]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/explainable_ai/sdk_custom_tabular_regression_online_explain.ipynb)                                            Use the Vertex AI SDK to train and deploy a custom tabular regression model for online prediction with explanation.
  Vertex AI Feature Store   [[Manage sample ML features using Vertex AI Feature Store]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/feature_store/gapic-feature-store.ipynb)                                                                             Store, serve, manage, and share machine learning features at a large scale.
  Model Monitoring          [[Use Model Monitoring to detect drift and training-prediction skew]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/model_monitoring/model_monitoring.ipynb)                                                                   Interpret statistics, visualizations, and other data reported by Model Monitoring.
  Vertex ML Metadata        [[Custom training job parameter and metric tracking]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/ml_metadata/sdk-metric-parameter-tracking-for-custom-jobs.ipynb)                                                           Track metrics and parameters for Vertex AI custom training jobs, and perform detailed analysis.
  Vertex ML Metadata        [[Locally trained model parameter and metric tracking]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/ml_metadata/sdk-metric-parameter-tracking-for-locally-trained-models.ipynb)                                              Track metrics and parameters for ML training jobs and analyze this metadata using Vertex AI SDK.
  Vertex AI Pipelines       [[Create a pipeline with lightweight components based on Python functions]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/lightweight_functions_component_io_kfp.ipynb)                                              Use the Kubeflow Pipelines (KFP) SDK to build Vertex AI Pipelines.
  Vertex AI Pipelines       [[AutoML image classification model workflow]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/google_cloud_pipeline_components_automl_images.ipynb)                                                                   Build an AutoML image classification workflow on Vertex AI Pipelines.
  Vertex AI Pipelines       [[AutoML tabular classification model workflow]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/automl_tabular_classification_beans.ipynb)                                                                            Build an AutoML tabular classification workflow on Vertex AI Pipelines.
  Vertex AI Pipelines       [[AutoML tabular regression model workflow]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/google_cloud_pipeline_components_automl_tabular.ipynb)                                                                    Build an AutoML tabular regression workflow on Vertex AI Pipelines.
  Vertex AI Pipelines       [[AutoML text classification model workflow]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/google_cloud_pipeline_components_automl_text.ipynb)                                                                      Build an AutoML text classification workflow on Vertex AI Pipelines.
  Vertex AI Pipelines       [[Custom training with pre-built Google Cloud Pipeline Components]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/custom_model_training_and_batch_prediction.ipynb)                                                  Use Vertex AI Pipelines with pre-built Google Cloud Pipeline Components for custom training.
  Vertex AI Pipelines       [[Custom training workflow with pre-built Google Cloud Pipeline Components and custom components]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/google_cloud_pipeline_components_model_train_upload_deploy.ipynb)   Use custom components to build a Vertex AI Pipelines workflow.
  Vertex AI Pipelines       [[Pipelines with control structures]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/control_flow_kfp.ipynb)                                                                                                          Use the Kubeflow Pipelines (KFP) SDK to build Vertex AI Pipelines that use control structures.
  Vertex AI Pipelines       [[Model metrics]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/metrics_viz_run_compare_kfp.ipynb)                                                                                                                   Build Vertex AI Pipelines that generate model metrics and visualizations, and compare pipeline runs.
  Vertex AI Pipelines       [[Vertex AI Pipelines and the Kubeflow Pipelines SDK]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/pipelines/pipelines_intro_kfp.ipynb)                                                                                      Use Vertex AI Pipelines with the Kubeflow Pipelines (KFP) SDK.
  Vertex AI Vizier          [[Multi-objective optimization]{.underline}](https://github.com/GoogleCloudPlatform/vertex-ai-samples/blob/main/notebooks/official/vizier/gapic-vizier-multi-objective-optimization.ipynb)                                                                                         Optimize multiple objective functions simultaneously.
  ------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------

\
I have used the Vertex AI- Tabular Binary Classification for batch
prediction.

The first step is to enable the vertex ai in the GCS and also enable
compute engine APIs and cloud storage. Enable billing for the project.

- Enter the project id and region (us-central1).

- Authenticate the GCP account by goind to the service account page and
  generating a new key in json format (or use an already generated key).

- Enter the path to your service account key as the
  GOOGLE_APPLICATION_CREDENTIALS variable

- Next step is to create a bucket and store the dataset in that bucket.

  - BUCKET_NAME="gs:// \[YOUR BUCKET NAME\]"

- Import aiplatform libraries and other dependencies needed.

- Initialize vertex sdk : aip**.**init(project**=**PROJECT_ID,
  staging_bucket**=**BUCKET_NAME)

- Declare a IMPORT_FILE variable to set the path for the csv dataset in
  the cloud storage bucket.

- Taking a quick peek at the data involves printing the first 10 rows of
  the dataset.

- Set the label to the variable on which training is to be done:
  label_column=\'gender\'.

- create the Dataset resource using the create method for the Tabular
  Dataset class, which takes the following parameters:

  - display_name: The human readable name for the Dataset resource.

  - gcs_source: A list of one or more dataset index files to import the
    data items into the Dataset resource.

  - bq_source: Alternatively, import data items from a BigQuery table
    into the Dataset resource.

- Creating a dataset may take a few minutes to execute.

- To train an autoML model we:

1.  Create the training pipeline

2.  Run the pipeline.

- An AutoML training pipeline is created with
  the AutoMLTabularTrainingJob class, with the following parameters:

  - display_name: The human readable name for the TrainingJob resource.

  - optimization_prediction_type: The type task to train the model for.

  - classification: A tabuar classification model.

  - regression: A tabular regression model.

- column_transformations: (Optional): Transformations to apply to the
  input columns

- optimization_objective: The optimization objective to minimize or
  maximize.

  - binary classification:

    - minimize-log-loss

    - maximize-au-roc

    - maximize-au-prc

    - maximize-precision-at-recall

    - maximize-recall-at-precision

  - multi-class classification:

    - minimize-log-loss

  - regression:

    - minimize-rmse

    - minimize-mae

    - minimize-rmsle

The instantiated object is a directed acyclic graph for the training
pipeline.

- Next we run the training pipeline:

  - dataset: The Dataset resource to train the model.

  - model_display_name: The human readable name for the trained model.

  - training_fraction_split: The percentage of the dataset to use for
    training.

  - test_fraction_split: The percentage of the dataset to use for test
    (holdout data).

  - validation_fraction_split: The percentage of the dataset to use for
    validation.

  - target_column: The name of the column to train as the label.

  - budget_milli_node_hours: (optional) Maximum training time specified
    in unit of millihours (1000 = hour).

  - disable_early_stopping: If True, training maybe completed before
    using the entire budget if the service believes it cannot further
    improve on the model objective measurements.

- After your model has finished training, you can review the evaluation
  scores for it.

- First, we need to get a reference to the new model. As with datasets,
  we can either use the reference to the model variable we created when
  deployed the model or we can list all of the models in our project.

- Make the batch predictions.

- Make the batch prediction explanation requests:

  - job_display_name: The human readable name for the batch prediction
    job.

  - gcs_source: A list of one or more batch request input files.

  - gcs_destination_prefix: The Cloud Storage location for storing the
    batch prediction resuls.

  - instances_format: The format for the input instances, either \'csv\'
    or \'jsonl\'. Defaults to \'jsonl\'.

  - predictions_format: The format for the output predictions, either
    \'csv\' or \'jsonl\'. Defaults to \'jsonl\'.

  - generate_explanations: Set to True to generate explanations.

  - sync: If set to True, the call will block while waiting for the
    asynchronous batch job to complete.

- The explanations are provided in a csv+header format which is stored
  in the bucket.

- All the training models, the batch predictions and their explanations
  are stored in the bucket.

**How the Data is Created?**

Import various libraries to be used followed by importing the google
cloud notebook. Configure and set the project as dh-ads-sandbox. Then
set the project id and location. Initialize the bucket. Import google
cloud aiplatform and initialise project id and link it to the bucket. To
check the contents of the bucket we can perform an ls cmd on the the
bucket.

Here the dataset is of 8gb and contains 4.5M data. The entire dataset is
divided into 200 smaller csv files containing approx 20K rows and 1591
columns.

**Data Preprocessing:**

The dataset I got was mostly preprocessed, just had some missing values,
these were handled directly at the source location of the dataset and
then uploaded to the bucket.

**Optimisation Function:**

  --------------------- -------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------
  AUC ROC               `maximize-au-roc`                Maximize the area under the receiver operating characteristic (ROC) curve. Distinguishes between classes. Default value for binary classification.
  Log loss              `minimize-log-loss`              Keep prediction probabilities as accurate as possible. Only supported objective for multi-class classification.
  AUC PR                `maximize-au-prc`                Maximize the area under the precision-recall curve. Optimizes results for predictions for the less common class.
  Precision at Recall   `maximize-precision-at-recall`   Optimize precision at a specific recall value.
  Recall at Precision   `maximize-recall-at-precision`   Optimize recall at a specific precision value.
  --------------------- -------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------

**Iterations:**

**[Demo1:]{.underline}** [Used 1M data- Training time 1 hr- 690
features]{.underline}

The 690 features were selected from the XGBoost model. The important
features from xgboost were listed along with their importances. The same
690 features were declared in a list in this iteration and the 1M
dataset(50 csv files) was selected for training for these 690 features.
Training time assigned was 1 hours.

[Why did we take only 690 features?]{.underline}

There is limitation of google cloud that it can not train a model on
more than 1000 features. Our original dataset consisted of 1591 columns
which is way more than the capacity of cloud training, so as starters we
defined features that were already used and declared important in the
xgboost model.

Here I have represented the features as numeric type.

[Evaluation Metrics:]{.underline}

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/50397214970740736/versions/default/evaluate?backTo=training&project=dh-gcp-ads-sandbox>

[Model Details:]{.underline}

[https://console.cloud.google.com/logs/query;query=resource.type%3D\"cloudml_job\"
resource.labels.job_id%3D\"50397214970740736\"
resource.labels.project_id%3D\"dh-gcp-ads-sandbox\"
labels.log_type%3D\"automl_tables\"
jsonPayload.\"@type\"%3D\"type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure\";timeRange=2022-06-30T11:24:59.768Z%2F2022-06-30T21:05:50.325805Z;cursorTimestamp=2022-06-30T12:24:59.572173Z?project=dh-gcp-ads-sandbox](https://console.cloud.google.com/logs/query;query=resource.type%3D%22cloudml_job%22%20resource.labels.job_id%3D%2250397214970740736%22%20resource.labels.project_id%3D%22dh-gcp-ads-sandbox%22%20labels.log_type%3D%22automl_tables%22%20jsonPayload.%22@type%22%3D%22type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure%22;timeRange=2022-06-30T11:24:59.768Z%2F2022-06-30T21:05:50.325805Z;cursorTimestamp=2022-06-30T12:24:59.572173Z?project=dh-gcp-ads-sandbox)

**[Demo2:]{.underline}** [Used 2.5M data- Training time 2 hr- 690
features]{.underline}

For the second iteration to check the working of the model the size of
dataset was increased to 2.5M(125 csv files), feature list was same as
previous iteration, however here we increased the training time to 2
hours. The model did not show any considerable changes in the results
when compared with the previous iteration. There was an approximate
reduction of f1 score by 0.1. The features are represented as numeric
type.

[Evaluation Metrics:]{.underline}

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/4215100970381606912/versions/default/evaluate?backTo=training&project=dh-gcp-ads-sandbox>

[Model Details:]{.underline}

[https://console.cloud.google.com/logs/query;query=resource.type%3D\"cloudml_job\"
resource.labels.job_id%3D\"4215100970381606912\"
resource.labels.project_id%3D\"dh-gcp-ads-sandbox\"
labels.log_type%3D\"automl_tables\"
jsonPayload.\"@type\"%3D\"type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure\";timeRange=2022-07-01T07:33:36.688Z%2F2022-07-01T20:07:29.308921Z?project=dh-gcp-ads-sandbox](https://console.cloud.google.com/logs/query;query=resource.type%3D%22cloudml_job%22%20resource.labels.job_id%3D%224215100970381606912%22%20resource.labels.project_id%3D%22dh-gcp-ads-sandbox%22%20labels.log_type%3D%22automl_tables%22%20jsonPayload.%22@type%22%3D%22type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure%22;timeRange=2022-07-01T07:33:36.688Z%2F2022-07-01T20:07:29.308921Z?project=dh-gcp-ads-sandbox)

**[Demo3:]{.underline}** [Used 1M data- Training time 1 hr- 999
features]{.underline}

In the third iteration the number of features was increased to 999 i.e.
the full capacity at which auto ml can train models. The training time
was reduced to 1 hour as in the previous iteration increasing time
showed no significant change. The feature are represented as numeric
type.

[Evaluation Metrics:]{.underline}

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/4634076473215418368/versions/default/evaluate?backTo=training&project=dh-gcp-ads-sandbox>

[Model Details:]{.underline}

[https://console.cloud.google.com/logs/query;query=resource.type%3D\"cloudml_job\"
resource.labels.job_id%3D\"4634076473215418368\"
resource.labels.project_id%3D\"dh-gcp-ads-sandbox\"
labels.log_type%3D\"automl_tables\"
jsonPayload.\"@type\"%3D\"type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure\";timeRange=2022-07-07T07:06:18.760Z%2F2022-07-08T02:48:48.193132Z;cursorTimestamp=2022-07-07T08:06:18.588784Z?project=dh-gcp-ads-sandbox](https://console.cloud.google.com/logs/query;query=resource.type%3D%22cloudml_job%22%20resource.labels.job_id%3D%224634076473215418368%22%20resource.labels.project_id%3D%22dh-gcp-ads-sandbox%22%20labels.log_type%3D%22automl_tables%22%20jsonPayload.%22@type%22%3D%22type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure%22;timeRange=2022-07-07T07:06:18.760Z%2F2022-07-08T02:48:48.193132Z;cursorTimestamp=2022-07-07T08:06:18.588784Z?project=dh-gcp-ads-sandbox)

**[Demo4:]{.underline}** [Used 1M data- Training time 1 hr- 999
features - Represented apps as text]{.underline}

In this iteration we have used 1M data and set training time to 1 hour.
Here the feature apps are represented of text and rest of the features
are set to numeric type. The apps represented as text is done so that we
can use all the 1591 features and perform training on the dataset using
all features. The 1591 columns were reduced to 732 when used this
representation method.

[Evaluation Metrics:]{.underline}

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/31045810321883136/versions/1/evaluate?project=dh-gcp-ads-sandbox>

[Model Details:]{.underline}

[https://console.cloud.google.com/logs/query;query=resource.type%3D\"cloudml_job\"
resource.labels.job_id%3D\"31045810321883136\"
resource.labels.project_id%3D\"dh-gcp-ads-sandbox\"
labels.log_type%3D\"automl_tables\"
jsonPayload.\"@type\"%3D\"type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure\";timeRange=2022-07-12T05:58:45.033Z%2F2022-07-12T17:26:43.927733Z;cursorTimestamp=2022-07-12T06:58:44.861677Z?project=dh-gcp-ads-sandbox](https://console.cloud.google.com/logs/query;query=resource.type%3D%22cloudml_job%22%20resource.labels.job_id%3D%2231045810321883136%22%20resource.labels.project_id%3D%22dh-gcp-ads-sandbox%22%20labels.log_type%3D%22automl_tables%22%20jsonPayload.%22@type%22%3D%22type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure%22;timeRange=2022-07-12T05:58:45.033Z%2F2022-07-12T17:26:43.927733Z;cursorTimestamp=2022-07-12T06:58:44.861677Z?project=dh-gcp-ads-sandbox)

**Demo5:** [Used 4.5M data- Training time 1 hr- 999 features -
Represented apps as text]{.underline}

Here the entire 4.5M dataset was used along with 1591 columns where the
apps were represented as text, which reduced the number of columns to
732. This model did not perform as well as the previous one and showed a
significant reduction in the score.

[Evaluation Metrics:]{.underline}

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/6500466675039600640/versions/1/evaluate?project=dh-gcp-ads-sandbox>

[Model Details:]{.underline}

[https://console.cloud.google.com/logs/query;query=resource.type%3D\"cloudml_job\"
resource.labels.job_id%3D\"6500466675039600640\"
resource.labels.project_id%3D\"dh-gcp-ads-sandbox\"
labels.log_type%3D\"automl_tables\"
jsonPayload.\"@type\"%3D\"type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure\";timeRange=2022-07-12T19:08:09.190Z%2F2022-07-13T13:14:10.688172Z;cursorTimestamp=2022-07-12T20:08:09.019239Z?project=dh-gcp-ads-sandbox](https://console.cloud.google.com/logs/query;query=resource.type%3D%22cloudml_job%22%20resource.labels.job_id%3D%226500466675039600640%22%20resource.labels.project_id%3D%22dh-gcp-ads-sandbox%22%20labels.log_type%3D%22automl_tables%22%20jsonPayload.%22@type%22%3D%22type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure%22;timeRange=2022-07-12T19:08:09.190Z%2F2022-07-13T13:14:10.688172Z;cursorTimestamp=2022-07-12T20:08:09.019239Z?project=dh-gcp-ads-sandbox)

**Demo6:** Used 4.5M dataset- Training time 1 hour- 1591 features-
Represented features as text, categorical and numeric.

This iteration used a dataset with increased number of popular apps.
Reverse encoded state, tier,brand, price range etc as type
categorical.Used the NN Demographics dataset. Kept separate train, test
and validate datasets.

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/2325489082978795520/versions/default/evaluate?backTo=training&project=dh-gcp-ads-sandbox>

[https://console.cloud.google.com/logs/query;query=resource.type%3D\"cloudml_job\"
resource.labels.job_id%3D\"2325489082978795520\"
resource.labels.project_id%3D\"dh-gcp-ads-sandbox\"
labels.log_type%3D\"automl_tables\"
jsonPayload.\"@type\"%3D\"type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure\";timeRange=2022-07-27T13:06:45.115Z%2F2022-07-28T01:28:53.633124Z;cursorTimestamp=2022-07-27T14:06:44.922937Z?project=dh-gcp-ads-sandbox](https://console.cloud.google.com/logs/query;query=resource.type%3D%22cloudml_job%22%20resource.labels.job_id%3D%222325489082978795520%22%20resource.labels.project_id%3D%22dh-gcp-ads-sandbox%22%20labels.log_type%3D%22automl_tables%22%20jsonPayload.%22@type%22%3D%22type.googleapis.com%2Fgoogle.cloud.automl.master.TablesModelStructure%22;timeRange=2022-07-27T13:06:45.115Z%2F2022-07-28T01:28:53.633124Z;cursorTimestamp=2022-07-27T14:06:44.922937Z?project=dh-gcp-ads-sandbox)

**Demo7:** Used the entire 4.5M data with representing apps as text only
and using a predefined test,train and validate set.

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/2790485744504799232/versions/1/evaluate?project=dh-gcp-ads-sandbox>

**Demo8:** Improved Demo6 results by removing features with scaled
importance less than 0.05 to reduce noise.

<https://console.cloud.google.com/vertex-ai/locations/us-central1/models/8624441664926121984/versions/1/evaluate?project=dh-gcp-ads-sandbox>

  ------------- ------------ ------------ ------------ ------------ ------------ ------------ ------------ ------------
  **Results**   **Demo 1**   **Demo 2**   **Demo 3**   **Demo 4**   **Demo 5**   **Demo 6**   **Demo 7**   **Demo 8**
  f1score       0.6030       0.5991       0.6032       0.6334       0.5725       0.6483       0.6262       0.6626
  PR AUC        0.645        0.639        0.641        0.678        0.605        0.688        0.666        0.707
  ROC AUC       0.863        0.861        0.858        0.872        0.833        0.876        0.869        0.887
  LogLoss       0.316        0.322        0.325        0.312        0.453        0.304        0.300        0.278
  Precission    57.8%        55.7%        58.3%        63.2%        57.4%        66.7%        61.6%        66.4%
  Recall        63%          64.8%        62.6%        63.5%        57.2%        63.1%        63.7%        66.1%
  ------------- ------------ ------------ ------------ ------------ ------------ ------------ ------------ ------------

**[Stages of Training:]{.underline}**

Data Preprocessing: Preprocesses the data before moving on to training
phase

Training: This phase is where the actual training is performed. The
training time is declared in the code and that time is more or less
honoured, it takes 20-30 mins extra if at all.

Evaluation: This is phase where the evaluation metrics are calculated.
This phase takes 20-30 mins to complete.

Model Post Processing: This stage prepares the model post processing,
i.e getting details about the hyperparameters and getting the model
ready for deployment

**[About the Models Used:]{.underline}**

The model hyperparameter had two categories- Model and Trial.

[Model-]{.underline} From what I observed the model part of
hyperparameter gives details about the final model hyperparameters.

[Trial-]{.underline} The trial part of the hyperparameter provides
information about hyperparameter tunning and how many trials it did to
tune the parameters.

**[To-Do:]{.underline}**

- Change the optimisation function to minimize-logloss.

- Set training time to 2 hours.

- Keep a common test set.

**Age Prediction Model AutoML- Vertex AI:**

Notebook link:
<https://29080abceab67051-dot-asia-south1.notebooks.googleusercontent.com/lab/tree/Age0.ipynb>
