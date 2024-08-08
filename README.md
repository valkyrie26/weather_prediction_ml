## bharatbench_ml

## Overview
 
This is an ML study on the BharatBench dataset's performance for CNN and convLSTM, and trying to analyse and possibly improve on, the results of the research paper by Choudhury, A., Panda, J., &amp; Mukherjee, A. (2024). BharatBench: Dataset for data-driven weather forecasting over India. arXiv [Physics.Ao-Ph]. (http://arxiv.org/abs/2405.07534). 

## Dataset
The BharatBench dataset is a collection of meteorological data specifically prepared for AI/ML applications in weather forecasting over India. It includes atmospheric variables, surface variables, and constants derived from the IMDAA reanalysis datasets. The dataset is available for download on Kaggle in NETCDF format. It can be downloaded from https://www.kaggle.com/datasets/maslab/bharatbench

Different types of atmospheric data variables are mentioned such as H500, T850, T2m, TP6h which can be chosen for a comparative study. In this study, we found T850 to have the best results (same as the original paper), and so the code reflects that, but it can be modified.

To import the dataset, you can either mount your google drive and have a folder containing the dataset in it (only the merged IMDAA_merged_1.08_1990_2020.nc file was imported here), or you can try to provide a downloadable drive link for the same. 

## Original Code Source
This project builds upon the code originally developed by the authors of the paper. The original code can be found in their GitHub repository:
https://github.com/MASLABnitrkl/BharatBench

## Program Execution

This project was run using Jupyter Notebooks on Google Colab. This repository contains iPython notebook files that are compatible and just need to be uploaded on the platform to run. Runtime requirements were set to a T4 GPU so that training does not take significant amount of time.

Libraries used are already included in the initial command block for installation and import. However, if you already have those installed and are running this code in an alternate application, feel free to delete those commands. Also, if the program needs to be executed as a .py file, remove the '!' in front of the pip statements in the first block as it is a syntax used on Colab and may not work in other enviroments, eg. terminal bash shell.
The Dataset Preparation sections of the noteboobs might need modification depending on where you choose to source the dataset from.
3_CNN_BatchNormalization.ipynb requires mounting and then sourcing the data from a google drive location using the relative file path. Upload the dataset to a desired location on your google drive and update the file path in the code accordingly. To mount the drive successfully to Colab, various permissions need to be provided when the popup appears.
3_CNN_Modified sources the data from a google drive location using a link and file id. Although the file id and the link provided already in the code might work, this article (https://safjan.com/download-data-google-drive-colab-gdown/) can be used as a starter on how to get the required sharable link and id to be used in the code if you choose to use the dataset from another drive location.

To run the code, go to the 'Runtime' tab and click 'Run all'. Alternatively, each code block can be clicked to run separately by clicking the play button on the top-left side of each cell, making sure that the execution is sequential to avoid errors.

<u>Note:</u> Leaving the screen idle for a long time will cause Colab to pause and give a pop-up message. If using the free-tier of Google Colab, it is advisable to use the resources wisely.

## Evaluation Metrics

The evaluation metrics used for analysis have been same as the original paper, RMSE (root mean squared error), MAE (mean absolute error), ACC (anomaly correction coefficient). Apart from these, the number of parameters trained, layer architecture and training loss curves can be observed for further analysis.

## Observations

We tried fine-tuning the original CNN and convLSTM models provided by varying its hyperparameters and making changes to the model itself. The optimal scenario found by our experimentation was:

CNN:
<br/>learning rate: 1e-04
<br/>activation type: 'selu'
<br/>number of batches: 32
<br/>drop rate for middle layer: 0.3

convLSTM:
<br/>learning rate: 1e-04
<br/>activation type: 'selu'
<br/>number of batches: 32
<br/>drop rate for middle layer: 0.3

## Acknowledgements
We would like to thank the authors of the original research paper for providing the foundational code and research that made this project possible.
