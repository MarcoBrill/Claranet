# Claranet

# Marco Brillanti #

# SQL Analytics problem 

This script provides the solutions to the following sections:
- Data Analytics (Pre-processing and Visualisation) + Model Training + Model Deploy

The script is written using Python 3 with Tensorflow 2 and it is saved as ipynb file.
In order to write the script I have used Google Colab but you can also be used Jupyter to run it.

## Data

I have uploaded the provided data (json and sql) into my Google Drive account because it was
easier for me to load them using Google Colab.

In order to access the data and allow Google Colab to use the drive you need to grant it permission using the password provided by the system when you run the following script:

from google.colab import drive
drive.mount('/content/drive')

Otherwise using Jupyter you can skip these lines and retrieve the data using the right paths.


## Data Analytics

I have divided this section into two parts.
Basically, I have eleborated both the json files but at the end I proceed with the analysis of just one of those.

After reading the json files (general_log.json, slow_log.json), as a first step, I have focused the attention on general_log (df_general) and elaborated it using Pandas.
However, df_general was not the right dataframe to analyse because I need the
execution time (query_time) which is provided in the second dataframe (df_slow).

In fact, all the following analysis will be focused on df_slow dataframe.
Here, I apply once again the previous pre-processing operation applied on df_general
in order to deal with datatime columns and categorical columns.
I apply the One Hot Encoding methodology to convert categorical data into numerical.
I have also rid of the unnecessary columns (constant columns)  

Once the df_slow was pre-processed I scaled (normalised) it.

In this section, I also provide some visualisation of the data.

## Model Training (Multicollinearity Analysis)

In this section, I provide the training and the accuracy evaluation of 3 models.

The first step was the data preparation (train, test and evaluation).

Model 1 and Model 2 are based on artificial neural networks (deep learning).
Model 1 is a simple model with just 3 fully connected layers.
Model 2 has a more complex architecture where I have also introduced dropout layers as well.

Graphical reports of the training processes are reported.

The evaluation of the models' prediction power has been assessed using R2 score.
The result obtained suggested that these two models were not good to predict the execution time.

Model 3 use a classical Machine Learning approach deploying a Linear Regression algorithm.
R2 score shows a much better result.
I also try to predict the next 10 datapoints using this model.

## Answering the questions asked:
1.	Is machine learning appropriate for this problem, and why or why not?
After the pre-processing and scaling of the data, it was possible to apply an ML solution.
However, fancy models, like artificial neural networks, were not right solutions.

2.	What is the ML problem if there is one, and what would a success metric look like?
Model 1 and Model 2 can be considered Deep Learning methodologies. These were too highly nonlinear and too complex for the prediction of executing time. Therefore, they were not optimal solutions. On the other hand, Model 3, which deployed Linear Regression provided a much better result (more details regarding the evaluation of the R2 score are provided in the script)

3.	What kind of ML problem is this?
Multicollinearity Analysis (multivariate analysis) for regression (prediction) purposes.

4.	Is the data appropriate?
After pre-processing the dataset was ready for analysis, however, the pre-processing increased the dimensionality of the dataset.

## Model Deploy

Here I have modified the main.py script to run it using TensorFlow 2 and to use the regression model previously obtained to predict the queries (or loading the provided model.h5).

This section would need more work/expansion. The application of DevOps principles to ML is a
fairly new field for me. 



