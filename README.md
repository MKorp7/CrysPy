# CrysPy
A tool to predict the crystallization propensity of proteins from their sequence.

# Abstract
Protein crystallization is a challenging task that takes a lot of time and money for research labs. However, it is crucial for studying the 3D structure of proteins and how they interact. Despite ongoing improvements in experimental techniques, only 30\% of crystallization trials are successful. Success depends on many factors, including the protein itself. Recently, machine-learning-based tools like XtalPred or XANNpred have been developed to help choose sequences with the best chance of crystallizing. This study looks at how selecting different features affects the success of the models and compares various model architectures and parameters, using XtalPred's results as a reference to compare efficiency. The influence of the selection of features on accuracy was demonstrated and comparable effectiveness was achieved.

# Requirements:
* For surface-related features calculation: NetSurfP-3.0 (https://services.healthtech.dtu.dk/services/NetSurfP-3.0/) The program requires acceptance of a license for academic and non-commercial use. NetSurfP requires a specific version of the conda environment provided by the authors of the software which is in conflict with the TensorFlow package. I encourage you to run it separately. You can also use *biolib* or NetSurfP web server.

  *The software is very demanding, it is possible to use your own CPU without GPU, but you have to be prepared for time-consuming calculations and possible overheating if you use a laptop without proper cooling. If you don't want to run the predictions yourself, the information for the dataset has been collected in a combined.csv file, by combining the NetSurfP results obtained for all proteins. Howere this is not needed if you do not want to create new features related to surface).*
* iupred2a can be download from here: https://iupred2a.elte.hu/download_new. It is also only for academic users.
* The rest of the requirements can be install with following command:
 ```{bash}
 pip install -r requirements.txt
  ```
# Raport
The raport and biblioraphy can be found in _Machine_Learning_to_Predict_Protein_Crystallizability.pdf_ This file will also bring you closer the idea behind this project.

# Data
The training dataset was downloaded from https://XtalPred.godziklab.org/XtalPred/data.tar. Credits belong to Adam Godzik Lab, which created the dataset. 

The results from NetSurfP for the sequences from the dataset are stored here as a compressed combined.csv file: https://drive.google.com/file/d/1sUaNOBqr99QW5StNqIYWrg5WPDAMpYBq/view?usp=sharing

The uncompressed file is 1.6 GB. You do NOT need it to run this scripts!

The calculated features for training set and test set are saved in _datasets_.

# Notebooks and usage
Notebooks are designed to run on a specific set of data and in the appropriate order, so they are numbered and use file paths. The results are presented in notebooks for the convenience of reviewers as they show partial results step by step and allow convenient editing of individual parts of the code if the user would like to expand it.
At the beginning of each notebook, the resulting files and the files necessary to run are described. Please change the paths if you would like to use own sequences and fasta files.

- 1_standard_features_calculations.ipynb - creating dataset with standard features, uses iupred2a.
- 2 - in this step you need to run NetSurfP!
- 3_data_integration-dataset_additional_features.ipynb - creating dataset with all features, uses ouput from first notebook and NetSurf3P results.
- 4_models_train_and_test.ipynb - the final notebook, performs predictions, saves csvwith features and results, create plots with "best" proteins features against feature distribution.

## Additional remarks

The result is prediction not the promise! A prediction of failure or success cannot be considered binding and certain.

It is also recommended to manually check which data deviate from the peak in the distribution graphs and decide for yourself what type of protein "unusualness" is more acceptable to us and we know how to deal with it in the wet lab.

The script to do not handle proteins with unusual amino acids! There will be written down to separte fasta file.

Below a real-life example:
<img width="1989" height="3880" alt="Bez nazwy" src="https://github.com/user-attachments/assets/7eebaa29-fc60-46a4-b447-43ccac56c83f" />

## About author
Marta Korpacz

[1] The Centre of New Technologies (University of Warsaw), INTERDISCIPLINARY LABORATORY of BIOLOGICAL SYSTEMS MODELLING (Sulkowska Group)

[2] Faculty of Mathematics, Informatics, and Mechanics, University of Warsaw





